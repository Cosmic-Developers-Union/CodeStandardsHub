# Python 代码风格指南

**本文档仍然在编写中**

## 目录

1. **命名约定**
   - 变量和函数命名
   - 类命名
   - 常量命名
   - 模块命名

2. **代码布局**
   - 缩进
   - 空格使用
   - 行长度限制

3. **导入规范**
   - 绝对导入 vs 相对导入
   - 导入分组顺序
   - 避免使用通配符导入

4. **注释**
   - 单行注释
   - 多行注释
   - 文档字符串（docstrings）

5. **代码结构**
   - 函数与类的定义
   - 条件表达式
   - 循环与迭代器

6. **异常处理**
   - 异常捕获与处理
   - 自定义异常类

7. **最佳实践**
   - 避免全局变量
   - 使用生成器表达式
   - 合理使用装饰器

8. **测试与质量**
   - 单元测试
   - 代码静态分析工具
   - 代码质量保证措施

## 1. 命名约定

### 变量和函数命名

使用小写字母和下划线分隔（snake_case）。

```python
# 示例
my_variable = 10
def calculate_sum(a, b):
    return a + b
```

### 类命名

使用驼峰命名法（CamelCase）。

```python
# 示例
class MyClass:
    pass
```

### 常量命名

全大写字母和下划线分隔。

```python
# 示例
MAX_RETRY_COUNT = 5
```

### 模块命名

简短、小写，可包含下划线。

```python
# 示例
import my_module
```

## 2. 代码布局

### 缩进

使用4个空格进行缩进，不要使用制表符。

### 空格使用

在运算符和逗号后面加一个空格，除了逗号后的换行。不要在括号内侧使用额外的空格。

### 行长度限制

每行代码不超过79个字符，长的文本字符串或注释不超过72个字符。

## 3. 导入规范

### 绝对导入 vs 相对导入

优先使用绝对导入，特别是在较大的项目中。

```python
# 示例
import my_module
from package.submodule import function
```

### 导入分组顺序

标准库导入、第三方库导入、本地应用/库导入，每组之间用空行分隔。

### 避免使用通配符导入

```python
# 不推荐
from module import *
```

## 4. 注释

### 单行注释

在代码上方使用单行注释，句末要使用句号。

```python
# 示例
result = calculate_sum(3, 5)  # 计算和
```

### 多行注释

使用多行注释描述函数、类等大块内容的功能和使用方法。

```python
"""
这是一个示例函数，用于计算两个数的和。

参数：
a (int): 第一个加数
b (int): 第二个加数

返回：
int: 两个数的和
"""
def calculate_sum(a, b):
    return a + b
```

### 文档字符串（docstrings）

对于所有公共模块、函数、类和方法使用文档字符串，遵循PEP 257规范。

```python
def calculate_sum(a, b):
    """
    计算两个数的和。

    参数：
    a (int): 第一个加数
    b (int): 第二个加数

    返回：
    int: 两个数的和
    """
    return a + b
```
Certainly! Let's continue with the Python style guide template:

---

## 5. 代码结构

### 函数与类的定义

使用空行分隔函数定义和类定义，类方法之间也使用空行分隔。

```python
# 示例
def function1():
    pass

def function2():
    pass

class MyClass:
    def method1(self):
        pass
    
    def method2(self):
        pass
```

### 条件表达式

优先使用清晰的条件表达式，避免复杂的嵌套。

```python
# 示例
if condition1 and condition2:
    do_something()
elif condition3:
    do_something_else()
else:
    fallback_action()
```

### 循环与迭代器

使用`for`循环而不是`while`循环，优先使用迭代器和生成器。

```python
# 示例
for item in my_list:
    process_item(item)
    
for key, value in my_dict.items():
    process_key_value(key, value)
```

## 6. 异常处理

### 异常捕获与处理

捕获具体的异常类型，而不是使用通用的`except`语句。

```python
# 示例
try:
    risky_operation()
except ValueError as e:
    handle_value_error(e)
except KeyError as e:
    handle_key_error(e)
except Exception as e:
    handle_generic_exception(e)
    raise  # 抛出异常保持调用者知情
```

### 自定义异常类

为项目中常见的错误情况定义自定义异常类。

```python
# 示例
class CustomError(Exception):
    def __init__(self, message):
        super().__init__(message)

# 使用自定义异常
def process_data(data):
    if not data:
        raise CustomError("Data is empty")
```

## 7. 最佳实践

### 避免全局变量

优先使用函数参数和返回值传递数据，而不是依赖全局变量。

```python
# 示例
def calculate_total(items):
    total = 0
    for item in items:
        total += item
    return total
```

### 使用生成器表达式

对于简单的迭代和过滤，使用生成器表达式。

```python
# 示例
filtered_data = (item for item in data if item > 0)
```

### 合理使用装饰器

使用装饰器来增强函数的功能，如日志记录、性能分析等。

```python
# 示例
import functools

def log_function_call(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__} with args={args}, kwargs={kwargs}")
        return func(*args, **kwargs)
    return wrapper
```
