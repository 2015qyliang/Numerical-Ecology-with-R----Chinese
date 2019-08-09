# R语言在数量生态学中的应用

## 目录

- 前言
- 第一章：绪论
- [第二章：探索性数据分析](./Rmdscripts/chapter-02.html)
- [第三章：关联方法与关联矩阵](./Rmdscripts/chapter-03.html)
- [第四章：聚类分析](./Rmdscripts/chapter-04.html)
- [第五章：非约束性排序](./Rmdscripts/chapter-05.html)
- [第六章：典型排序](./Rmdscripts/chapter-06.html)
- [第七章：生态数据的空间分析](./Rmdscripts/chapter-07.html)
- [第八章：群落多样性分析](./Rmdscripts/chapter-08.html)

### 译者：梁其云

* 2019 年春于山东·威海 转译

#### 注: 第七章的笔记内容, 转述了'赖江山'老师翻译的<数量生态学--R语言的应用_第一版>相关的内容

#### 其他相关资源

- https://www.davidzeleny.net/anadat-r/doku.php/en:numecolr
- https://github.com/zdealveindy/anadat-r/tree/master/scripts
- https://github.com/JoeyBernhardt/NumericalEcology
- https://github.com/CMET-UGent/CMETNGS/tree/master/R

---

# 前言

生态学，婀娜多姿。

教授生态学是一门引人入胜的艺术，同时也是一门非常难以习得的艺术。
现代生态学研究的复杂性，已远远超过中学时代或者电影中对生态系统的轻描淡写。
而数量生态学则是另一种版本的故事。
由于某些不清楚的原因，部分科班出身的生态学工作者不太愿意使用数学工具帮助量化、理解自然界中的事物。
从事生物统计学和数量生态学的教师，应在教授这门课程之前说明数量生态学的必要性，同时提起受众的学习兴趣。

几十年来，生态学家（学生或者学术圈、私人、政府机构中的研究人员）很少会基于统计考虑来设计研究方案并数据收集，他们将数据的统计分析"外包"给"以此为生"的"专业人员"。
然而，在其他情况下，最终结果是由少量基本上数据和显著性测试汇总而来的大量数据，这些结果通常不能用于揭示结构中的左右。丰度
生态学和统计学的相互分离将限制诸多科学研究。
因此，在某种程度上，造成了生态学家与生物统计学家之间的双盲影响。
除了防止数据被利用外，这种双盲影响将进一步阻碍针对生态问题的特定解决方案。

为解决上述问题，需要培育一批有数学功底的生态学家。令人欣慰的是，这样的人涌现的越来越多。
这一情况对统计生态学来说是巨大的进步，与此同时，也逐渐涌现出一些高质量的相关书籍，，生态学家合理的设计实验并进行分析无意中增加了其责任意识。
目前存在的这种意识，将有助于教学工作的顺利进行。

虽然，有效的教授任务和统计学实践已在生态学研究人员中变得相当普遍；但是，对每个从业人员都适用的工具分析包依旧很匮乏。
生物统计学或者数量生态学课程**不实践永无意义**。
与商业应用相关的软件有很多，但是如果研究人员无法深度对此调研，那势必将限制未来相类似应用程序的发展。
此外，在大多数情况下，商业软件包是为比生态学家群体更大的受众所编写的，它们可能不包括分析生态数据所需的所有功能（专业领域的专业性不足）。
R语言解决了这个问题，这要归功于许多研究人员的奉献精神，他们创造并开源分享了软件包。
现在，教授者不再需要说"这就是PCA的工作方式..."，而可以换成"这是PCA的工作方式，下面我将给大家演示它的运算过程；通过演示教学，你也可以在任何时候、任何地点分析自己的实验数据"。

R语言的另一个基本特性是它的自学环境。
因此，一本关于R的书必须遵循这一哲学，并且必须为任何希望自己探索这个主题的人提供必要的支持。
这本书是为了在数值生态学的理论和实践之间架起一座桥梁供人翻越那道鸿沟。
我们最大的希望是它能让更多的从业者快乐工作与学习--寓教于乐。


