有的 JS 语句一定要以分号结尾，所以 JS 中存在自动分号插入机制。

> Some [JavaScript statements](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements) must be terminated with semicolons and are therefore affected by automatic semicolon insertion (ASI):

- 空语句
- let，const，变量语句
- import， export， 模块申明
- 表达式语句
- 调试器
- continue， break，throw 语句
- return 语句

>Empty statement
>
>`let`, `const`, variable statement
>
>`import`, `export`, module declaration
>
>Expression statement
>
>`debugger`
>
>`continue`, `break`, `throw`
>
>`return`



ECMAScript 说明书提到了插入分号的三个规则

> The ECMAScript specification mentions[ three rules of semicolon insertion](https://tc39.github.io/ecma262/#sec-rules-of-automatic-semicolon-insertion).



1. 当遇到语法不允许的行结束符或者"}"的时候，插入分号。

1.  >A semicolon is inserted before, when a [Line terminator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Line_terminators) or "}" is encountered that is not allowed by the grammar.

```
{ 1 2 } 3 

// is transformed by ASI into 

{ 1 2 ;} 3;
```



2. 监测到输入流结束或者解析器不能将单输入流解析为一段完整的程序，在其后插入分号。

2.  > A semicolon is inserted at the end, when the end of the input stream of tokens is detected and the parser is unable to parse the single input stream as a complete program.



下面这个例子中，`++`不会作为一个前缀表达式应用到b上，因为在b 和 `++` 中间存在行结束符。

Here `++` is not treated as a [postfix operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators#Increment) applying to variable `b`, because a line terminator occurs between `b` and `++`.

```
a = b
++c

// is transformend by ASI into

a = b;
++c;
```



3. 当一个语句在语法上面是限制继续并且存在行结束符的时候，在后面插入分号。这些有“无行结束符”规则的语句有：(重新翻译)

3. > A semicolon is inserted at the end, when a statement with restricted productions in the grammar is followed by a line terminator. These statements with "no LineTerminator here" rules are:

- 前缀表达式(`++` `--`)   >PostfixExpressions (`++` and `--`)
- `continue`
- `break`
- `return`
- `yield`, `yield*`
- `module`

```
return
a + b

// is transformed by ASI into

return;
a + b;
```