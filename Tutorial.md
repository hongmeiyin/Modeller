<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html><head>
<link href="Tutorial_files/modeller.css" rel="stylesheet" type="text/css">
<link rel="canonical" href="https://salilab.org/modeller/tutorial/basic.html">
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<script type="text/javascript" src="Tutorial_files/modeller.js"></script>
<script type="text/javascript" src="Tutorial_files/escramble-new.js"></script>
<title>Tutorial</title>
</head>

<body>

<!-- Auto-generated file: do not edit (any changes will be lost) -->

<div class="rightlink">
<a class="salilab" title="To main Sali lab pages" href="https://salilab.org/">
<img src="Tutorial_files/salilab.png" alt="To main Sali lab pages"></a>

<a class="mobilemenu" title="Mobile menu" href="#" onclick="show_menu(); return false;">
<img src="Tutorial_files/mobilemenu.png" alt="Mobile menu"></a></div>

<div class="modheader">
</div>

<div class="blayout">
<div class="lbar">
<ul class="menu">
<li class="menu"><a href="https://salilab.org/modeller/">About MODELLER</a></li>
<li class="menu"><a href="https://salilab.org/modeller/news.html">MODELLER News</a></li>
<li class="menu"><a href="https://salilab.org/modeller/download_installation.html">Download &amp; Installation</a></li>
<li class="submenu"><a href="https://salilab.org/modeller/release.html">Release Notes</a></li>
<li class="submenu"><a href="https://salilab.org/modeller/supplemental.html">Data file downloads</a></li>
<li class="menu"><a href="https://salilab.org/modeller/registration.html">Registration</a></li>
<li class="submenu"><a href="https://salilab.org/modeller/nonacademic.html">Non-academic use</a></li>
<li class="menu"><a href="https://salilab.org/modeller/discussion_forum.html">Discussion Forum</a></li>
<li class="submenu"><a href="https://salilab.org/mm/postorius/lists/modeller_usage.salilab.org/">Subscribe</a></li>
<li class="submenu"><a href="https://salilab.org/mm/hyperkitty/list/modeller_usage@salilab.org/latest">Archives</a></li>
<li class="menu"><a class="this" href="https://salilab.org/modeller/documentation.html">Documentation</a></li>
<li class="submenu"><a href="https://salilab.org/modeller/FAQ.html">FAQ</a></li>
<li class="submenu"><a href="https://salilab.org/modeller/tutorial/">Tutorial</a></li>
<li class="submenu"><a href="https://salilab.org/modeller/manual/">Online manual</a></li>
<li class="submenu"><a href="https://salilab.org/modeller/wiki/">Wiki</a></li>
<li class="menu"><a href="https://salilab.org/modeller/developers_pages1.html">Developers' Pages</a></li>
<li class="menu"><a href="https://salilab.org/modeller/contact.html">Contact Us</a></li>
</ul>

</div>
<div class="main">

<h1>Tutorial</h1>
<hr>

<h2>Basic example:<br>
Modeling lactate dehydrogenase from <em>Trichomonas vaginalis</em> based on a
single template.(基于单一模板对阴道毛滴虫乳酸脱氢酶进行建模)</h2>

<p><i>All input and output files for this example are available to download,
in either <a href="https://salilab.org/modeller/tutorial/basic-example.zip">zip format (for Windows)</a> or
<a href="https://salilab.org/modeller/tutorial/basic-example.tar.gz">.tar.gz format (for Unix/Linux)</a>.</i></p>

<p>A novel gene for lactate dehydrogenase was identified from the genomic
sequence of <em>Trichomonas vaginalis</em> (TvLDH)(从阴道毛滴虫（Trichomonas vaginalis）的基因组序列中鉴定出一个新的乳酸脱氢酶基因（TvLDH）). The corresponding protein
had a higher similarity to the malate dehydrogenase of the same species (TvMDH)
than to any other LDH(该对应蛋白与同一物种的苹果酸脱氢酶（TvMDH）的相似性高于与任何其他乳酸脱氢酶（LDH）的相似性). We hypothesized that TvLDH arose from TvMDH by
convergent(收敛的) evolution relatively recently(我们假设TvLDH是通过趋同进化最近从TvMDH演化而来的). Comparative models were constructed
for TvLDH and TvMDH to study the sequences in the structural context and to
suggest site-directed mutagenesis experiments for elucidating specificity
changes in this apparent case of convergent evolution of enzymatic specificity.
(本研究构建了TvLDH和TvMDH的比较模型，旨在从结构角度分析序列特征，并为阐明这一酶特异性趋同进化现象中的特异性变化提出定点突变实验方案。)
The native and mutated enzymes were expressed and their activities were
compared.</p>

<p>The individual modeling steps of this example are explained below. Note
that we go through every step in this tutorial to build a model knowing only
the amino acid sequence(请注意，在本教程中，我们将逐步演示如何仅凭氨基酸序列构建模型). In practice you may already know the related
structures, and may even have an alignment from another program, so you can
skip one or more steps.(在实际操作中，您可能已经了解相关的结构，甚至可能已经从其他程序中获得了对齐结果，因此您可以跳过一个或多个步骤。) Alternatively, for very simple applications you
may be able to use the <a href="https://salilab.org/modweb">ModWeb web server</a> rather than
Modeller itself.</p>

<h3>1. Searching for structures related to TvLDH(搜索与TvLDH相关的结构)</h3>
<p>First, it is necessary to put the target TvLDH sequence into the PIR format
readable by <span class="progs">MODELLER</span> (file
"<span class="filename">TvLDH.ali</span>").</p>

<pre class="filecontent">&gt;P1;TvLDH
sequence:TvLDH:::::::0.00: 0.00
MSEAAHVLITGAAGQIGYILSHWIASGELYGDRQVYLHLLDIPPAMNRLTALTMELEDCAFPHLAGFVATTDPKA
AFKDIDCAFLVASMPLKPGQVRADLISSNSVIFKNTGEYLSKWAKPSVKVLVIGNPDNTNCEIAMLHAKNLKPEN
FSSLSMLDQNRAYYEVASKLGVDVKDVHDIIVWGNHGESMVADLTQATFTKEGKTQKVVDVLDHDYVFDTFFKKI
GHRAWDILEHRGFTSAASPTKAAIQHMKAWLFGTAPGEVLSMGIPVPEGNPYGIKPGVVFSFPCNVDKEGKIHVV
EGFKVNDWLREKLDFTEKDLFHEKEIALNHLAQGG*
</pre>
<p class="smallfilename">File: TvLDH.ali</p>

