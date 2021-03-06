# 1.2 Functions and the Processes They Generate

> - 来源：[Functions and the Processes They Generate](https://sicp.comp.nus.edu.sg/chapters/11)
> - 译者：[塔希](https://github.com/iheyunfei/)
> - 协议：[CC BY-NC-SA 4.0](http://creativecommons.org/licenses/by-nc-sa/4.0/)

---

现在，我们已经见识了一些编程的要素：我们使用过基本的数学运算操作，然后将这些操作组合起来，并且通过声明复合函数来抽象这些组合后的的操作。但是，了解这些并不足以声称我们学会了如何去编程。我们现在的情况和刚学会如何移动国际象棋棋子的人一样，虽然了解基本的规则，但是对开局，策略，战术一无所知。和国际象棋初学者一样，我们还不知道编程领域中各种模式的用法。我们缺乏足够的知识去判断棋子的哪一步是值得的？(哪一个函数值得声明？)。我们缺乏足够的经验判断每一步的后果(比如，执行一个函数)。

把正在考虑的行为的结果进行可视化的能力，对于成为一名专业编程人员来说，是至关重要的，就像这种能力在其他合成性，创造性活动中的作用一样。举个例子，在成为一个专业摄影家的过程中，一个人必须学习如何观察各种景象，知道在各种可能的曝光和显影的条件<sup> [\[1\]]() </sup>下，镜像中的各个区域在影像中的明暗程度。只有这样，人才能反推对于想要效果应该作的取景、 亮度、曝光、和显影行为。对于编程来说也是一样的，我们需要对于计算过程中各种动作行为作出规划和通过程序去控制其进程。为了成为一个专家，我们必须学会如何看清各种类型函数产生的计算过程。这样，我们才能学着如何去构造出可靠的程序，并使其表现出我们想要的行为。

一个函数就是相对于于计算过程局部演化的一种形式。它描述了计算过程的每一步是如何建立在上一步上。We would like to be able to make statements about the overall, or *global*, behavior of a process whose local evolution has been specified by a function. This is very difficult to do in general, but we can at least try to describe some typical patterns of process evolution.

在这一节里，我们将会考察一些由简单函数产生的计算过程的“形状”。我们同样会研究计算过程消耗的各种重要的时间和空间计算资源的速率。将要考察的函数是非常简单的。它们在这里扮演的角色就像是是摄影技术中测试模式：作为极度简化的摄影模式，对其来说，而非实际的例子。

<small>

[1] The textbook was written at a time when photography commonly involved photographic development, a chemical process for making paper prints from photographic film.

<small>
