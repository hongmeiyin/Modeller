<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<!--Converted with LaTeX2HTML 2018.2 (Released May 16, 2018) -->
<html><head>
<title>Preparing input files</title>
<meta name="description" content="Preparing input files">
<meta name="keywords" content="manual">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">

<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<meta name="Generator" content="LaTeX2HTML v2018.2">
<meta http-equiv="Content-Style-Type" content="text/css">

<link rel="STYLESHEET" href="Preparing%20input%20files_files/manual.css">
<link rel="STYLESHEET" href="Preparing%20input%20files_files/pygments.css">

<link rel="next" href="https://salilab.org/modeller/manual/node14.html">
<link rel="previous" href="https://salilab.org/modeller/manual/node12.html">
<link rel="up" href="https://salilab.org/modeller/manual/node12.html">
<link rel="next" href="https://salilab.org/modeller/manual/node14.html">
</head>

<body>

<div class="navigation"><!--Navigation Panel-->
<a name="tex2html1578" href="https://salilab.org/modeller/manual/node14.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Preparing%20input%20files_files/next.png"></a> 
<a name="tex2html1572" href="https://salilab.org/modeller/manual/node12.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Preparing%20input%20files_files/up.png"></a> 
<a name="tex2html1566" href="https://salilab.org/modeller/manual/node12.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Preparing%20input%20files_files/prev.png"></a> 
<a name="tex2html1574" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Preparing%20input%20files_files/contents.png"></a> 
<a name="tex2html1576" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Preparing%20input%20files_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html1579" href="https://salilab.org/modeller/manual/node14.html">Running MODELLER</a>
<b> Up:</b> <a name="tex2html1573" href="https://salilab.org/modeller/manual/node12.html">Using MODELLER for comparative</a>
<b> Previous:</b> <a name="tex2html1567" href="https://salilab.org/modeller/manual/node12.html">Using MODELLER for comparative</a>
 &nbsp; <b>  <a name="tex2html1575" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html1577" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> 
<br>
<br></div>
<!--End of Navigation Panel-->
<!--Table of Child-Links-->
<a name="CHILD_LINKS"><strong>Subsections</strong></a>

<ul class="ChildLinks">
<li><a name="tex2html1580" href="https://salilab.org/modeller/manual/node13.html#SECTION00661100000000000000">Atom files</a>
</li><li><a name="tex2html1581" href="https://salilab.org/modeller/manual/node13.html#SECTION00661200000000000000">Alignment file</a>
</li><li><a name="tex2html1582" href="https://salilab.org/modeller/manual/node13.html#SECTION00661300000000000000">Script file</a>
</li></ul>
<!--End of Table of Child-Links-->
<hr>

<h2><a name="SECTION00661000000000000000">
Preparing input files</a>
</h2>

<p>
The sample input files in this tutorial can be found in the 
<tt>examples/automodel</tt> directory of the M<small>ODELLER</small> distribution. 

</p><p>
There are three kinds of input files: Protein Data Bank
atom files with coordinates for the template structures, the alignment
file with the alignment of the template structures with the
target sequence, and M<small>ODELLER</small> commands in a script file that instruct
M<small>ODELLER</small> what to do.

</p><p>

</p><h3><a name="SECTION00661100000000000000">
Atom files</a>
</h3>

<p>
Each atom file is named <tt>code.atm</tt> where <tt>code</tt> is a short protein
code, preferably the PDB code; for example, <i>Peptococcus aerogenes</i> 
ferredoxin would be in a file <tt>1fdx.atm</tt>. If you wish, you can also use 
file extensions <tt>.pdb</tt> and <tt>.ent</tt> instead of <tt>.atm</tt>. The code must 
be used as that protein's identifier throughout the modeling.

</p><p>

</p><h3><a name="SECTION00661200000000000000"></a><a name="2641"></a>
<br>
Alignment file
</h3>

<p>
One of the formats for the alignment file is related to the PIR database
format; this is the preferred format for comparative modeling:

</p><p>

</p><p>
<br>
</p><pre class="verbatim">C; A sample alignment in the PIR format; used in tutorial

&gt;P1;5fd1
structureX:5fd1:1    :A:106  :A:ferredoxin:Azotobacter vinelandii: 1.90: 0.19
AFVVTDNCIKCKYTDCVEVCPVDCFYEGPNFLVIHPDECIDCALCEPECPAQAIFSEDEVPEDMQEFIQLNAELA
EVWPNITEKKDPLPDAEDWDGVKGKLQHLER*

