#北师大本科生毕业论文模板

#Beijing Normal University Bachelor Thesis Template

项目地址: https://github.com/Hggg/BNU-Bachelor-Template

##说明及注意事项
1.	**注意**：
	-	本模板基于北师大毕业论文规范[1]和图书馆word模板[2]制作，与图书馆模板大体上一致，***暂未***通过审核；
	
	-	在TeXLive2019/2020或MacTeX2019/2020上正常运行，在其他环境上可能存在无法复制中文的问题，见已知问题的4；
	
	-	若使用该模板则视为同意：制作者不承担任何可能由本模板引起的责任；不用于商业用途

2.	主文档为main，使用`\input{}`, `\include{}`命令调用其他文件，依次是preamble, cover, loc, abs-chinese, abs-english, preface, chap1, chap2 (自行添加更多), epilogue, bib, appendix, acknowledge；
	schoollogo为学校标志；
	comparison文档以图书馆模板为背景（黑色字体），模板字体改为红色，可以清晰对比本模板与图书馆模板，如果你对本模板的距离不满意，可以自行修改，参考6.部分实现原理

3.	必须使用XeLaTeX编译

4.	如何使用
	1.	编辑main导言区中的个人信息部分，包括：论文标题、英文标题、部院系、专业、学号、姓名、指导教师、指导教师职称、指导教师单位、年、月、日；模板会自动根据以上信息，生成对应的封面、承诺书等内容
	
	2.	在对应文件中输入以下内容：中文摘要(abs-chinese)、英文摘要(abs-english)、前言(preface)、第一章(chap1)、第二章(chap2)、结语(epilogue)、参考文献(bib)、附录(appendix)、致谢(acknowledge)等；如有你不需要的部分，注释掉即可；模板中使用了`\lipsum`,`\zhlipsum`生成了随机文本填充正文、使用规范[1]对各项的说明填充了其他文本，输入你的内容时删掉即可；
	
	3.	本模板只预置了少量的宏包、自定义宏和环境，如果需要，自行添加；若有冲突，适当调整顺序
	
	4.	首次编译时间可能较长；目录、交叉引用等内容可能需要多次编译

5.	一些个性化设定：
	1.	关于参考文献：规范[1]中推荐使用GB/T 7714-2015。本模板默认使用`bibliography`环境（因此需要你自行生成或输入符合要求的条目）；
	另外也可以使用`biblatex`宏包自动生成符合规定的参考文献，见preamble和bib中部分注释，同时见[5]
	
	2.	如果你的标题有两行：在相应位置输入你的标题；模板会自动换行，也可以手动使用`\\`换行；手动在cover中将
		
		>%\aeunderline[16.27cm]{}
		
		的注释去掉以画出第二条下划线

	3.	如果你使用英文写作：
		1.	注释掉main的以下命令以得到正确的首行缩进

			>	\setlength\parindent{2em}%中英文首行缩进2em，
		
		2.	视需要将目录、前言、结语、参考文献、附录、致谢等标题名称改为英文

6.	部分实现原理：由于图书馆模板中存在诸多小问题，如中英文摘要到页面上方的间距不同等，为了尽可能模拟图书馆模板，本模板大量使用`\vspace{}`, `\vspace*{}` 调整垂直间距，例如preamble中使用

	>	\titleformat{\chapter}{\vspace*{-19.8mm}\centering\fontsize{16}{16}\bfseries\heiti}{\thechapter}{1em}{\vspace*{-9.5mm}}

	修改`\chapter`使之向上平移19.8mm；
	comparison文档是由comparison文件夹中的tex文件生成的，其利用了`overlay`宏包，将图书馆模板设为背景；
	如果你对当前的距离不满意，可在comparison文件夹中进行对比、修改

7.	如果你不清楚某些代码的作用，不建议修改；
	不建议随意增加或删去空白行(有可能会影响垂直距离)	

8.	欢迎在致谢中提到我们；
	感谢图书馆工作人员提供的模板，尽管其存在若干问题，仍然给予了我们很多帮助；
	感谢LKX, LWH, LZX等同学的测试和反馈

