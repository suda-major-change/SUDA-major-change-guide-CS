# 8 附录

## 附录A Python入门书籍推荐

下面几本书在网上都可以找到电子版。如果无法确定需要阅读哪本书，可以先找到它们的电子版大致看一下前几页，确定自己适合哪本。

**如果你没有其他编程语言基础：**

以下几本书无论有没有其他编程语言基础都可以阅读。但是有其他编程语言基础者可能会感到有些啰嗦。

- **Python编程从入门到实践（第2版）**：中文版正文422页，英文原版出版于2019年，黑白印刷。由人民邮电出版社出版。如果目的只是为了通过考试，仅需阅读第一部分，也就是前200页。第二部分想看就看，与考试关系不大。如果是零基础并且希望通过阅读入门Python，我最推荐这本。翻译不错。
- **Head First Python（第2版）**：中文版正文620页，英文原版出版于2016年，黑白印刷。非常基础的Python入门书，大量附图并附有大量例子，语言非常活泼，几乎不存在任何理解难度。与上一本相同，如果目的只是为了通过考试，仅需选择性阅读一部分。我个人不将它放在第一顺位优先级也是因为这本书太注重易于理解与趣味性，这导致其信息密度太低，读起来太过啰嗦。个人仅建议连上一本书都读不下去的读者考虑选择。

**如果你有其他编程语言基础：**

以下几本书不推荐没有其他编程语言基础者阅读。

- **Python编程快速上手（第2版）**：中文版正文409页，英文原版出版于2019年，黑白印刷。主要注重实用性，不像上面两本书那样基础，建议有其他编程语言基础的读者阅读。同样，如果目的只是为了通过考试，仅需阅读前半本约200页，并且这200页中涉及实际项目的考试也不会涉及（因此建议结合董付国那本确定哪些内容可以跳读）。翻译不错。
- **Python学习手册（第5版）**：中文版正文1514页，英文原版出版于2013年，黑白印刷，分上下册。我不推荐阅读本书，包括有其他编程语言基础者，因为其内容事无巨细而且过于啰嗦，唯一的优点就是全面。即使希望进阶也不建议阅读本书。

事实上，如果你有其他编程语言基础，并且能够忍受教材中枯燥的语言，直接阅读董付国的《Python程序设计》也是可以的。甚至如果你的时间比较紧张，直接阅读“菜鸟教程”网站上的Python 3教程即可，几个小时就足够掌握大概语法。

## 附录B Python编辑器推荐

**对于初学者来说，编写Python代码使用的编辑器最推荐Jetbrains公司开发的PyCharm。**PyCharm提供免费的社区版本，在官网上直接下载即可。社区版本的功能一般来说对于任何本科生应该都是足够的。当然，**使用Python自带的IDLE进行学习自然也是可以的**，至少对于转专业考试的难度来说IDLE的功能同样是足够的。

如果在配置PyCharm的过程中出现了些许困难，建议直接换用**Python自带的IDLE**进行学习。以防止在不尽的折腾中快速丧失兴趣。

> ### 题外话：Jetbrains学生认证与学生邮箱
>
> 如果你希望获取PyCharm的专业版，或是也很喜欢Jetbrains公司开发的其他没有提供免费社区版的IDE，那么可以在Jetbrains的官方网站上提交学生认证。学生认证的期限是一年，在此期间你可以通过学生账号免费使用Jetbrains家的所有产品。在到期之后会提醒你更新认证，成功后可以继续你的免费使用凭证。
>
> 此外，苏州大学提供的学生邮箱是非常有用的。学生邮箱不仅可以用来较为正式地与学校部门及老师通过邮件沟通，还可以用来（配合学生证或学信网认证）申请数不清的学生优惠，甚至软件和网站的免费使用。例如Onedrive使用苏大学生邮箱登录就会赠送1TB的空间与网页版Office365的使用凭证。除此之外，学生邮箱还有其他许许多多用处，比如和学生证一起申请Jetbrains的学生认证。