<p>The first line contains the sequence code, in the format
"<em>&gt;P1;code</em>". The second line with ten fields separated by colons
generally contains information about the structure file, if applicable.(第二行包含十个以冒号分隔的字段，通常包含关于结构文件的信息（如适用）) Only
two of these fields are used for sequences, "<em>sequence</em>" (indicating
that the file contains a sequence without known structure) and "<em>TvLDH</em>"
(the model file name). The rest of the file contains the sequence of TvLDH,
with "*" marking its end. The standard one-letter amino acid codes are used.
(Note that they must be upper case; some lower case letters are used for
non-standard residues.(使用标准的一字母氨基酸代码。（注意：这些代码必须使用大写字母；部分小写字母用于表示非标准残基。）) See the file <tt>modlib/restyp.lib</tt> in the
Modeller distribution for more information.)</p>

<p>A search for potentially related sequences of known
structure can be performed by the <strong>Profile.build()</strong> command of
<span class="progs">MODELLER</span>.(可以通过MODELLER的Profile.build()命令搜索具有已知结构的潜在相关序列) The following script, taken line by line,
does the following (see file "<span class="filename">build_profile.py</span>"):</p>

<ol>
<li>Initializes the 'environment' for this modeling run, by creating a new
'Environ' object. Almost all MODELLER scripts require this step, as the new
object (which we call here 'env', but you can call it anything you like) is
needed to build most other useful objects.</li>
         
(初始化本次建模运行的“环境”，通过创建一个新的“Environ”对象。几乎所有MODELLER脚本都需要执行此步骤，因为该新对象（在此我们称其为“env”，但您可以随意命名）是构建其他大多数有用对象的必要条件。)

<li>Creates a new 'SequenceDB' object, calling it 'sdb'. 'SequenceDB'
objects are used to contain large databases of protein sequences.</li>
(创建一个新的 ‘SequenceDB’ 对象，并将其命名为 ‘sdb’。'SequenceDB'对象用于存储大量蛋白质序列数据库。)

<li>Reads a text format file containing non-redundant PDB sequences at 95%
sequence identity into the <tt>sdb</tt> database. The sequences can be found
in the file "<span class="filename">pdb_95.pir</span>" (which can be downloaded
using the link at the top of this page). Like the
previously-created alignment, this file is in PIR format. Sequences which
have fewer than 30 or more than 4000 residues are discarded, and non-standard
residues are removed.</li>

(将包含95%序列同一性非冗余PDB序列的文本文件（格式为PIR）读入sdb数据库。这些序列存储在文件"pdb_95.pir"中（可通过本页顶部链接下载）。与此前创建的比对文件类似，该文件采用PIR格式。系统会自动丢弃残基数少于30或多于4000的序列，并移除非标准残基)

<li>Writes a binary machine-specific file containing all sequences read in the
previous step.</li>

(写入一个二进制机器特定文件，其中包含上一步骤中读取的所有序列)

<li>Reads the binary format file back in. Note that if you plan to use the
same database several times, you should use the previous two steps only the
first time, to produce the binary database. On subsequent runs, you can omit
those two steps and use the binary file directly, since reading the binary
file is a lot faster than reading the PIR file.</li>

(读取二进制格式文件。请注意，如果你计划多次使用同一个数据库，你应该只在第一次使用时执行前两个步骤，以生成二进制数据库。在后续运行中，你可以省略这两个步骤，直接使用二进制文件，因为读取二进制文件比读取PIR文件快得多)

<li>Creates a new 'Alignment' object, calling it 'aln', reads our query
sequence "<em>TvLDH</em>" from the file
"<span class="filename">TvLDH.ali</span>", and converts it to a profile
'prf'. Profiles contain similar information to alignments, but are more
compact and better for sequence database searching.</li>

(创建一个新的“对齐”对象，命名为“aln”，从文件“TvLDH.ali”中读取查询序列“TvLDH”，并将其转换为一个“prf”文件。文件包含与对齐类似的信息，但更加紧凑，更适合序列数据库搜索)

<li>Searches the sequence database 'sdb' for our query profile 'prf'.
Matches from the sequence database are added to the profile.</li>

(在序列数据库'sdb'中搜索我们的查询文件'prf'。从序列数据库中匹配到的序列将被添加到该文件中。)

<li>Writes a profile of the query sequence and its homologs (see file 
"<span class="filename">build_profile.prf</span>"). The equivalent information
is also written out in standard alignment format.</li>
</ol>

(生成查询序列及其同源序列的特征描述（参见文件“build_profile.prf”）。等效信息也将以标准比对格式输出)

<pre class="filecontent">from modeller import *

log.verbose()
env = Environ()

#-- Prepare the input files

#-- Read in the sequence database
sdb = SequenceDB(env)
sdb.read(seq_database_file='pdb_95.pir', seq_database_format='PIR',
         chains_list='ALL', minmax_db_seq_len=(30, 4000), clean_sequences=True)

#-- Write the sequence database in binary form
sdb.write(seq_database_file='pdb_95.bin', seq_database_format='BINARY',
          chains_list='ALL')

#-- Now, read in the binary database
sdb.read(seq_database_file='pdb_95.bin', seq_database_format='BINARY',
         chains_list='ALL')

#-- Read in the target sequence/alignment
aln = Alignment(env)
aln.append(file='TvLDH.ali', alignment_format='PIR', align_codes='ALL')

#-- Convert the input sequence/alignment into
#   profile format
prf = aln.to_profile()

#-- Scan sequence database to pick up homologous sequences
prf.build(sdb, matrix_offset=-450, rr_file='${LIB}/blosum62.sim.mat',
          gap_penalties_1d=(-500, -50), n_prof_iterations=1,
          check_profile=False, max_aln_evalue=0.01)

#-- Write out the profile in text format
prf.write(file='build_profile.prf', profile_format='TEXT')

#-- Convert the profile back to alignment format
aln = prf.to_alignment()

#-- Write out the alignment file
aln.write(file='build_profile.ali', alignment_format='PIR')

</pre>
<p class="smallfilename">File: build_profile.py</p>

<p>This is a regular Python script, and so can be run with a command
similar to the following at your command line:</p>

<p><tt>python3 build_profile.py &gt; build_profile.log</tt></p>

