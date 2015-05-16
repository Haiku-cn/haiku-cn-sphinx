Haiku编程学习
=======================

.. figure:: /_static/darkwyrm/ISBN_978-0-557-53969-7.jpg
  :figwidth: image
  :align: right
  :target: `lulu.com`_

  **ISBN: 978-0-557-53969-7** (`lulu.com`_)

Have you ever wanted to learn to program for Haiku (or something else) but never had the money or the chance? Has something else gotten in the way? Even though I still don't have any real motivation to write code, right now I have plenty of motivation for writing about code.

-- Darkwyrm

简介
------------------------

Haiku编程学习（Learning to Program with Haiku）由 DarkWyrm 编写，主要目的在于，为 Haiku 爱好者和愿意为 Haiku 开发程序的新手提供一个渐进的学习教程，从简单的编概念的讲解，函数的认识和学习，基本的 GUI 掌握，最后到构建一个完整的程序。您会发现，它虽然讲解的很简单，每一章节都不是很长，但是它给你提供了一个思路，一个从零到构建完整的程序的思路，慢慢的引导您了解整个开发的过程，摆脱入门新手的混沌，渐渐走进编程世界的佳境。

目录
------------------------

本教程分为五个部分，23 个章节。下面将会给出每个部分以及各章节的简单介绍，同时给出相应的链接。由于其中文翻译还未完全完成，对于已经完成的章节，我们会给出相应的中文链接；而对于未完成的部分，我们会提供相应的英语原文下载。

* 第一部分

    * :doc:`/develop/darkwyrm/learning/C01` ：主要讲解编程的基本概念，初探函数以及基本函数编写，以及 Haiku 或者类 unix 下 GCC 的使用方法。
    * :doc:`/develop/darkwyrm/learning/C02` ：探讨注释的种类和写法规范，编译器对代码的处理过程，以及如何进行代码的调试。
    * :doc:`/develop/darkwyrm/learning/C03` ：主要讲解数据类型，它们的存储方式，以及它们在函数和接口中的传递方式。
    * :doc:`/develop/darkwyrm/learning/C04` ：讲解条件语句和循环语句，以及通过示例了解如何应用条件和循环语句。
    * :doc:`/develop/darkwyrm/learning/C05` ：主要讲解数组，指针，以及字符串，并且提供项目实例和错误查找，方便对以上内容的深入理解，避免使用中可能出现的错误。
    * `小结 <>`_

* 第二部分

    * :doc:`/develop/darkwyrm/learning/C06` ：讲解了除 while 语句以外的 for 循环语句，switch 语句以及条件赋值语句。
    * :doc:`/develop/darkwyrm/learning/C07` ：讲解了内存的分配，堆与栈的区别，二进制数学运算（即对位的各种操作）。
    * :doc:`/develop/darkwyrm/learning/C08` ：主要讲解作用域的概念，常量的使用，以及文件的操作和各种常用函数使用说明。
    * :doc:`/develop/darkwyrm/learning/C09` ：主要讲解 C 语言中的难点 － 指针与多维数组，并且指明在使用中遇到的问题，如何来避免使用出错。
    * `小结 <>`_

* 第三部分

    * :doc:`/develop/darkwyrm/learning/C10` ：深入讲解引用，传引用或传值，函数指针，指针的指针和命令行参数，最后附加小项目“简易 cat”
    * :doc:`/develop/darkwyrm/learning/C11` ：深入介绍自定义类型，枚举类型，联合和结构体，最后给出一个较复杂的纸牌案例
    * :doc:`/develop/darkwyrm/learning/C12` ：C++ 入门，面向对象编程概念，类定义，构造和析构函数等
    * :doc:`/develop/darkwyrm/learning/C13` ：介绍了 C++ 的语言特性，继承，虚函数，和重载。十三虽不吉利，其中的内容比较核心，也比较容易理解。
    * :doc:`/develop/darkwyrm/learning/C14` ：首次介绍了如何编写 GUI 程序，并讲解了 Paladin IDE 的初步用法。

* 第四部分

    * :doc:`/develop/darkwyrm/learning/C15` ：首先简要介绍了 Haiku 的 API，即各个接口套件，从 Application 套件到 Translation 套件；然后讲解了事件编程，Haiku/Beos 的 Application 套件内部的消息机制，最后给出了一个实例，ClickMe。
    * :doc:`/develop/darkwyrm/learning/C16` ：讲解了我们之间未涉及到得内容，函数和操作符重载，复制构造函数，这两者都是 C++ 中的重要特性，有弊有利，如果运用得当，必能事半功倍，请务必尝试最后的项目，须知“纸上得来终觉浅，绝知此事须躬行”。
    * :doc:`/develop/darkwyrm/learning/C17` ：继续 Haiku GUI 应用的内容，在程序中使用菜单，包括为程序添加菜单，添加视图等内容。对于我们喜欢图形界面的用户来说，学了这么久的东西，终于“柳暗花明”了，看到写界面，就看到了希望。
    * :doc:`/develop/darkwyrm/learning/C18` ：列出了其余的窗口空间类型，回访了类型转换，给出了一个小项目，其中使用到了列表控件。虽然动脑有益，动手可以多得哟。
    * :doc:`/develop/darkwyrm/learning/C19` ：程序中总会用到各种东西，包括漂亮的图标，动画效果等等，本节简要介绍了 Translation 套件的用法，以及程序资源的打包工具和方法，一如既往，最后一个小项目 - Emo，喜怒哀乐，方为人生。

* 第五部分

    * :doc:`/develop/darkwyrm/learning/C20` ：主要介绍了存储套件(即Storage Kit)，以及对其中各个接口的简单描述，并且给出了简单的应用项目示例。
    * :doc:`/develop/darkwyrm/learning/C21` ：初步讲解了项目－ HaikuFortune，并且通过该项目具体介绍了 BFile 文件处理类以及构建它的框架，包括对项目编写和测试的步骤。
    * :doc:`/develop/darkwyrm/learning/C22` 
    * :doc:`/develop/darkwyrm/learning/C23` ：主要讲解在完成程序之前的，源代码打包，程序的发布，使用授权的选择，以及之后的进一步学习等内容。


参考资料和工具
------------------------

如果您是一个熟悉 unix/linux 的开发者，您可能对下面的内容有所了解，但是下面的资料包涵内容众多，多了解可以加深对编程理念的更深入的体会。如果您是一个开发新手或者是Windows 下的开发者，您可能会发现 Haiku 下的编程非常的有意思，学习下面的资料，熟悉里面介绍的工具将会对您更快的接受 Haiku 的理念，更好的学习本教程非常有用。

* `Bash和脚本 <BeOSBash教程>`_ 


.. _lulu.com: http://www.lulu.com/product/paperback/learning-to-program-with-haiku/11914307
