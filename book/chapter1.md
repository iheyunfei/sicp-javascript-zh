# 1 使用函数构造抽象

> - 来源：[Building Abstractions with Functions](https://sicp.comp.nus.edu.sg/chapters/1)
> - 译者：[塔希](https://github.com/iheyunfei/)
> - 协议：[CC BY-NC-SA 4.0](http://creativecommons.org/licenses/by-nc-sa/4.0/)

---

> The acts of the mind, wherein it exerts its power over simple ideas, are chiefly these three: 1. Combining several simple ideas into one compound one, and thus all complex ideas are made. 2. The second is bringing two ideas, whether simple or complex, together, and setting them by one another so as to take a view of them at once, without uniting them into one, by which it gets all its ideas of relations. 3. The third is separating them from all other ideas that accompany them in their real existence: this is called abstraction, and thus all its general ideas are made. —— John Locke An Essay Concerning Human Understanding (1690)

我们即将学习有关 *计算过程(computational process)* 的概念。计算过程是一种栖息于电脑中、抽象的存在。经过演化，过程可以操控另一种被称为 *数据(data)* 的抽象事物。人们创建程序来指导、控制各种过程，而 *程序(program)* 是一种含有许多规则的形式，主导着过程的运行。从形式上看，就像我们通过自己编写的咒语控制计算机中的精灵一样。

对于一个计算过程的理解可以参照巫师如何理解小精灵。小精灵并非由物质组成的实体，它们无法被看见和触摸。但是，它们却又是实际存在的。它们能完成智力性的任务、可以回答问题，并且通过在银行付钱或者控制工厂里机器人的手臂来对世界产生实际影响。我们用来“变出”过程的程序就如同巫师们用来召唤小精灵的咒语一样。程序是由神秘、晦涩的 *编程语言(programming languages)* 中各种符号表达式精心构建的，它们被用来描述可以完成我们所关心任务的计算过程。

在一台正常工作的计算机里，一个计算过程会严格且准确地的执行对应的程序。因此，“菜鸟”程序员就像巫师的学徒一样，必须经过事先学习，以图理解和预测他们通过咒语使用的各种“魔法”的后果。程序中即使很微小的的错误都可能导致复杂且无法预料的后果。

幸运的是，学习编程要比学习魔法安全得多，因为我们要面对的“小精灵”被一种安全的方式保存着。不过，现实世界中的编程依然要求谨慎、专业和智慧。举个例子，一个小小的程序错误都可能导致使用计算机辅助操控的飞机发生坠机、水坝崩坏或者工业机器人产生自毁行为。

软件工程大师们掌握着高超的构建程序的能力，所以他们才能合理地确信程序产生的过程，能够正确地完成其被安排的任务。软件工程大师们能够“预视”到系统的行为，知道该怎么组织程序的结构来避免意料之外的错误以及可能导致的严重后果，并且明白当错误出现时该怎么*定位、解决*它们。设计优良的计算系统，就像一个设计优良的汽车或核反应堆，是采用模块化设计的，所以每一部分都可以独立地被构建、替换和除错(debug)。


## 使用JavaScript编程

我们需要合适的语言来描述过程，为了达成这个目的，我们将会使用编程语言JavaScript。就如我们每天会用自然语言（英语，法语，日语）来表达我们日常的想法，用数学符号来描述数量的概念，我们的过程将会使用JavaScript来描述。JavaScript产生于1990年早期，通过内嵌于网页内部作为脚本，用来控制网页浏览器的行为。这门语言由Brendan Eich设计出，开始被称为Mocha，后改为*LiveScript*，最终命名为JavaScript。这个名字“JavaScript”是属于Sun Microsystems公司的一个商标。

尽管JavaScript作为一门语言，其诞生时的目的是为了控制网页浏览器，但JavaScript依然是一个通用编程语言。一个JavaScript *解释器(interpreter)* 就是一部用来执行由JavaScript编写的过程的机器。第一个JavaScript解释器是由Eich就职于Netscape Communications公司期间实现的，用在Netscape Navigator网页浏览器上。JavaScript的主要语言特性继承自Scheme和Self编程语言。Scheme是Lisp的一个方言，并且被当作原版《SICP》书籍的编程语言。从Scheme里，JavaScript继承了其大部分的函数式设计原则，例如静态作用域、一等函数公民和动态类型，这种继承的直接结果就是本书中的程序可以很直接、简单的从原书中的Scheme语言翻译成JavaScript语言。

JavaScript仅仅与Java在表面上有相似之处，最大的关联点就是名字中都带个Java而已。JavaScript和Java都沿用了C语言的程序块(block structure)结构。与Java和C这种编译成底层语言后执行的过程相比，JavaScript常常是被浏览器内建的解释器解释执行。在Netscape Navigator浏览器出现后，其他网页浏览器也开始提供内嵌的JavaScript解释器，包括微软的Internet Explorer浏览器（微软称其为JScript而非JavaScript）。JavaScript因为可以控制浏览器的行为而普及后，广受大众欢迎，进而引起了对JavaScript进行标准化的工作，最终产生了一个标准化的语言标准，被称为 *ECMAScript*。第一版的ECMAScript(ECMA 1997)标准由Guy Lewis Steele Jr. 主导制定于1997年6月。本书使用的是第六版，由Allen Wirfs-Brock主导制定，在2015年6月的ECMA大会上被接受。

网页可以执行内嵌其中的JavaScript程序已经成为互联网的共识，这促使了网页浏览器的开发者去实现JavaScript解释器。随着JavaScript程序变得越来越复杂，解释器的效率也变得越来越高，其中使用了一些精巧、复杂的技巧，例如 **[即时编译（JIT）](https://zh.wikipedia.org/wiki/%E5%8D%B3%E6%99%82%E7%B7%A8%E8%AD%AF)** 技术。大部分的JavaScript程序内嵌于网页，被浏览器解释执行，但是JavaScript也被用于编写苹果电脑桌面仪表板的小控件，以及控制一些软件或硬件的行为，比如Adobe Reader、Adobe Flash和一些通用的远程桌面设备。

不管怎样，对于一个在线教学编程书籍来说，可以被浏览器解释执行的能力使JavaScript成为了一门理想的编程语言。对JavaScript来说，通过在网页上点击执行JavaScript程序是非常自然的一件事——毕竟这就是JavaScript被设计出来的目的。从根本上来说，JavaScript拥有的语言特性使其成为了一个完美的工具，非常适合被用来学习、理解程序结构和数据结构的概念。同时也是一个完美的媒介，将程序结构和数据结构与支持它们的JavaScript语言特性联系起来。JavaScript的静态作用域、一等函数公民语言特性提供了一种简单、直接的途径来理解、应用抽象机制，动态类型则使得程序使用数据时不需要提前声明其类型。除了以上所有的考量之外，还有一点——使用JavaScript编程是很有趣的。