<p><i>Note that on some systems the Python interpreter is called
<tt>python2</tt> or <tt>python</tt> rather than <tt>python3</tt>.
The full path to the Python interpreter may also be necessary, such as
<tt>/usr/bin/python</tt> on a Linux or Mac machine
or <tt>C:\python27\python.exe</tt> on a Windows system. If Python is not
installed on your machine, Modeller also includes a basic Python 2.3
interpeter as <tt>mod&lt;version&gt;</tt>. For example, to run this script
using Modeller 10.0's own interpreter, use <tt>mod10.0 build_profile.py</tt>.
Note that <tt>mod10.0</tt> automatically creates a <tt>build_profile.log</tt>
logfile.</i></p>

(需注意，在某些系统中，Python解释器的名称可能是python2或python而非python3。有时可能需要指定Python解释器的完整路径，例如Linux/Mac系统中的/usr/bin/python或Windows系统中的C:\python27\python.exe。若系统中未安装Python，Modeller自带一个基础的Python 2.3解释器，可通过mod<版本号>调用。例如，使用Modeller 10.0自带的解释器运行脚本时，命令为mod10.0 build_profile.py。注意：mod10.0会自动生成日志文件build_profile.log)

<p>(You can get a command line using xterm or GNOME Terminal in Linux,
Terminal in Mac OS X, or the 'Modeller' link from your Start Menu in Windows.
For more information on running Modeller, see
<a href="https://salilab.org/modeller/release.html">the release notes</a>. For more information
on using Python, see the <a href="http://www.python.org/">Python web site</a>.
Note that you can use other Python modules within your Modeller scripts, if
Python is correctly installed on your system.)</p>

(在Linux系统中可通过xterm或GNOME Terminal获取命令行界面，Mac OS X系统使用Terminal，Windows系统则通过开始菜单中的'Modeller'快捷方式启动。更多关于运行Modeller的详细信息，请参阅版本说明文档。关于Python的使用方法，请参考Python官方网站。需注意的是，如果系统中已正确安装Python，您可以在Modeller脚本中使用其他Python模块。)

<p>The <strong>Profile.build()</strong> command has many options. In this
example <strong>rr_file</strong> is set to use the BLOSUM62 similarity matrix
(file "<span class="filename">blosum62.sim.mat</span>" provided in the
<span class="progs">MODELLER</span> distribution). Accordingly, the parameters
<strong>matrix_offset</strong> and <strong>gap_penalties_1d</strong> are set to
the appropriate values for the BLOSUM62 matrix. For this example, we will run
only one search iteration by setting the parameter
<strong>n_prof_iterations</strong> equal to 1. Thus, there is no need
for checking the profile for deviation (<strong>check_profile</strong> set to
False). Finally, the parameter <strong>max_aln_evalue</strong> is set to 0.01,
indicating that only sequences with e-values smaller than or equal to 0.01 will
be included in the final profile.</p> 

(Profile.build()命令提供多种参数选项。在本示例中，rr_file参数设置为使用BLOSUM62相似性矩阵（该矩阵文件"blosum62.sim.mat"包含在MODELLER安装包中）。相应地，matrix_offset和gap_penalties_1d参数也被设置为适用于BLOSUM62矩阵的对应值。本示例中我们将n_prof_iterations参数设为1，表示仅执行一次搜索迭代，因此无需检查profile偏差（check_profile设为False）。最后，max_aln_evalue参数设置为0.01，表示仅将e值小于等于0.01的序列纳入最终profile)

<h3>2. Selecting a template</h3>
<p>The output of the "<span class="filename">build_profile.py</span>" script is
written to the "<span class="filename">build_profile.log</span>" file.
<span class="progs">MODELLER</span> always produces a log file. Errors and
warnings in log files can be found by searching for the "<em>_E&gt;</em>" and
"<em>_W&gt;</em>" strings, respectively.
<span class="progs">MODELLER</span> also writes the profile in text format to
the "<span class="filename">build_profile.prf</span>" file. An extract (omitting the aligned sequences)
 of the output file can be seen next. The first 6 commented lines indicate the input parameters used in
<span class="progs">MODELLER</span> to build the profile. Subsequent lines correspond to the detected
similarities by <strong>Profile.build()</strong>.</p>

("build_profile.py"脚本的输出结果将写入"build_profile.log"文件。MODELLER始终会生成日志文件。通过搜索"_E>"和"_W>"字符串可分别定位日志文件中的错误和警告信息。MODELLER同时会将profile以文本格式写入"build_profile.prf"文件。下文展示了该输出文件的节选内容（已省略比对序列部分）。前6行注释内容显示MODELLER构建profile时使用的输入参数，后续各行则对应Profile.build()检测到的相似性结果。)

<pre class="filecontent"># Number of sequences:     30
# Length of profile  :    335
# N_PROF_ITERATIONS  :      1
# GAP_PENALTIES_1D   :   -900.0   -50.0
# MATRIX_OFFSET      :    0.0
# RR_FILE            : ${MODINSTALL8v1}/modlib//as1.sim.mat
    1 TvLDH                                    S     0   335     1   335     0     0     0    0.    0.0
    2 1a5z                                     X     1   312    75   242    63   229   164   28.   0.83E-08
    3 1b8pA                                    X     1   327     7   331     6   325   316   42.    0.0
    4 1bdmA                                    X     1   318     1   325     1   310   309   45.    0.0
    5 1t2dA                                    X     1   315     5   256     4   250   238   25.   0.66E-04
    6 1civA                                    X     1   374     6   334    33   358   325   35.    0.0
    7 2cmd                                     X     1   312     7   320     3   303   289   27.   0.16E-05
    8 1o6zA                                    X     1   303     7   320     3   287   278   26.   0.27E-05
    9 1ur5A                                    X     1   299    13   191     9   171   158   31.   0.25E-02
   10 1guzA                                    X     1   305    13   301     8   280   265   25.   0.28E-08
   11 1gv0A                                    X     1   301    13   323     8   289   274   26.   0.28E-04
   12 1hyeA                                    X     1   307     7   191     3   183   173   29.   0.14E-07
   13 1i0zA                                    X     1   332    85   300    94   304   207   25.   0.66E-05
   14 1i10A                                    X     1   331    85   295    93   298   196   26.   0.86E-05
   15 1ldnA                                    X     1   316    78   298    73   301   214   26.   0.19E-03
   16 6ldh                                     X     1   329    47   301    56   302   244   23.   0.17E-02
   17 2ldx                                     X     1   331    66   306    67   306   227   26.   0.25E-04
   18 5ldh                                     X     1   333    85   300    94   304   207   26.   0.30E-05
   19 9ldtA                                    X     1   331    85   301    93   304   207   26.   0.10E-05
   20 1llc                                     X     1   321    64   239    53   234   164   26.   0.20E-03
   21 1lldA                                    X     1   313    13   242     9   233   216   31.   0.31E-07
   22 5mdhA                                    X     1   333     2   332     1   331   328   44.    0.0
   23 7mdhA                                    X     1   351     6   334    14   339   325   34.    0.0
   24 1mldA                                    X     1   313     5   198     1   189   183   26.   0.13E-05
   25 1oc4A                                    X     1   315     5   191     4   186   174   28.   0.18E-04
   26 1ojuA                                    X     1   294    78   320    68   285   218   28.   0.43E-05
   27 1pzgA                                    X     1   327    74   191    71   190   114   30.   0.16E-06
   28 1smkA                                    X     1   313     7   202     4   198   188   34.    0.0
   29 1sovA                                    X     1   316    81   256    76   248   160   27.   0.93E-03
   30 1y6jA                                    X     1   289    77   191    58   167   109   33.   0.32E-05 