&gt;P1;1fdx
sequence:1fdx:1    :A:54   :A:ferredoxin:Peptococcus aerogenes: 2.00:-1.00
AYVINDSC--IACGACKPECPVNIIQGS--IYAIDADSCIDCGSCASVCPVGAPNPED-----------------
-------------------------------*
</pre>
<p>
See Section&nbsp;<a href="https://salilab.org/modeller/manual/node502.html#alignmentformat">B.1</a> for a detailed description of the
alignment file format. Influence of the alignment on the 
quality of the model cannot be overemphasized. (对齐方式对模型质量的影响不容忽视)
To obtain the best possible model, it is important to
understand how the alignment is used by M<small>ODELLER</small>[<a href="https://salilab.org/modeller/manual/node517.html#SalBlu93">Šali &amp; Blundell, 1993</a>]. In outline(概要), for
the aligned regions, M<small>ODELLER</small> tries to derive a 3D model for the target
sequence (that is as close to one or the other of the template structures) as
possible while also satisfying stereochemical restraints (<em>e.g.</em>, bond
lengths, angles, non-bonded atom contacts, ...); the inserted
regions, which do not have any equivalent segments in any of the
templates, are modeled in the context of the whole molecule, but using
their sequence alone.<font color=red>("插入区域（在任何模板中都没有对应片段的部分）是在整个分子的背景下进行建模的，但仅使用其自身序列。") </font>This way of deriving a model means that whenever
a user aligns a target residue with a template residue, he tells
M<small>ODELLER</small> to treat the aligned residues as <b>structurally</b>
equivalent. Command <b><a href="https://salilab.org/modeller/manual/node301.html#CMD:Alignment.check">Alignment.check()</a></b><a name="2722"></a> can be used to find some 
trivial alignment mistakes.(这种建模方式意味着，每当用户将目标序列的残基与模板残基对齐时，他实际上是在告诉MODELLER将这些对齐的残基视为结构等效。用户可以使用Alignment.check()命令来检测一些明显的对齐错误。)

</p><p>

</p><h3><a name="SECTION00661300000000000000"></a><a name="2649"></a><a name="2650"></a>
<br>
Script file
</h3>

<p>
M<small>ODELLER</small> is a command-line only tool, and has no graphical user interface;
instead, you must provide it with a script file containing M<small>ODELLER</small> commands.
This is an ordinary <a name="tex2html20" href="https://www.python.org/">Python</a> script.

</p><p>
If you are not familiar with <a name="tex2html21" href="https://www.python.org/">Python</a>, you can simply adapt one of the many
examples in the <tt>examples</tt> directory, or look at the code for the classes
used by M<small>ODELLER</small> itself, in the <tt>modlib/modeller</tt> directory. Finally,
there are many resources for learning <a name="tex2html22" href="https://www.python.org/">Python</a> itself, such as a comprehensive
tutorial at <a name="tex2html23" href="https://docs.python.org/3/tutorial/index.html">https://docs.python.org/3/tutorial/index.html</a>.

</p><p>
A sample script file <tt>model-default.py</tt> to produce one model of sequence
<tt>1fdx</tt> from the known structure of <tt>5fd1</tt> and from the alignment
between the two sequences is

</p><p>
<br>
</p><pre class="verbatim"># Comparative modeling by the AutoModel class
from modeller import *              # Load standard Modeller classes
from modeller.automodel import *    # Load the AutoModel class

log.verbose()    # request verbose output
env = Environ()  # create a new MODELLER environment to build this model in

# directories for input atom files
env.io.atom_files_directory = ['.', '../atom_files']

a = AutoModel(env,
              alnfile  = 'alignment.ali',     # alignment filename
              knowns   = '5fd1',              # codes of the templates
              sequence = '1fdx')              # code of the target
a.starting_model= 1                 # index of the first model
a.ending_model  = 1                 # index of the last model
                                    # (determines how many models to calculate)
a.make()                            # do the actual comparative modeling
</pre>

<p>
See Chapter&nbsp;<a href="https://salilab.org/modeller/manual/node15.html#CHAPTERAUTOMODEL">2</a> for more information about the
<tt>AutoModel</tt> class, and a more detailed explanation of what this
script does.

</p><p>

</p><div class="navigation"><hr>
<!--Navigation Panel-->
<a name="tex2html1578" href="https://salilab.org/modeller/manual/node14.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Preparing%20input%20files_files/next.png"></a> 
<a name="tex2html1572" href="https://salilab.org/modeller/manual/node12.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Preparing%20input%20files_files/up.png"></a> 
<a name="tex2html1566" href="https://salilab.org/modeller/manual/node12.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Preparing%20input%20files_files/prev.png"></a> 
<a name="tex2html1574" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Preparing%20input%20files_files/contents.png"></a> 
<a name="tex2html1576" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Preparing%20input%20files_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html1579" href="https://salilab.org/modeller/manual/node14.html">Running MODELLER</a>
<b> Up:</b> <a name="tex2html1573" href="https://salilab.org/modeller/manual/node12.html">Using MODELLER for comparative</a>
<b> Previous:</b> <a name="tex2html1567" href="https://salilab.org/modeller/manual/node12.html">Using MODELLER for comparative</a>
 &nbsp; <b>  <a name="tex2html1575" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html1577" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> </div>
<!--End of Navigation Panel-->



</body></html>