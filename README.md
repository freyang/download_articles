
目的：批量下载一篇论文的参考文献（PDF）

现状：现有的软件有EndNote、WOS等，但是都是基于数据库中有导入过这篇论文的参考文献。

问题：有些论文，比如说我现在在看的一篇综述，有100多篇参考论文，但是WOS检索出来的参考文献条目为0。所以无法通过检索导出参考文献条目。网上的一些爬虫搜索下载的方法均是基于此条件的。

想法：所以现在的想法是通过一篇论文的PDF后的参考文献目录，将PDF转换成EXCEL或txt，自动分割存储作者和论文题目。（可通过文字识别）。第二步是通过获得的目录自动通过论文题目进行网页搜索，下载对应的PDF并保存下来。

难点：主要在第一步。现有网站和工具帮助实现PDF转Word，需要写一个分割题目的程序。


1、模拟登录

使用selenium与 chrome无头浏览器实现（PhantomJS项目已经不更新了）

pip install selenium

安装chromedriver，要将exe文件复制到Chorme安装目录和pytho安装目录下，再将Chorme安装目录添加到path环境中。

iframe获取元素那块还是没有弄清楚


2、对于arXiv的文章，需要的是文章编号以及文章题目

对于非arXiv的文章，需要的是文章会议以及文章题目

直接在读取的时候对文章进行分类，然后分开搜索


3、现存问题：如何在下载文件的时候重命名

4、5.28日新的问题：在下载的时候若出现网络错误，没有处理这类的情况。判断是否出现网络错误，而且接下来应该怎么做，重新暂停下来，记录现在的位置，过一段时间就再次发送请求看网络是否恢复，达到一定的错误量后，输出信息，终止程序。




对于pdf图标的元素性质

<a _ngcontent-bvi-c48="" aria-label="PDF" class="icon-pdf" href="/stamp/stamp.jsp?tp=&amp;arnumber=6787078"></a>

第一个class="List-results-items"就是搜索出来的第一个结果