</pre>

<p class="smallfilename">File: build_profile.prf</p>

<p>The most important columns in the <strong>Profile.build()</strong> output
are the second, tenth, eleventh and twelfth columns. The second column reports 
the code of the PDB sequence that was compared with the target sequence. 
The PDB code in each line is the representative of a group of PDB sequences 
that share 95% or more sequence identity to each other and have less than 30 
residues or 30% sequence length difference. The eleventh column reports the 
percentage sequence identities between TvLDH and a PDB sequence normalized by 
the lengths of the alignment (indicated in the tenth column). In general, 
a sequence identity value above approximately 25% indicates a potential
template unless the alignment is short (i.e., less than 100 residues). A
better measure of the significance of the alignment is given in the twelfth
column by the e-value of the alignment. In this example, six PDB sequences
show very significant similarities to the query sequence with e-values equal
to 0. As expected, all the hits correspond to malate dehydrogenases
(<span class="pdb">1bdm:A</span>,
<span class="pdb">5mdh:A</span>, <span class="pdb">1b8p:A</span>, 
<span class="pdb">1civ:A</span>, <span class="pdb">7mdh:A</span>, and 
<span class="pdb">1smk:A</span>).  To select the most appropriate template for
our query sequence over the six similar structures, we will use the 
<strong>Alignment.compare_structures()</strong> command to assess the structural
and sequence similarity between the possible templates (file
"<span class="filename">compare.py</span>").
         
(Profile.build()输出结果中最重要的列为第二、第十、第十一和第十二列。第二列显示与目标序列比对的PDB序列代码，每个PDB代码代表一组序列相似性≥95%、残基差异＜30个或序列长度差异＜30%的PDB序列集合。第十一列报告TvLDH与PDB序列的百分比序列同一性（按第十列显示的比对长度标准化）。通常，若序列同一性＞25%（且比对长度≥100个残基）提示该序列可能作为模板。第十二列提供的比对e值能更好反映比对显著性。本示例中，6个PDB序列（1bdm:A、5mdh:A、1b8p:A、1civ:A、7mdh:A和1smk:A）与查询序列高度相似（e值=0），均为苹果酸脱氢酶。我们将通过Alignment.compare_structures()命令（"compare.py"文件）进一步评估这些候选模板的结构与序列相似性，以选择最优模板。)
</p><pre class="filecontent">from modeller import *

env = Environ()
aln = Alignment(env)
for (pdb, chain) in (('1b8p', 'A'), ('1bdm', 'A'), ('1civ', 'A'),
                     ('5mdh', 'A'), ('7mdh', 'A'), ('1smk', 'A')):
    m = Model(env, file=pdb, model_segment=('FIRST:'+chain, 'LAST:'+chain))
    aln.append_model(m, atom_files=pdb, align_codes=pdb+chain)
aln.malign()
aln.malign3d()
aln.compare_structures()
aln.id_table(matrix_file='family.mat')
env.dendrogram(matrix_file='family.mat', cluster_cut=-1.0)
</pre>
<p class="smallfilename">File: compare.py</p>

<p>In this case, we create an (initially empty) alignment object 'aln' and then
use a Python 'for' loop to instruct MODELLER to read each of the PDB files.
(Note that in order for this to work, you must have all of the PDB files in
the same directory as this script, either downloaded from the PDB website or
from the archive linked at the top of this page.) We use the
<strong>model_segment</strong> argument to ask only for a single chain to be
read from each PDB file (by default, all chains are read from the file). As
each structure is read in, we use the <strong>append_model</strong> method to
add the structure to the alignment.</p>

(在此案例中，我们首先创建一个（初始为空的）比对对象"aln"，随后通过Python的"for"循环指令MODELLER逐个读取PDB文件。（注意：要使此操作成功执行，必须将所有PDB文件置于与脚本相同的目录中，这些文件可从PDB官网或本页顶部链接的归档中下载。）我们使用model_segment参数指定仅读取每个PDB文件中的单条链（默认情况下会读取文件中的所有链）。每当读入一个结构时，便通过append_model方法将该结构添加至比对中。)

<p>At the end of the loop, all of the structures are in the alignment, but they
are not ideally aligned to each other (<strong>append_model</strong> creates
a simple 1:1 alignment with no gaps). Therefore, we improve this alignment by
using <strong>malign</strong> to calculate a multiple sequence alignment.
The <strong>malign3d</strong> command then performs an iterative least-squares
superposition of the six 3D structures, using the multiple sequence alignment
as its starting point. The
<strong>compare_structures</strong> command compares the structures according
to the alignment constructed by <strong>malign3d</strong>. It does not make an
alignment, but it calculates the RMS and DRMS deviations between atomic
positions and distances, differences between the mainchain and sidechain
dihedral angles, percentage sequence identities, and several other measures.
Finally, the <strong>id_table</strong> command writes a file with pairwise
sequence distances that can be used directly as the input to the
<strong>dendrogram</strong> command (or the clustering programs in the
<span class="progs">PHYLIP</span> package). <strong>dendrogram</strong>
calculates a clustering tree from the input matrix of pairwise distances,
which helps visualizing differences among the template candidates. Excerpts
from the log file are shown below (file
"<span class="filename">compare.log</span>").</p>