9.	如果你有任何意见、建议，欢迎联系我们

	CHEN Hong: hchen@mail.bnu.edu.cn

	SHU Xuanlin: 201611130195@mail.bnu.edu.cn


## 已知问题
1.	***未***处理单双页的问题，建议在定稿后用Acrobat处理

2.	参考文献的水平缩进存在一定问题

3.	本模板基于由win平台的Acrobat生成的PDF（`ref/[2]`, `comparison/OWT`）制作，不同平台、软件生成的PDF间存在一定的肉眼难以分辨的区别

4.	**重要：**在某些环境，例如低于TeXLive2019或MacTeX2019的环境，中编译得到的PDF可能会有***无法复制中文***问题，经过测试、排查，该问题疑似由AutoFakeBold导致。
	更新至TeXLive2019/2020或MacTeX2019/2020可以完美解决此问题。
	另外也可通过修改cover等中的`\textbf`命令来解决，参考[6]，但此方法仍存在一些很奇怪的问题，如某些汉字无法加粗、某些文本复制出来后有重复等，不建议使用这种方法。
	此后**不会**对这一问题做进一步修复。


##	Build histroy
### Apr 11, 2020
1.	修复了致谢页的页码为黑体的问题

2.	关于preamble的修改

	1.	将preamble中关于引用的两个宏包`cite`, `biblatex`的位置进行了调整，并补充了说明

	2.	将preamble中的部分自定义宏和环境注释掉了，自行添加你需要的

	3.	对preamble的部分内容的顺序进行了调整

3.	现在默认不调用showkeys宏包了

4.	现在标题支持两行了

5.	增加了更新内容的说明


## ref
[1] 毕业论文写作规范 师教文[2007]186号(未找到链接，见附件)

>	9.参考文献
>
>	应是论文作者亲自考察过的对毕业论文有参考价值的文献，除个别专业的外，均应有外文参考文献。参考文献应具有权威性，要注意引用最新的文献。
>
>	按照参考文献在文中出现的顺序采用阿拉伯数字连续编号，参考文献著录格式可因专业不同而有所差异，但各专业应统一著录格式。建议院（系）按照本学科通行惯例制定参考文献著录格式，也可参考国家标准“信息与文献参考文献著录规则 GB/T 7714—2015（见附件）”或参照下面格式。
>
>	著录格式：
>
>	（1） 著作：[序号]作者1，作者2．译者．书名．版本．出版地：出版社，出版时间，引用部分起止页．
>
>	（2） 期刊：[序号]作者1，作者2．译者．文章题目．期刊名，年份，卷号(期数)： 引用部分起止页．
>
>	（3） 会议论文集：[序号]作者．译者．文章名．文集名．会址．开会年．出版地：出版社，出版时间，引用部分起止页．
>
>	注：文献中的作者数量低于三位时全部列出；超过三位时只列前三位，其后加“等”字即可；作者姓名之间用逗号分开；中外人名一律采用姓在前，名在后的著录法。

[2] 图书馆论文模板 http://etd.lib.bnu.edu.cn/Home/BKSIndex 或 http://bs.bnu.edu.cn/docs/20171025110639474112.dot 

[3] 北师大学术成果库 http://ir.bnu.edu.cn

[4] 刘海洋. LATEX 入门. 北京: 电子工业出版社, 2013. Print

[5] CTAN:biblatex https://www.ctan.org/tex-archive/macros/latex/contrib/biblatex-contrib/biblatex-gb7714-2015

[6]	使用CJKfakebold修复不能复制中文的问题 https://tex.stackexchange.com/questions/180168/fontspec-xecjk-autofakebold-and-copyable-chinese-characters-in-pdf
一个相关的讨论 https://github.com/CTeX-org/ctex-kit/issues/353

[7] TeXLive 官网 https://www.tug.org/texlive/
MacTeX 官网 https://tug.org/mactex/

Last Update: Apr 11, 2020