# 环境简述
操作系统：Windows

JDK版本：1.8.0_202

apktool版本: 2.3.0

# 关键字

## $
类名后加$XX代表是这个类的内部类，如果为数字代表匿名内部类。

## .local
格式为：

.local 寄存器, 变量名字符串:类型

	.local v2, "offline_mode":Z

有助于反编译出java代码。

## .locals
声明该方法需要使用的寄存器数量（从v0开始），如果超过该数量会抛出异常。

## .prologue
方法内代码的起始位置。

## .catch
格式为：

.catch 捕获异常类型; {try块开始标记 .. try块结束标记} catch块标记

	.catch Ljava/lang/Exception; {:try_start_0 .. :try_end_36} :catch_24

### 在try块内的寄存器引用有作用域限制，离开try块后会被清空，继续调用会抛出异常

## .line
声明该位置在源代码中的行数，有助于反编译出java代码。