(循环结束时，所有结构均已加入比对，但它们之间的对齐并非最优（append_model生成的简单1:1比对不含空位）。因此，我们使用malign进行多序列比对优化，再通过malign3d命令基于该多序列比对结果，对这六个三维结构进行迭代最小二乘叠加。compare_structures命令根据malign3d构建的比对来比较结构差异——它不生成新比对，而是计算原子位置的RMS和DRMS偏差、主链与侧链二面角差异、序列同一性百分比等指标。最后，id_table命令输出包含成对序列距离的文件，该文件可直接作为dendrogram命令（或PHYLIP软件包中的聚类程序）的输入。dendrogram根据成对距离矩阵计算聚类树，帮助可视化候选模板间的差异。部分日志文件内容如下所示（文件"compare.log"）。)

<pre class="filecontent">Sequence identity comparison (ID_TABLE):

   Diagonal       ... number of residues;
   Upper triangle ... number of identical residues;
   Lower triangle ... % sequence identity, id/min(length).

         1b8pA @11bdmA @11civA @25mdhA @27mdhA @21smkA @2
1b8pA @1      327     194     147     151     153      49
1bdmA @1       61     318     152     167     155      56
1civA @2       45      48     374     139     304      53
5mdhA @2       46      53      42     333     139      57
7mdhA @2       47      49      87      42     351      48
1smkA @2       16      18      17      18      15     313


Weighted pair-group average clustering based on a distance matrix:


                                           .----------------------- 1b8pA @1.9    39.0000
                                           |
                                  .-------------------------------- 1bdmA @1.8    50.5000
                                  |
                              .------------------------------------ 5mdhA @2.4    55.3750
                              |
                              |                                .--- 1civA @2.8    13.0000
                              |                                |
        .---------------------------------------------------------- 7mdhA @2.4    83.2500
        |
      .------------------------------------------------------------ 1smkA @2.5

      +----+----+----+----+----+----+----+----+----+----+----+----+
    86.0600   73.4150   60.7700   48.1250   35.4800   22.8350   10.1900
         79.7375   67.0925   54.4475   41.8025   29.1575   16.5125
                                                                                                            </pre>

<p class="smallfilename">Excerpts of the file compare.log</p>

<p>The comparison above shows that <span class="pdb">1civ:A</span> and
<span class="pdb">7mdh:A</span> are almost identical, both sequentially and
structurally. However, <span class="pdb">7mdh:A</span> has a better
crystallographic resolution (2.4Å versus 2.8Å), eliminating
<span class="pdb">1civ:A</span>. A second group of structures
(<span class="pdb">5mdh:A</span>, <span class="pdb">1bdm:A</span>, and 
<span class="pdb">1b8p:A</span>) share some similarities. From this group, 
<span class="pdb">5mdh:A</span> has the poorest resolution leaving for 
consideration only <span class="pdb">1bdm:A</span> and
<span class="pdb">1b8p:A</span>. <span class="pdb">1smk:A</span> is the most
diverse structure of the whole set of possible templates. However, it is the
one with the lowest sequence identity (34%) to the query sequence. We finally
pick <span class="pdb">1bdm:A</span> over <span class="pdb">1b8p:A</span> and
<span class="pdb">7mdh:A</span> because of its better crystallographic R-factor
(16.9%) and higher overall sequence identity to the query sequence (45%).
         
(上述比较表明，1civ:A 和 7mdh:A 在序列和结构上几乎完全一致。但 7mdh:A 的晶体分辨率更高（2.4Å vs 2.8Å），因此排除 1civ:A。第二组结构（5mdh:A、1bdm:A 和 1b8p:A）具有部分相似性，其中 5mdh:A 分辨率最差，仅剩 1bdm:A 和 1b8p:A 可供选择。1smk:A 是所有候选模板中差异最大的结构，但其与查询序列的序列同一性最低（34%）。最终我们选择 1bdm:A，因其晶体学R因子更优（16.9%），且与查询序列的整体同一性更高（45%）。)

</p><h3>3. Aligning TvLDF with the template</h3>
<p>A good way of aligning the sequence of TvLDH with the structure of
<span class="pdb">1bdm:A</span> is the <strong>align2d()</strong> command in
<span class="progs">MODELLER</span>. Although <strong>align2d()</strong> is
based on a dynamic programming algorithm, it is different from standard
sequence-sequence alignment methods because it takes into account structural
information from the template when constructing an alignment. This task is
achieved through a variable gap penalty function that tends to place gaps in
solvent exposed and curved regions, outside secondary structure segments, and
between two positions that are close in space. As a result, the alignment
errors are reduced by approximately one third relative to those that occur
with standard sequence alignment techniques. This improvement becomes more
important as the similarity between the sequences decreases and the number
of gaps increases. In the current example, the template-target similarity
is so high that almost any alignment method with reasonable parameters will
result in the same alignment. The following <span class="progs">MODELLER</span>
script aligns the TvLDH sequence in file
"<span class="filename">TvLDH.ali</span>" with the
<span class="pdb">1bdm:A</span> structure in the PDB file
"<span class="filename">1bdm.pdb</span>" (file
"<span class="filename">align2d.py</span>").</p>

(使用MODELLER中的align2d()命令是将TvLDH序列与1bdm:A结构进行比对的有效方法。尽管align2d()基于动态规划算法，但它不同于标准的序列-序列比对方法，其在构建比对时会整合模板的结构信息。该功能通过可变空位罚分函数实现：倾向于将空位放置在溶剂暴露区/弯曲区域、二级结构片段之外，以及空间距离较近的两个位点之间。相较于标准序列比对技术，该方法能将比对错误减少约三分之一。当序列相似性较低且空位较多时，这一改进尤为重要。本案例中，由于模板与目标序列相似性极高，几乎任何参数合理的比对方法都能得到相同结果。以下MODELLER脚本将"TvLDH.ali"文件中的TvLDH序列与PDB文件"1bdm.pdb"中的1bdm:A结构进行比对（脚本文件"align2d.py"）)

<pre class="filecontent">from modeller import *