自2011年第一版"数量生态学"出版以来，数量生态学和R语言都发生了诸多"进化"。
目前第二版在更新第一版中代码（代码由rstudio中的r markdown生成）的同时，提出新方法、以及针对现有方法的更多示例和主要方法的更为广泛的应用场景。

### 本书的主创团队：

Daniel Borcard	Montréal, QC, Canada

François Gillet	Besançon, France

Pierre Legendre	Montréal, QC, Canada

---

# 第一章：绪论

本章内容简介：

- 1.1 Why Numerical Ecology?
- 1.2 Why R?
- 1.3 Readership and Structure of the Book
- 1.4 How to Use This Book
- 1.5 The Data Sets
- 1.6 A Quick Reminder About Help Sources
- 1.7 Now It Is Time...

## 1.1 为什么是数量生态学?

生态数据的多元变量分析始于20世纪60年代，兴于70年代。
期间很多教科书出版：《the seminal Écologie numérique》(Legendre and Legendre 1979)和它的英文版本《Numerical Ecology》(Legendre and Legendre 1983)。
那些书籍的作者以一种全新的方式介绍了诸多广泛使用的统计分析技术，这不仅有助于研究人员理解现有的统计分析方法，同时也帮助他们能够以一种有序、合理的方式去选择、应用这些统计方法，进而达到他们的研究目的。
在这些书中不乏详尽的数学解释内容，并对各种分析技术进行了深入探讨，正因如此，这些可以很好的吸引住一些“小白”人群。

自那时起，数量生态学就已无处不在。
每一位认真的科研工作者深谙“梅花香自苦寒来”，代价与成果并存。
其他相关的教程也陆陆续续出版（e.g. Orlóci and Kenkel 1985; Jongman et al. 1995; McCune and Grace 2002; McGarigal et al. 2000; Zuur et al. 2007; Greenacre and Primicerio 2013; Wildi 2013）。
《数量生态学》于1998年出版第二版，于2012年出版了第三版，该书介绍了现有的统计分析方法的使用界限。
本书列举了诸多我们认为最重要的分析方法和开发工具，更加适用于用户。针对所提到的分析方法或者开发工具，本书给出了最为基本的应用示例

本书没有一一列举现存的所有的数据分析方法。所选择的分析方法的出发点主要基于我们自身定量群落分析的生态学家的科研经历。有些方法仅仅介绍了其主要框架，并没有进行详细介绍。

## 1.2 为什么选择R语言?

R语言的发展迅速并且拥有广泛地用户使用群体，因此不需要证明R语言在数量生态学中应用的合理性；同时，随着R语言的生态环境的不断发展，一些新方法的计算只能通过R包进行。

然而，本书并不适合作为R语言入门书籍。读者可以到R语言分析包的数据框网站（ http://www.R-project.org ）进行见多，获取开发工具的基本使用手册。
在使用本书之前，读者最好具备入门级的R语言能力（ 基本的语法、常规的使用操作没有障碍 ）。
由于本书中所分析的数据多数是多变量对象，因此本书第二章先从多变量对象开始。

本书不会详细介绍所使用的方法的所有函数，只是根据数据分析的情景，适当的调整函数，必要时添加个性化设置，进而提高受众的学习曲线，同时保证R分析包的合理规范使用。
同时，本书所使用的R分析包并不一定是针对特定问题的的最优的解决方案。

## 1.3 本书的受众与结构

本书适用于一切应用R语言进行数据分析的一切人员。
本书是一本具体的应用数据，内容简练，示例中详细介绍了数量生态学的使用方法。
本书每章开篇都会有一个简短的概要：简述了本章的主题，使读者了解本章的范围，同时能够在本章节中理解所述方法的观点。
部分章节可能篇幅较长。
总而言之，该书通过探索性多元数据分析的应用引导读者。
本书第二章先从一些探索性分析方法开始，从逻辑上与第三章关联度量和矩阵建立了联系，以后顺序介绍了聚类（第四章）、排序（第五章）、规范性排序（第六章）、空间分析（第七章）和群落多样性（第八章）等内容。
本书涵盖了从描述性、解释性到预测性的多种方法，可以用于解决多元生态分析中的各种问题。

