# 附录 C Type Hints（类型提示）

> _It should also be emphasized that_ **\*Python will remain a dynamically typed language, and the authors have no desire to ever make type hints mandatory, even by convention**.\*
> Guido van Rossum, Jukka Lehtosalo, and Łukasz Langa, PEP 484—Type Hints

可能有读者对 LeetCode 上类似“nums: List[int]、target: int、-> List[int]”这样的语句感到困惑。这确实是一般 Python 教程中不会涉及的，更何况这一用法直到 Python 3.5 才开始可用，旧一些的参考资料根本不可能会涉及。

首先我在这里声明由于转专业考试对 Python 进阶语法考察很少，这部分知识你完全**不需要**了解，我在这里提及这部分内容主要是为了满足部分读者的好奇心。**如果你不想了解这些内容，完全可以不了解**。

这一用法被称为 type hints，即类型提示。使用方法主要是在变量后添加冒号并指定其类型，例如“a: int”。除此之外，type hints 也可以用于指定函数的返回值类型，这需要在函数定义的第一行（即 def 行）最后添加箭头符号，并指定返回值类型，例如“... -> dict”。

```python3
def two_sum(nums: list, target: int) -> list:
    dct = {} # 这里不必显式标注dct: dict = {}，
             # 因为编辑器可以通过类型推断自动推导出dct的类型为dict
    for i, num in enumerate(nums):
        if dct.get(target - num) is not None:
            return [i, dct.get(target - num)]
        dct[num] = i
```

除此之外，type hints 还有很多规则，你可以使用类似“list[int]”这样的形式表示一个仅包含整数的列表，也可以使用“dict[str, int]”表示一个键为字符串，值为整数的字典。

```python3
def two_sum(nums: list[int], target: int) -> list[int]:
    dct: dict[int, int] = {} # 也可以这样具体地标注dct的类型
    for i, num in enumerate(nums):
        if dct.get(target - num) is not None:
            return [i, dct.get(target - num)]
        dct[num] = i
```

在较早的 Python 版本中（3.8 及以前），无法直接使用“list[int]”这样的语法，而需要使用“List[int]”这样的语法。

```python3
from typing import List, Dict

def two_sum(nums: List[int], target: int) -> List[int]:
    dct: Dict[int, int] = {} # 也可以这样具体地标注dct的类型
    for i, num in enumerate(nums):
        if dct.get(target - num) is not None:
            return [i, dct.get(target - num)]
        dct[num] = i
```

除此之外，如果想要标注函数，可以使用“Callable[[...], returnVal]”表示一个参数为...(方括号中可包含多个用逗号分隔的参数)，返回值为 returnVal 的**可调用对象**（要使用 Callable 需要从 typing 库中导入 Callable）。也可以使用“Iterable”表示可迭代对象，使用 Optional[int]表示可选参数（在这里是 int 或 None）。

```python3
from typing import Callable, Iterable, Optional

def reduce_int_list(func: Callable[[int, int], int],
                    nums: Iterable[int],
                    start_value: Optional[int] = None) -> int:
    if start_value is None:
        start_value = 0
    total = start_value # 编辑器可以通过类型推导得知total的类型为total，同样不必显式标注类型
    for num in nums:
        total = func(total, num)
    return total

reduceIntList(lambda total, num: total + num, [1, 2, 3, 4, 5]) # => 15
```

此外，在 Python 3.10 中，支持以“|”表示“或”。例如“int | str”表示整数或字符串。在之前的版本，可以使用 typing 库中的“Union”表示“或”，例如“Union[list[int], list[str]]”。

```python3
def parse_token(token: str) ->  str | float:
    try:
        return float(token)
    except ValueError:
        return token
```

同时，类型也是可以被命名的。这可以使代码更加简洁

```python3
Hexadecimal = str | int

def hex_to_ascii_string(hex: Haxdecimal) -> str:
    ...

# 上面的代码与以下代码是等价的
def hex_to_ascii_string(hex: str | int) -> str:
    ...
```

也可以用“Any”表示任意类型。不过不建议这么做，因为把类型标成 Any 等于什么都没标，意义不大。下面是用“Any”实现的 reduce 函数，但实际上应该使用泛型，不过这里不再过多赘述泛型的语法，感兴趣可以自己查。