env = Environ()
aln = Alignment(env)
mdl = Model(env, file='1bdm', model_segment=('FIRST:A','LAST:A'))
aln.append_model(mdl, align_codes='1bdmA', atom_files='1bdm.pdb')
aln.append(file='TvLDH.ali', align_codes='TvLDH')
aln.align2d(max_gap_length=50)
aln.write(file='TvLDH-1bdmA.ali', alignment_format='PIR')
aln.write(file='TvLDH-1bdmA.pap', alignment_format='PAP')
</pre>
<p class="smallfilename">File: align2d.py</p>

<p>In this script, we again create an 'Environ' object to use as input to
later commands. We create an empty alignment 'aln',
and then a new protein model 'mdl', into which we read the 
chain A segment of the <span class="pdb">1bdm</span> PDB structure file. The
<strong>append_model()</strong> command transfers the PDB sequence of this
model to the alignment and assigns it the name of "<em>1bdmA</em>"
(<strong>align_codes</strong>). Then we add the "<em>TvLDH</em>" sequence from
file "<span class="filename">TvLDH.seq</span>" to the alignment, using the
<strong>append()</strong> command. The <strong>align2d()</strong> command is then
executed to align the two sequences. Finally, the alignment is written out in two 
formats, PIR ("<span class="filename">TvLDH-1bdmA.ali</span>") and PAP
("<span class="filename">TvLDH-1bdmA.pap</span>"). The PIR format is used by
<span class="progs">MODELLER</span> in the subsequent model building stage,
while the PAP alignment format is easier to inspect visually. Due to the high
target-template similarity, there are only a few gaps in the alignment. In the
PAP format, all identical positions are marked with a "*" (file
"<span class="filename">TvLDH-1bdmA.pap</span>").</p>

(在此脚本中，我们再次创建了一个"Environ"对象作为后续命令的输入环境。初始化一个空比对对象"aln"后，新建蛋白质模型"mdl"并读入1bdm PDB结构文件的A链片段。通过append_model()命令将该模型的PDB序列转移至比对对象，并命名为"1bdmA"（align_codes参数）。接着使用append()命令将"TvLDH.seq"文件中的TvLDH序列加入比对。执行align2d()命令对两条序列进行比对，最终以两种格式输出比对结果：PIR格式（"TvLDH-1bdmA.ali"）和PAP格式（"TvLDH-1bdmA.pap"）。PIR格式将用于后续建模阶段，而PAP格式更便于人工检查。由于目标序列与模板高度相似，比对结果中仅存在少量空位。在PAP格式中，所有完全匹配的位点均用"*"标记（见文件"TvLDH-1bdmA.pap"）。)


<pre class="filecontent"> _aln.pos         10        20        30        40        50        60
1bdmA     MKAPVRVAVTGAAGQIGYSLLFRIAAGEMLGKDQPVILQLLEIPQAMKALEGVVMELEDCAFPLLAGL 
TvLDH     MSEAAHVLITGAAGQIGYILSHWIASGELYG-DRQVYLHLLDIPPAMNRLTALTMELEDCAFPHLAGF 
 _consrvd *     *  ********* *   ** **  * *  * * ** ** **  *    ********* ***

 _aln.p   70        80        90       100       110       120       130
1bdmA     EATDDPDVAFKDADYALLVGAAPRL---------QVNGKIFTEQGRALAEVAKKDVKVLVVGNPANTN 
TvLDH     VATTDPKAAFKDIDCAFLVASMPLKPGQVRADLISSNSVIFKNTGEYLSKWAKPSVKVLVIGNPDNTN 
 _consrvd  ** **  **** * * **   *             *  **   *  *   **  ***** *** ***

 _aln.pos  140       150       160       170       180       190       200
1bdmA     ALIAYKNAPGLNPRNFTAMTRLDHNRAKAQLAKKTGTGVDRIRRMTVWGNHSSIMFPDLFHAEVD--- 
TvLDH     CEIAMLHAKNLKPENFSSLSMLDQNRAYYEVASKLGVDVKDVHDIIVWGNHGESMVADLTQATFTKEG 
 _consrvd   **   *  * * **     ** ***    * * *  *       *****   *  **  *

 _aln.pos    210       220       230       240       250       260       270
1bdmA     -GRPALELVDMEWYEKVFIPTVAQRGAAIIQARGASSAASAANAAIEHIRDWALGTPEGDWVSMAVPS 
TvLDH     KTQKVVDVLDHDYVFDTFFKKIGHRAWDILEHRGFTSAASPTKAAIQHMKAWLFGTAPGEVLSMGIPV 
 _consrvd          *       *      *   *   **  ****   *** *   *  **  *   **  *

 _aln.pos      280       290       300       310       320       330
1bdmA     Q--GEYGIPEGIVYSFPVTAK-DGAYRVVEGLEINEFARKRMEITAQELLDEMEQVKAL--GLI 
TvLDH     PEGNPYGIKPGVVFSFPCNVDKEGKIHVVEGFKVNDWLREKLDFTEKDLFHEKEIALNHLAQGG 
 _consrvd      ***  * * ***      *   ****   *   *     *   *  * *
</pre>
<p class="smallfilename">File: TvLDH-1bdmA.pap</p>

<h3>4. Model building</h3>

<p>Once a target-template alignment is constructed,
<span class="progs">MODELLER</span> calculates a 3D model of the target
completely automatically, using its <strong>AutoModel</strong> class. The
following script will generate five similar models of TvLDH based on the
<span class="pdb">1bdm:A</span> template structure and the alignment in file
"<span class="filename">TvLDH-1bdmA.ali</span>" (file
"<span class="filename">model-single.py</span>").</p>
(在完成目标-模板比对构建后，MODELLER会使用其AutoModel类全自动计算目标蛋白的三维模型。以下脚本将基于1bdm:A模板结构和"TvLDH-1bdmA.ali"文件中的比对信息，生成五个相似的TvLDH模型（脚本文件"model-single.py"）)
<pre class="filecontent">from modeller import *
from modeller.automodel import *
#from modeller import soap_protein_od

env = Environ()
a = AutoModel(env, alnfile='TvLDH-1bdmA.ali',
              knowns='1bdmA', sequence='TvLDH',
              assess_methods=(assess.DOPE,
                              #soap_protein_od.Scorer(),
                              assess.GA341))
a.starting_model = 1
a.ending_model = 5
a.make()
</pre>
<p class="smallfilename">File: model-single.py</p>