## 1.4 如何使用这本书

将书中的知识融汇贯通必然离不开对计算机的操作。
读者可以采用“读书”与“实际操作”相结合的方式，边读书边练习，理论结合实践。
本书的编排结构之间具有衔接性，因此为了能有一个系统性的学习，读者可以按照本书的编排顺序进行学习。
每次进行新的章节的学习，读者应该重新建立空白的 R 工作空间。
本书中所使用的数据、R 代码以及相关的函数和程序包皆可在线下载(http://adn.biol.umontreal.ca/~numericalecology/numecolR/)。
一些自编函数已融合进每章节的分析流程中。

为了能够更好地了解每个函数的功能，读者可以采用逐步逐行运行的方式进行学习和探究；学习初期，太顺畅的“粘贴复制”并不利于系统性地掌握这门技术（推而广之——慢慢来会比较快）。
在学习初期，读者可以多去尝试使用 R 自带的帮助系统（?help），尽可能地多接触原生态的 R 环境（虽然有时代码中直接的“注释”信息更加明了，但是有时太明了的信息会遗失掉很多过程中的逻辑）。
本书主要是通过具体的、实际的案例引入函数使用的分析情景，对每个函数功能的“事事巨细”并非初衷；在读者逐渐掌握地过程中，可以逐步去探索相关函数的其他应用，将典型案例分析中的经验拓展应用至更加个性化的案例分析中。

每章的 R 代码独立成单独的整体，章节之间的代码文件互不影响，同时 R 代码脚本的开头已导入每章所需要使用的 R 分析包。

为了能够使读者熟悉每步代码的运行效果，本书采用“庖丁解牛”的方式进行相关知识点的讲解，即每个相对独立的代码操作都会紧跟着相应的结果展示，有助于读者更加形象具体地理解代码的操作过程与效果。
但当不再是初学者时，可以进一步的简化“庖丁解牛”式的学习方式。

有时读者可以通过代码底部的提示框了解函数的某些特性或者获得输出某种特定结果的技巧。
虽然，本书中提到的很多方法适用于示例数据，但是，读者一定要保持清醒的认识——并非所有都具有生态学意义。
文末会给读者留些习题，以期读者可以通过实践加深对知识的理解，进而获得正反馈不断地提升自己。

对于“老手”，本书鼓励读者自行编写代码以实现相同、甚至更优的功能。
部分章节最后会有“自产代码角”，以期读者可以根据给出的公式编写函数，使读者能够融会贯通。
这种“代码角”的方式可以帮助读者更加深入地理解某些关键方法的数学运算。

## 1.5 本书中的数据集

除了极个别的案例需要调用特定数据集进行演示之外，其余的数据集主要基于 R 自带的两个基本基本数据集。
由于数据集的更新换代，为了保持数据分析的可再现性，本书采用电子表格的方式提供相关的数据信息。
1）Doubs鱼类数据集，包含 3 个矩阵：第一个矩阵是 27 种鱼类在每个样方的多度，第二个矩阵包括11个与河流的水文、地形核水体化学属性相关的环境变量，第三个矩阵是样方的地理坐标。
2）甲蟎数据集，包括 3 个矩阵：第一个是 35 个形态多度数据，第二个是 5 个基质和微地形数据，第三个是 70 个取样点坐标。

## 1.6 R 帮助资源速览

R —— 自学型统计分析软件，自身携带丰富且强大的帮助系统。

- ?	获取关于函数的相关信息	前提是已载入相关的分析包
- ??	获取与关键字相关的基本信息	所有已安装的分析包
- CRAN + Google	

## 1.7 准备开始...

充分利用本书所使用的代码。
读者在充分理解之后，可自行修改代码进行探索分析。
希望各位读者能在应用 R 进行数量生态学分析过程中快乐学习与生活！
