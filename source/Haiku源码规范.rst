Haiku 编码规范
=============================

本文不是很完整。如果某一特殊类型的规范在这里没有写明，您应该遵循已经写好的代码的风格（最好使用 Haiku 的源代码作为本文的参考）。如果你对此有更好的建议，你可以直接向 `我们 <http://www.haiku-os.org/contact>`_ 说明。请别向我们提供类似“我更喜欢这种类型的缩进风格，我们可以改成这样的么？”的建议。

由于时间原因，可能在某些地方，一些代码风格与我们的源码规范不一致。如果您能够帮忙对这些代码进行整理，我们将会非常欢迎。

相比于指定一个特定的代码风格，我们更主要的目的在于保证代码的前后一致；在经过一系列的外部代码贡献和补丁提交之后，我们希望Haiku的代码能够仍然保持整洁，一致，并且容易阅读和维护。

规范概况
------------------------------

保持缩进—使它们和你所贡献的其他代码保持保持前后一致。当你提交补丁的时候，你会看到这一规则贯穿整个代码规范。

缩进和空格
------------------------------

* 使用制表符来控制缩进。把你的编辑器的每个制表符设置为4个空格。
* Haiku的缩进风格与 `K&R <http://en.wikipedia.org/wiki/Indent_style#K.26R_style>`_ 风格非常接近。
* 在命名空间里的函数/类不需要进行缩进。
* 通常在每一级表达式前使用一个制表符，你可以参看下面的例子。

首先，让我们通过一些例子来认识主要的规范：

.. code-block:: cpp

    class Foo : public Bar {
    public:
                                        Foo(int32);
        virtual                        ~Foo();
 
        virtual	void                    SomeFunction(SomeType* argument);
 
        // 使用 tab 来控制长参数列表的缩进量:
        virtual	const char*            FunctionWithLotsOfArguments(const char* name,
                                            const char* path, const char* user);
    private:
                int32                    _PrivateMethod();
        static	int32                    _SomeStaticPrivateMethod();
 
                int32                    fMember;
                const char*              fPointerMember;
    };
     
     
    // 冒号 ':' 总是另起一行,之后就是初始化工作。
     
    Foo::Foo(int32 param)
        :
        Bar(int32* param),
        fMember(param),
        fPointerMember(NULL)
    {
	...
    }
     
     
    /*!	函数描述通常使用 doxygen 格式，需要注意的是， 这里的注释
	并不是为终端用户设计的文档，而是用于帮助理解和正确使用
	该段代码的文档。
    */
    template<class T>
    const T*
    Foo<T>::Bar(const char* bar1, T bar2)
    {
    	...
    }

    static int32
    my_static_function()
    {
        return 42;
    }

    if (someCondition) {
        DoSomething();
            // 对于单行的注释通常写在代码行之后，并且要另起一行，	
            // 而且还要控制一个制表符的缩进量
        DoSomethingElse();
    } else if (someOtherCondition) {
        DoSomethingElse();
        DoSomething();
    }
 
    if (someVeryVeryLongConditionThatBarelyFitsOnALine
        && someOtherCondition) {
        // && 操作符要放在下一行的起始位置,
        // 并且要保持一个制表符的缩进
        ...
    }
 
    if (someVeryVeryLongConditionThatBarelyFitsOnALine
        && (someVeryLongNestedConditionPart1
            || someVeryLongNestedConditionPart2)
        && lastPartOfSomeVeryVeryLongCondition
            != 0) {
        // 同一优先级的代码保持相同的缩进。
        ...
    }
 
    if (fMemberPointer->VeryLongFunctionCall(uint32 argument1,
        uint32 argument2, uint32 argument3) != NULL
        && someOtherCondition) {
        // 函数调用的圆括号当做是一个优先级
        // 这样就需要在第二行增加一个制表符的额外缩进
        ...
         
        localVariable = AnotherLongFunction(uint32 argument1,
            uint32 argument2, uint32 argument3);
                // 对于这个简单的分配任务，一个额外的
                // 缩进对于代码的可读性并没有太大提高
            
        anotherVariable = fSomeUselessRGBColor.alpha *
            (fSomeUselessRGBColor.red + fSomeUselessRGBColor.green
                + fSomeUselessRGBColor.green + fOffset.blue)
                / 3 + fBrightness;
                // 这一个表达式超过了两行, 我们可以增加
                // 一个制表符的缩进来区分括号中表达式的
                // 不同优先级运算。
    }
    
    
    for (int32 index = 0; index < count; index++) {
        DoSomething(index);
        DoSomethingElse(index);
    }
 
    // 对于单行的声明，可以不要使用大括号,直接把它放在新一行即可。
    // (但是对于多行语句，则必须把它们包含在大括号之中)
 
    if (condition)
        DoOneThingOnly(index);
     
    for (int32 index = 0; index < count; index++)
        DoOneThingOnly(index);
 
    // switch 条件语句格式
     
    switch (condition) {
        case label1:
            DoSomething();
            break;
    
        case label2:
        {
            // 由于这里存在 count 声明，因此需要使用一组
            // 大括号。
            int32 count;
            ...
            DoSomething();
            break;
        }
    }
     
    ...
    CallingSomeFunction(firstArgument * 2 + someMoreStuff,
            secondArgument, thirdArgument);
            // 对于较长的参数，另起一行是要使用缩进。
    ...
    
    const rgb_color kNeonBlue = {10, 10, 50, 255};