<p>The first line loads in the <strong>AutoModel</strong> class and prepares
it for use. We then create an <strong>AutoModel</strong> object, call it 'a',
and set parameters to guide the model building procedure.
<strong>alnfile</strong> names the file that contains the target-template
alignment in the PIR format. <strong>knowns</strong> defines the known template
structure(s) in <strong>alnfile</strong>
("<span class="filename">TvLDH-1bdmA.ali</span>"). <strong>sequence</strong>
defines the name of the target sequence in <strong>alnfile</strong>.
<strong>assess_methods</strong> requests one or more assessment scores
(discussed in more detail in the next section).
<strong>starting_model</strong> and <strong>ending_model</strong> define the
number of models that are calculated (their indices will run from 1 to 5).
The last line in the file calls the <strong>make</strong> method that
actually calculates the models.</p>

(首行代码导入AutoModel类并准备使用。接着我们创建一个名为'a'的AutoModel对象，并通过参数设置指导建模流程：alnfile指定包含PIR格式目标-模板比对的文件名；knowns定义比对文件（"TvLDH-1bdmA.ali"）中的已知模板结构；sequence指定比对文件里的目标序列名称；assess_methods请求一个或多个评估分数（下节将详细讨论）；starting_model和ending_model定义待计算模型的数量（编号从1到5）。文件最后一行调用make方法执行实际建模计算。)

<p>The most important output file is
"<span class="filename">model-single.log</span>", which reports warnings,
errors and other useful information including the input restraints used for
modeling that remain violated in the final model. The last few lines from this
log file are shown below.</p>

(最重要的输出文件是"model-single.log"，该文件记录了警告、错误及其他关键信息，包括建模过程中使用的输入约束条件以及在最终模型中仍存在的违例情况。下文展示了该日志文件的最后几行内容。)

<pre class="filecontent">&gt;&gt; Summary of successfully produced models:
Filename                          molpdf     DOPE score    GA341 score
----------------------------------------------------------------------
TvLDH.B99990001.pdb           1763.56104   -38079.76172        1.00000
TvLDH.B99990002.pdb           1560.93396   -38515.98047        1.00000
TvLDH.B99990003.pdb           1712.44104   -37984.30859        1.00000
TvLDH.B99990004.pdb           1720.70801   -37869.91406        1.00000
TvLDH.B99990005.pdb           1840.91772   -38052.00781        1.00000
</pre>

<p class="smallfilename">Excerpts of the file model-single.log</p>

<p>As you can see, the log file gives a summary of all the models built.
For each model, it lists the file name, which contains the coordinates of the
model in PDB format. The models can be viewed by any program that reads the
PDB format, such as Chimera. The log also shows the score(s) of each model,
which are further discussed below. (Note that the actual numbers may be
slightly different on your machine - this is nothing to worry about.)</p>

(如您所见，日志文件汇总了所有构建的模型信息：每个模型均列出其PDB格式坐标文件的文件名（可通过Chimera等支持PDB格式的程序查看），同时显示各模型的评分分数（具体评分标准将在下文讨论）。（注意：您计算机上的实际数值可能略有差异，这属于正常现象。）)

<h3>5. Model evaluation</h3>

<p>If several models are calculated for the same target, the "best" model
can be selected in several ways. For example, you could pick the model with
the lowest value of the <span class="progs">MODELLER</span> objective function
or the <a href="https://salilab.org/modeller/10.0/manual/node261.html">DOPE</a>
or <a href="https://salilab.org/modeller/10.0/manual/node285.html">SOAP</a>
assessment scores, or with the highest
<a href="https://salilab.org/modeller/10.0/manual/node205.html">GA341</a>
assessment score, which are reported at the end of the log file, above.
(The objective function, molpdf,
is always calculated, and is also reported in a REMARK in each generated PDB
file. The DOPE, SOAP, and GA341 scores, or any other assessment scores, are
only calculated if you list them in <strong>assess_methods</strong>. To
calculate the SOAP score, you will first need to download the SOAP-Protein
potential file from <a href="https://salilab.org/SOAP/">the SOAP website</a>,
then uncomment the SOAP-related lines in <tt>model-single.py</tt> by removing
the '<tt>#</tt>' characters.)
The molpdf, DOPE, and SOAP scores are not 'absolute' measures, in the
sense that they
can only be used to rank models calculated from the same alignment. Other
scores are transferable. For example GA341 scores always range from 0.0
(worst) to 1.0 (native-like); however GA341 is not as good as DOPE or SOAP at
distinguishing 'good' models from 'bad' models.</p>

<p>Once a final model is selected, it can be further assessed in many ways.
Links to programs for model assessment can be found in
the <em>MODEL EVALUATION</em> section on
<a href="https://salilab.org/bioinformatics_resources.shtml">this page</a>.</p>

<p>Before any external evaluation of the
model, one should check the log file from the modeling run for runtime errors
("<span class="filename">model-single.log</span>") and restraint violations
(see the <span class="progs">MODELLER</span>
<a href="https://salilab.org/modeller/manual/">manual</a> for details). The file
"<span class="filename">evaluate_model.py</span>" evaluates an input model
with the DOPE potential. (Note that here we arbitrarily picked the second
generated model - you may want to try other models.)</p>

(若针对同一目标蛋白构建了多个模型，可通过以下方式选择"最佳"模型：
    (1)选择MODELLER目标函数（molpdf）、DOPE或SOAP评估分数最低的模型
    
    (2)选择GA341评估分数最高的模型
    
    (3)（这些分数均记录在日志文件末尾。其中molpdf是默认计算的，也会写入每个PDB文件的REMARK字段；而DOPE、SOAP和GA341分数需通过assess_methods参数指定才会计算。如需计算SOAP分数，需先从SOAP官网下载SOAP-Protein势能文件，并移除"model-single.py"中SOAP相关代码行的注释符号#。）

需注意：
    (1)非绝对性指标：molpdf、DOPE和SOAP分数仅适用于同一比对生成的模型间比较
    
    (2)可迁移指标：GA341分数始终在0.0（最差）到1.0（类天然）之间，但其区分"好/坏"模型的能力不如DOPE或SOAP
    
    选定最终模型后，可通过更多方式验证质量（本页"模型评估"章节提供相关工具链接）。)
    
<pre class="filecontent">from modeller import *
from modeller.scripts import complete_pdb

log.verbose()    # request verbose output
env = Environ()
env.libs.topology.read(file='$(LIB)/top_heav.lib') # read topology
env.libs.parameters.read(file='$(LIB)/par.lib') # read parameters

# read model file
mdl = complete_pdb(env, 'TvLDH.B99990002.pdb')