如果你有其他编程语言的基础，自己也喜欢折腾，可以试试**Visual Studio Code**（注意和Visual Studio区分）。VSCode配置Python也非常方便，简单易上手，关键是生态非常好，可配置性强，几乎支持所有主流编程语言，这样就避免了在编辑器之间来回切换，还方便各种折腾，而且由于是轻量级编辑器，内存占用比较小，打开速度快（前提是扩展装得不多），此外也开源免费（这还是挺关键的）。VSCode的缺陷也很明显，由于是轻量级编辑器，不是IDE，因此智能提示效果比较差，比不上Jetbrains家的IDE，比如Pycharm和IDEA。对于新手，我更建议直接上手Pycharm这类专业IDE。

## 附录C Type Hints（类型提示）

> *It should also be emphasized that* ***Python will remain a dynamically typed language, and the authors have no desire to ever make type hints mandatory, even by convention**.*
> Guido van Rossum, Jukka Lehtosalo, and Łukasz Langa, PEP 484—Type Hints

可能有读者对LeetCode上类似“nums: List[int]、target: int、-> List[int]”这样的语句感到困惑。这确实是一般Python教程中不会涉及的，更何况这一用法直到Python 3.6才基本可用，旧一些的参考资料根本不可能会涉及。

首先我在这里声明由于转专业考试使用的是Python 3.5，这部分知识你完全**不需要**了解，我在这里提及这部分内容主要是为了满足部分读者的好奇心。**如果你不想了解这些内容，完全可以不了解**。

这一用法被称为type hints，即类型提示。使用方法主要是在变量后添加冒号并指定其类型，例如“a: int”。除此之外，type hints也可以用于指定函数的返回值类型，这需要在函数定义的第一行（即def行）最后添加箭头符号，并指定返回值类型，例如“... -> dict”。

```python3
def twoSum(nums: list, target: int) -> list:
    dct = {} # 这里不必显式标注dct: dict = {}，
             # 因为编辑器可以通过类型推断自动推导出dct的类型为dict
    for i, num in enumerate(nums):
        if dct.get(target - num) is not None:
            return [i, dct.get(target - num)]
        dct[num] = i
```

除此之外，type hints还有很多规则，你可以使用类似“list[int]”这样的形式表示一个仅包含整数的列表，也可以使用“dict[str, int]”表示一个键为字符串，值为整数的字典。

```python3
def twoSum(nums: list[int], target: int) -> list[int]:
    dct: dict[int, int] = {} # 也可以这样具体地标注dct的类型
    for i, num in enumerate(nums):
        if dct.get(target - num) is not None:
            return [i, dct.get(target - num)]
        dct[num] = i
```

在较早的Python版本中，无法直接使用“list[int]”这样的语法，而需要使用“List[int]”这样的语法。

```python3
from typing import List, Dict

def twoSum(nums: List[int], target: int) -> List[int]:
    dct: Dict[int, int] = {} # 也可以这样具体地标注dct的类型
    for i, num in enumerate(nums):
        if dct.get(target - num) is not None:
            return [i, dct.get(target - num)]
        dct[num] = i
```

除此之外，如果想要标注函数，可以使用“Callable[[...], returnval]”表示一个参数为...(方括号中可包含多个用逗号分隔的参数)，返回值为returnval的**可调用对象**（要使用Callable需要从typing模块中导入Callable）。也可以使用“Iterable”表示可迭代对象，使用Optional[int]表示可选参数（在这里是int或None）。

```python3
from typing import Callable, Iterable, Optional

def reduceIntList(func: Callable[[int, int], int], nums: Iterable[int], start_value: Optional[int] = None) -> int:
    if start_value is None:
        start_value = 0
    total = start_value # 编辑器可以通过类型推导得知total的类型为total，同样不必显式标注类型
    for num in nums:
        total = func(total, num)
    return total

reduceIntList(lambda total, num: total + num, [1, 2, 3, 4, 5]) # => 15
```

此外，在Python 3.10中，支持以“|”表示“或”。例如“int | float | str”表示整数、浮点数或字符串。在之前的版本，可以使用typing库中的“Union”表示“或”，例如“Union[list[int], list[str]]”。

```python3
from typing import Callable, Iterable, Optional

def reduceNumList(func: Callable[[int | float, int | float], int | float], 
                  nums: Iterable[int | float], start_value: Optional[int | float] = None) -> int | float:
    if start_value is None:
        start_value = 0
    total = start_value
    for num in nums:
        total = func(total, num)
    return total

# 于是我们的函数也支持了浮点型
reduceNumList(lambda total, num: total + num, [1.1, 1.2, 1.3]) # => 3.5999999999999996
```