杂项
------------------------------

* 每一行不能够超过 80 列；并且在连接一行时，通常要缩进一个额外的制表符，而这则依赖于这些杂项的内容。
* 在函数之间空出两个行距。
* 在每个文件结尾包含一个换行符。

标识符
------------------------------

* 使用简单鲜明的标识符。避免使用类似 r，aMessage，theView，MyDraw(who's draw?) 等标识符；同时还要避免使用成对的标识符，例如：ProcessMessage 和 DoProcessMessage，AddTasks1 和 AddTask。在Haiku代码中推荐使用类似 rect，message，invokeMessage, view，targetView，DrawBorder，ProcessMessage 和 ProcessMessageinternals 或者ProcessMessageDetails 等的标识符。
* 类名，结构体名，类型名，命名空间和函数名应该以大些字符开头，并且在名字中间要使用一些大写字符（这有助于其他人可以更好的理解代码，但是请不要使用下划线）。
* 变量名要以小写字符开头，同样的在名字中间要使用一些大写字符。
* 成员变量名要以 “f” 字符开头，格式如下：

.. code-block:: cpp

    int32 fMemberVariable;


* 常量名要以 “k” 字符开头，格式如下：

.. code-block:: cpp

    const uint32 kOpenFile = 'open';

（需要注意的是，这种常量格式和标准的 Be API 常量名是不同的）

* 全局变量名要饰以 “g” 前缀字符，静态变量名同上面组合一样，但是要饰以 “s” 前缀字符。
* 私有的方法名要饰以一个 “_” 前缀。

变量声明
------------------------------

* 在变量的本地作用范围内声明它，要避免把所有的变量都集中在函数的头部进行声明（就像我们在 C 语言中所做的那样）。这样做的好处是可以很容易检查变量是否被合理的进行了初始化，并且代码段可以很容易的被复制粘贴到其他的地方。
* 尽量使用能够反映变量含义的名字，同时避免为了不同的目的而重复使用单个临时变量。
* 尽量使用全名，避免使用缩写，例如：使用 msg 来代替 message。提倡使用 rect，frame，bounds 等来替代r，使用 menuItem 代替 mi。

使用 Haiku 内置的 API，类型等
------------------------------

* 推荐使用 Haiku API 功能调用，而不是自己重新设计。
* 推荐使用 BobjestList 来代替 Blist。BobjectList 提供了安全类型，可选的项目权限，并且由于其良好的设计，附加的模板实例并不会增加代码的长度。
* 在进行字符串操作时，推荐使用 Bstring 来替代 malloc，strdup，free 等。
* 推荐使用 Bstring 中的 << 运算符来替代固定大小的缓冲区和 sprintf 函数。
* 推荐使用在 SupportDefs.h 中定义的类型 int32，unit32 等来代替 int，long 等。使用 status_t 来代替 int，int32 用以返回出错信息，在合适的地方使用 off_t 来代替 int64。

注释
------------------------------

* 在适当的地方对代码进行注释。
* 推荐使用 C++ 风格的注释。
* 注释要适当而不能太过多余。（下面即是注释过多的例子：）

  .. code-block:: cpp

      ...
      index++; //index 的自增运算
      ...
             
      ...
      /* InitProgress
       *
       */
      void
      InitProgress(int param1)
      {
      ...


* 推荐在需要注释的代码行前或后相近的地方进行注释（当需要对一个代码段进行注释时，在代码段前面进行注释；当需要对某一行代码进行注释时，在其下面一行缩进一个制表符，再进行注释）。

  .. code-block:: cpp

      // 回收站窗口需要显示所有已挂载卷的回收站中
      // 的文件
      // (对一个代码段所做的注释)
      BVolumeRoster volRoster;
      volRoster.Rewind();
      BVolume volume;
      while (volRoster.GetNextVolume(&volume) == B_OK) {
          if (!volume.IsPersistent())
              continue;
          ...
          ...
          BPoseView::WatchNewNode(&itemNode,watchMask,lock.Target());
              // 必须把节点显示放在时间之前，这是因为 
              // Model 将会缓存文件类型和偏好的程序。
              // (对上一行代码所做的注释)
    

* 尽量避免在代码行后进行注释，这将会产生诸多不便（通常推荐在独立行进行注释）。

  .. code-block:: cpp

        ...
        if (this < is && a < very && long != condition) { // ...
        ...
        if (this < is && a < very && long != condition) {
            // 该注释是关于上面的长条件语句的，
            // 在这里添加注释将会很容易理解。
        ...


* 不要把你的名字或者名字缩写添加到注释中，如果你提交的补丁被采用了，你的名字将会存在于 GIT 的签名日志中。所有的人都可以通过这种方式来识别你的代码。
* 避免在注释中添加自己的心情，不要在代码中包含以下类似的内容:

  .. code-block:: cpp

      // this is a hack!


相反的解释为什么你认为值得留意的代码是 hack：

  .. code-block:: cpp

      // 下面的代码是没有用的，它不能够很好的处理缓冲区溢出。


许可和版权
------------------------------

* 推荐的源文件的许可和版权声明格式如下：

  .. code-block:: cpp

     /*
      * Copyright 2004-2007 Haiku Inc. All rights reserved.
      * Distributed under the terms of the MIT License.
      *
      * Authors:
      *		Jonathan Smith, optional@email
      *		Developer Name, optional@email
      */

  假如所有的文件都受 “Haiku Inc.” 版权保护，并且所有作者的名字都以姓氏按字符先后排序。

* 公共头文件都应该受 “Haiku Inc.” 版权保护，并且不再列出作者名单。
* 假如您希望自己来进行授权，许可文件的首部应该如下所示；至于作者名字的排序，和示例中的相似：

  .. code-block:: cpp

     /*
      * Copyright 2007 Jane Doe, optional@email
      * Copyright 2003-2005 Some Developer, optional@email
      * All rights reserved. Distributed under the terms of the MIT License.
      */


* 在一些特殊情况下，你可能必须对已有文件的版权列表进行扩展。你必须为 “Haiku Inc.” 添加一行版权声明，并且参照示例一对作者名字进行排序，而不是仅仅从刚刚的例子和推荐方法中任选一种。
* 头文件中的版权声明中，在许可证和头部声明之间没有空行。
* 在版权声明头部之后（包括头文件中的头部声明），其他内容之前，必须有两个空行。

无用代码和调试代码
------------------------------

* 如果你无法保证自己贡献的代码的质量，请不要遗留无用的，有争议的或者使用 #if 0’ed 的代码。你的更改首先需要有很高的质量，并且能够很好地代替所要替代的代码。如果由于某些缘故，您希望收回你的代码或者仅仅把它们用作参考，你可以使用源代码控制工具
* 不要留下简单的被注释掉的调试输出代码。现在 BeDebug 解决了大部分代码的调试输出的工作。可以通过设置断点来调试代码，在 #if DEBUG 代码段中包含需要调试的代码。一定要保证调试的代码在编译时没有警告，并保持正确性（保证你的更改不会破坏已经调试过的代码，否则，就还需要对这些代码进行修改）。您也可以利用 Debug.h 中的其他工具来进行代码调试。

其他的要求
------------------------------

* 使用新型的组件（dynamic_cast，static_cast，const_cast，reinterpret_cast 等等）来代替过时的组件。
* 选用合适的常量。
* 如果可能的话，尽量选择使用 stack-allocated 对象来代替 heap-allocated 对象。
* 使用自动锁(AutoLock)，例如对所有的锁和其他的资源获取，不要直接使用 Blocker 中的 Lock() 和 Unlock()。在使用自动自动锁时,推荐使用 Autolock 模板而不要使用 BAutolock。
* 在声明时，不要在if语句中进行赋值。

  .. code-block:: cpp

      if ((err = entry.GetRef(&ref)) == B_OK)
      ...

* 避免在 while 循环语句的条件中进行赋值，例如：

  .. code-block:: cpp

        BMenuItem* item;
        int32 index = 0;
        while ((item = ItemAt(index++)) != NULL) {
            ...
   
  相反的在 for 语句的条件语句中，这略显冗长但是非常有效率。

  .. code-block:: cpp 

        for (int32 index = 0; ; index++) {
            BMenuItem* item = ItemAt(index);
            if (item == NULL)
                break;
            ...

* 在删除或者释放对象之前，不要做 NULL 检查。

  .. code-block:: cpp
       
        // 错误示例
        if (fIcon)
            delete fIcon;
        
        // 错误示例
        if (fIconBuffer)
            free(fIconBuffer);

* 不要在返回值两旁添加圆括号：

  .. code-block:: cpp

        // 错误示例
        return (fList.ItemAt(index));

* 在检查位掩码时需要使用圆括号，一般的格式如下：

  .. code-block:: cpp

        if ((a & 3) != 0 && (b & 4) == 0)
            ...
 
        // 错误 - C/C++ 运算符的优先级不同
        if (a & 3 && xyz)
            ...

* 尽量少用内联函数。
* 在构造函数内部使用初始化列表来代替初始化成员。
* 使用内置的 false/true 而不是 FALSE/TRUE #define。
* 根据字母顺序对 #include 声明排序，而且要将 “includes” 和 <includes> 分开排序。
* 一个源文件的头文件应该被包含在该文件内以保证它能够实现正常的编译，所有其他的头文件，从最常用的（POSIX）到最具体的（本地目录中的），都遵循一定的规定。为了对它们作字母排序，请根据他们所属的API进行分类进行，示例如下（但是不要作相关的注释）：

  .. code-block:: cpp

        #include "ThisClass.h"
         
        // POSIX API headers
        #include <stdio.h>
        #include <string.h>
         
        // Haiku API headers
        #include <File.h>
        #include <OS.h>
         
        #include <PrivateHeader.h>
 
        #include "OtherLocalHeaders.h"

* 如果没有必要，请不要使用 <路径名/include .h >；（例如 < sys/stat.h >）。
* 指针初始化时使用 NULL 而不是 0。
* 避免使用 goto。
* 不要使用构造函数调用的语法来初始化指针，例如，对于 NULL：

  .. code-block:: cpp

        // 错误示例
        BView* view(NULL);

  使用更加常规的赋值方式：

  .. code-block:: cpp

        BView* view = NULL;

  （至于适当的使用结构函数来调用堆栈对象和创建分配对象，请不要对此感到疑惑）。

* 在比较函数调用的结果/变量和某一个常量的大小时，不要把常量置于比较表达式的左侧：

  .. code-block:: cpp

        if (B_OK == file.InitCheck()) // 不要使用这种格式
            ...

  程序员使用这一方式来确保他们使用了比较而不是赋值。这种表示方法可能不是很常见，把重要的函数调用/调用放在相对不是很重要的右侧。当然 Haiku 不使用这种表示方法，一个错误的赋值可以由给出的警告而被发现。

* 推荐使用 C 格式的头文件（string.h，stdlib.h）来代替在 C++ 下的对等文件（cstring，cstdlib）：Haiku 的头文件通常是 C++ 所接受的，不需要使用这种变通措施

风格检查工具
------------------------------

由于下面的工具仍然存在一些问题，有时候可能会反馈错误的结果，但是它们在大多数时间还是能够正常使用，并且可以找出一些常见的问题。这些工具仍然还在开发之中，欢迎你提出一些有创意的建议。

* Checkstyle.py 是一个独立的 Python 程序（在 Haiku 源码树的 src/tools/checkstyle/ 下可以找到相关的源码）。它可以以标准输出的方式反馈与风格相关的问题，而且生成一个易于阅读的有高亮度提示的 HTML 报告。示例如下：

  .. code-block:: sh

     python src/tools/checkstyle/checkstyle.py src/apps/deskcalc

  （假如你处在Haiku源码树的顶层目录）这将会反复检查 src/apps/deskcalc 目录。你可以使用 --help 选项来了解它的使用方法。

* `HaikuCodingGuidelinesVIM`_ 是一个 Vim 文本编辑器集成在一起的脚本。

.. _HaikuCodingGuidelinesVIM: http://dev.haiku-os.org/wiki/HaikuCodingGuidelinesVIM