```python3
from typing import Callable, Iterable, Optional, Any
ReduceFunc = Callable[[Any, Any], Any]

def reduce(func: ReduceFunc, args: Iterable[Any], start_value: Optional[Any] = None) -> Any:
    if start_value is None:
        # 若不提供起始值，将第一个参数作为起始值
        total = args[0]
        for arg in args[1:]:
            total = func(total, arg)
    else:
        total = start_value
        for arg in args[1:]:
            total = func(total, arg)
    return total

reduce(lambda total, x: str(total) + ", " + str(x), [1, 2, 3, 4, 5]) # => '1, 2, 3, 4, 5'


# 泛型版本的reduce，不提供解释，感兴趣自己查
from typing import TypeVar
T = TypeVar("T")

def reduce(func: Callable[[T, T], T], args: Iterable[T], start_value: Optional[T] = None) -> T:
    if start_value is None:
        total = args[0]
        for arg in args[1:]:
            total = func(total, arg)
    else:
        total = start_value
        for arg in args[1:]:
            total = func(total, arg)
    return total
```

有时候我们也可能只想限定某个参数只能是特定值之一。接触过其他语言者可能会考虑使用枚举类型，在 Python 3.4 中同样对枚举类型（Enum）添加了支持，但使用 type hints 可以更优雅地解决这一问题：

```python3
from typing import Literal
# Literal即字面量，不了解这个概念的可以很轻松地从网上找到这一名词的解释

# 这里表示新建一个类型Fruit，且只能是Literal[]中的三个类型之一
Fruit = Literal['apple', 'pear', 'banana']
def sell(fruit: Fruit):
    ...
```

此外，Python 的 type hints 还对泛型、鸭子类型（结构化类型）、自引用等高级特性提供了支持，在这里不再过多赘述。

如果想了解更多关于 type hints 的知识，我推荐阅读*[Fluent Python 2nd](https://learning.oreilly.com/library/view/fluent-python-2nd/9781492056348/)*的[Chapter 8](https://learning.oreilly.com/library/view/fluent-python-2nd/9781492056348/ch08.html)和[Chapter 15](https://learning.oreilly.com/library/view/fluent-python-2nd/9781492056348/ch15.html%23more_types_ch)（如果你英文水平过得去的话）或是[Python 关于 typing 库的官方中文文档](https://docs.python.org/zh-cn/3/library/typing.html)。如果你很遗憾的，英文水平不过关，也不想看文档，那或许就只能找国内的各种网站（比如博客和某乎）上的二手资料了。_近日我对 type hints 相关语法进行了简单的总结，可以移步我的文章[Python Type Hints 简明教程 (基于 Python 3.11)](https://zhuanlan.zhihu.com/p/464979921)。_

显然，type hints 不是强制的，你可以只为部分变量加上类型标注，方便自己阅读阅读或是方便编辑器的类型推断。值得注意的是，type hints 是“类型标注”而不是“类型检查”，Python 的运行时（Runtime）实际上不会进行类型检查，也就是说，即使实际运行的时候变量类型与标注类型并不一致也不会报错，你甚至可以写类似“a: int = 'abc'”这样的语句，Python 运行时同样不会报错。这听起来可能很奇怪，但实际上是合理的——Python 的运行速度本来就很慢了，再加上运行时类型检查只会使其雪上加霜。

尽管对于一些程序员来说，type hints 可能并不是特别常用，但使用 type hints 确实是一个很好的习惯，在一些大型公司中为了编写易于维护 Python 项目而大量使用 type hints 也是很常见的。如果你非要在转专业考试中使用 type hints，自然也没人拦着你，但你需要了解到转专业使用的 Python 版本是 3.8，有一些最新的特性无法使用。我也不建议在考试时使用 type hints，因为写点小程序没必要用 type hints，写大型项目用这个才有意义。

值得指出的是，Python 其实有着大量你认为没有实现但实际上已经实现的功能，这些大多数都可以在*[Fluent Python 2nd](https://learning.oreilly.com/library/view/fluent-python-2nd/9781492056348/)*中找到。例如 Python 可以使用`@property`装饰器和`@[methodName].setter`装饰器实现类似 JavaScript 中的`get`和`set`方法，也可以使用`@classmethod`装饰器实现类方法，甚至"@dataclass"装饰器帮助你更方便地定义数据类型。Python 甚至通过 asyncio 库实现了高效的异步编程，支持通过`await`/`async`关键词定义异步函数，这可以在很多情况下替代多线程。如果你在写 Python 代码的时候很怀念某个语言的某个特性，不要犹豫立刻搜一下，说不定 Python 已经有装饰器或其他语法可以实现类似的用法了。