同时，类型也是可以被命名的。这可以使代码更加简洁

```python3
from typing import Callable, Iterable, Optional
Number = int | float
ReduceFunc = Callable[[Number, Number], Number]

def reduceNumList(func: ReduceFunc, nums: Iterable[Number], start_value: Optional[Number] = None) -> Number:
    if start_value is None:
        start_value = 0
    total = start_value
    for num in nums:
        total = func(total, num)
    return total

reduceNumList(lambda total, num: total + num, [1.1, 1.2, 1.3]) # => 3.5999999999999996
```

也可以用“Any”表示任意类型。不过不建议这么做，因为把类型标成Any等于什么都没标，意义不大。下面是用“Any”实现的reduce函数，但实际上应该使用泛型，不过这里不再过多赘述泛型的语法，感兴趣可以自己查。

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

有时候我们也可能只想限定某个参数只能是特定值之一。接触过其他语言者可能会考虑使用枚举类型，在Python 3.4中同样对枚举类型（Enum）添加了支持，但使用type hints可以更优雅地解决这一问题：

```python3
from typing import Literal
# Literal即字面量，不了解这个概念的可以很轻松地从网上找到这一名词的解释

# 这里表示新建一个类型Fruit，且只能是Literal[]中的三个类型之一
Fruit = Literal["apple", "pear", "banana"]
def sell(fruit: Fruit):
    ...
```

此外，Python的type hints还对泛型、鸭子类型（结构化类型）、自引用等高级特性提供了支持，在这里不再过多赘述。

如果想了解更多关于type hints的知识，我推荐阅读*[Fluent Python 2nd](https://learning.oreilly.com/library/view/fluent-python-2nd/9781492056348/)*的[Chapter 8](https://learning.oreilly.com/library/view/fluent-python-2nd/9781492056348/ch08.html)和[Chapter 15](https://learning.oreilly.com/library/view/fluent-python-2nd/9781492056348/ch15.html%23more_types_ch)（如果你英文水平过得去的话）或是[Python关于typing库的官方中文文档](https://docs.python.org/zh-cn/3/library/typing.html)。如果你很遗憾的，英文水平不过关，也不想看文档，那或许就只能找国内的各种网站（比如博客和某乎）上的二手资料了。*近日我对type hints相关语法进行了简单的总结，可以移步我的文章[Python Type Hints 简明教程 (基于Python 3.10)](https://zhuanlan.zhihu.com/p/464979921)。*

显然，type hints不是强制的，你可以只为部分变量加上类型标注，方便自己阅读阅读或是方便编辑器的类型推断。值得注意的是，type hints是“类型标注”而不是“类型检查”，Python的运行时（Runtime）实际上不会进行类型检查，也就是说，即使实际运行的时候变量类型与标注类型并不一致也不会报错，你甚至可以写类似“a: int = 'abc'”这样的语句，Python同样不会报错。这听起来可能很奇怪，但实际上是合理的——Python的运行速度本来就很慢了，再加上运行时类型检查只会使其雪上加霜。

尽管对于一些程序员来说，type hints可能并不是特别常用，但使用type hints确实是一个很好的习惯，在一些大型公司中为了编写易于维护Python项目而大量使用Type Hint也是很常见的。不过，既然转专业考试使用的Python环境是Python 3.5，那么自然是用不了Type Hint的——毕竟在Python 3.6时type hints才得到了比较完善的支持。我也不建议在考试时使用type hints，因为写点小程序没必要用type hints，写大型项目用这个才有意义。

值得指出的是，Python其实有着大量你认为没有实现但实际上已经实现的功能，这些大多数都可以在*[Fluent Python 2nd](https://learning.oreilly.com/library/view/fluent-python-2nd/9781492056348/)*中找到。例如Python可以使用`@property`装饰器和`@[methodName].setter`装饰器实现类似JavaScript中的`get`和`set`方法，也可以使用`@classmethod`装饰器实现类方法，甚至"@dataclass"装饰器帮助你更方便地定义数据类型。Python甚至通过asyncio库实现了高效的异步编程，支持通过`await`/`async`关键词定义异步函数，这可以在很多情况下替代多线程。如果你在写Python代码的时候很怀念某个语言的某个特性，不要犹豫立刻搜一下，说不定Python已经有装饰器或其他语法可以实现类似的用法了。