# Assess with DOPE:
s = Selection(mdl)   # all atom selection
s.assess_dope(output='ENERGY_PROFILE NO_REPORT', file='TvLDH.profile',
              normalize_profile=True, smoothing_window=15)
</pre>
<p class="smallfilename">File: evaluate_model.py</p>

<p>In this script we use the <strong>complete_pdb</strong> script to read in
a PDB file and prepare it for energy calculations (this automatically
allows for the possibility that the PDB file has
atoms in a non-standard order, or has different subsets of atoms, such as
all atoms including hydrogens, while <span class="progs">MODELLER</span>
uses only heavy atoms, or vice versa). We then create a selection of all atoms,
since most <span class="progs">MODELLER</span> energy functions can operate on
a subset of model atoms. The DOPE energy is then calculated
with the <strong>assess_dope</strong> command, and we additionally request an
energy profile, smoothed over a 15 residue window, and normalized by the
number of restraints acting on each residue. This profile is written to
a file "<span class="filename">TvLDH.profile</span>", which can be used as
input to a graphing program. For example, it could be plotted with
<span class="progs">GNUPLOT</span> using the command
'<tt>plot "TvLDH.profile" using 1:42 with lines</tt>'. Alternatively, you
can use the <span class="filename">plot_profiles.py</span> script included
in the tutorial zip file to plot profiles with the Python matplotlib
package.</p>

(在此脚本中，我们使用complete_pdb脚本读取PDB文件并准备能量计算（该功能可自动处理PDB文件中原子的非标准排序或不同原子子集的情况，例如包含氢原子的全原子文件与MODELLER仅使用的重原子文件之间的兼容性问题）。随后创建所有原子的选择集（因大多数MODELLER能量函数可针对模型原子的子集运算），通过assess_dope命令计算DOPE能量。我们还额外请求生成经过15个残基窗口平滑处理、并按各残基所受约束数归一化的能量分布曲线。该曲线将写入"TvLDH.profile"文件，可作为绘图程序的输入。例如，使用GNUPLOT命令plot "TvLDH.profile" using 1:42 with lines即可绘制曲线，或直接使用教程压缩包中的plot_profiles.py脚本通过Python的matplotlib包进行绘图)

<p>The GA341 score, as well as external analysis with the
<span class="progs">PROCHECK</span> program, confirms that
<span class="filename">TvLDH.B99990001.pdb</span> is a
reasonable model. However, the plotted DOPE score profile (below) shows regions
of relatively high energy for the long active site loop between residues 90 and
100 and the long helices at the C-terminal end of the target sequence. (Note
that we have superposed the model profile on the template profile - gaps in the
plot can be seen corresponding to the gaps in the alignment. Remember that
the scores are not absolute, so we cannot make a direct numerical comparison
between the two. However, we can get an idea of the quality of our input
alignment this way by comparing the rough shapes of the two profiles - if one
is obviously shifted relative to the other, it is likely that the alignment
is also shifted from the correct one.)</p>

(GA341评分以及PROCHECK程序的外部分析均证实，TvLDH.B99990001.pdb是一个合理的模型。然而，绘制的DOPE能量分布图（下图）显示，在90-100号残基之间的长活性位点环区以及目标序列C端的长螺旋区域存在相对较高的能量值。（注：我们已将模型的能量曲线与模板的曲线叠加显示——图中空白处对应比对中的空位区域。需谨记这些评分并非绝对值，因此无法直接进行数值比较。但通过对比两条曲线的整体形状，可以评估输入比对的质量：若两条曲线明显偏移，则可能表明当前比对存在系统性错位。）)

<p class="centerimg">
<img class="centerimg" src="Tutorial_files/dope_profile.png" alt="DOPE score profile">
</p>

<p class="smallfilename">DOPE score profiles for the model and templates</p>

<p>This long loop interacts with region 220-250, which forms the other half of 
the active site. This latter part is well resolved in the template and probably
correctly modeled in the target structure, but due to the unfavorable
non-bonded interactions with the 90-100 region, it is also reported to be
of high "energy" by DOPE. In general, a possible error indicated by DOPE may 
not necessarily be an actual error, especially if it highlights an active site 
or a protein-protein interface. However, in this case, the same active site
loops have a better profile in the template structure, which strengthens the
assessment that the model is probably incorrect in the active site region.
This problem is addressed in the <a href="https://salilab.org/modeller/tutorial/advanced.html">advanced modeling
tutorial</a>.</p>

(该长环区（90-100）与220-250区域（活性位点的另一组成部分）存在相互作用。虽然220-250区域在模板结构中解析良好，且在目标模型中的构建可能正确，但由于其与90-100区存在不利的非键相互作用，DOPE同样报告该区域具有高"能量"。通常而言，DOPE提示的潜在误差未必是真实错误——尤其是当高能区位于活性位点或蛋白质相互作用界面时。但本案例中，模板结构的相同活性位点环区显示出更优的能量分布，这强化了"模型在活性位点区域可能存在错误"的判断。该问题的解决方案将在进阶建模教程中探讨。)

</div></div>

<div class="copyright">
<p><a class="ucsflogo" href="https://www.ucsf.edu/"><img src="Tutorial_files/ucsf-logo.png" alt="UCSF Logo"></a>
MODELLER (copyright © 1989-2025 Andrej Sali) is
maintained by <a href="https://salilab.org/modeller/contact.html">Ben Webb</a>
at the Departments of Biopharmaceutical Sciences and Pharmaceutical Chemistry,
and California Institute for Quantitative Biomedical Research, Mission Bay
Byers Hall, University of California San Francisco, San Francisco,
CA 94143, USA.
Any selling or distribution of the program or its parts, original or modified,
is prohibited without a written permission from Andrej Sali.
This file last modified: Wed Feb 10 10:36:26 PST 2021.</p>
</div>
(MODELLER（版权 © 1989-2025 Andrej Sali）由Ben Webb维护，其所属机构为加州大学旧金山分校（University of California San Francisco）生物制药科学系、药理化学系及定量生物医学研究加州研究所（California Institute for Quantitative Biomedical Research），地址：Mission Bay Byers Hall，旧金山，加利福尼亚州94143，美国。未经安德烈·萨利书面许可，禁止出售或分发该程序或其任何部分（包括原始版本或修改版本）。本文件最后修改时间：2021年2月10日 10:36:26 PST)

</body></html>
