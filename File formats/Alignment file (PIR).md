<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
<!--Converted with LaTeX2HTML 2008 (1.71)
original version by:  Nikos Drakos, CBLU, University of Leeds
* revised and updated by:  Marcus Hennecke, Ross Moore, Herb Swan
* with significant contributions from:
  Jens Lippmann, Marek Rouchal, Martin Wilck and others -->
<html><head>
<meta http-equiv="content-type" content="text/html; charset=UTF-8">
<title>Alignment file (PIR)</title>
<meta name="description" content="Alignment file (PIR)">
<meta name="keywords" content="manual">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">

<meta name="Generator" content="LaTeX2HTML v2008">
<meta http-equiv="Content-Style-Type" content="text/css">

<link rel="STYLESHEET" href="Alignment%20file%20(PIR)_files/manual.css">

<link rel="next" href="https://salilab.org/modeller/9v8/manual/node455.html">
<link rel="previous" href="https://salilab.org/modeller/9v8/manual/node453.html">
<link rel="up" href="https://salilab.org/modeller/9v8/manual/node453.html">
<link rel="next" href="https://salilab.org/modeller/9v8/manual/node455.html">
</head>

<body>
<!--Navigation Panel-->
<a name="tex2html8466" href="https://salilab.org/modeller/9v8/manual/node455.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Alignment%20file%20(PIR)_files/next.png"></a> 
<a name="tex2html8460" href="https://salilab.org/modeller/9v8/manual/node453.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Alignment%20file%20(PIR)_files/up.png"></a> 
<a name="tex2html8454" href="https://salilab.org/modeller/9v8/manual/node453.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Alignment%20file%20(PIR)_files/prev.png"></a> 
<a name="tex2html8462" href="https://salilab.org/modeller/9v8/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Alignment%20file%20(PIR)_files/contents.png"></a> 
<a name="tex2html8464" href="https://salilab.org/modeller/9v8/manual/node470.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Alignment%20file%20(PIR)_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html8467" href="https://salilab.org/modeller/9v8/manual/node455.html">Restraints file</a>
<b> Up:</b> <a name="tex2html8461" href="https://salilab.org/modeller/9v8/manual/node453.html">File formats</a>
<b> Previous:</b> <a name="tex2html8455" href="https://salilab.org/modeller/9v8/manual/node453.html">File formats</a>
 &nbsp; <b>  <a name="tex2html8463" href="https://salilab.org/modeller/9v8/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html8465" href="https://salilab.org/modeller/9v8/manual/node470.html">Index</a></b> 
<br>
<br>
<!--End of Navigation Panel-->

<h1><a name="SECTION001410000000000000000">
Alignment file (PIR)</a>
</h1>

<p>
<a name="alignmentformat"></a><a name="41680"></a>
<a name="41681"></a>
The preferred format for comparative modeling is related to the PIR database
format:

</p><p>
<br>
</p><pre>C; A sample alignment in the PIR format; used in tutorial

&gt;P1;5fd1
structureX:5fd1:1    :A:106  :A:ferredoxin:Azotobacter vinelandii: 1.90: 0.19
AFVVTDNCIKCKYTDCVEVCPVDCFYEGPNFLVIHPDECIDCALCEPECPAQAIFSEDEVPEDMQEFIQLNAELA
EVWPNITEKKDPLPDAEDWDGVKGKLQHLER*

&gt;P1;1fdx
sequence:1fdx:1    : :54   : :ferredoxin:Peptococcus aerogenes: 2.00:-1.00
AYVINDSC--IACGACKPECPVNIIQGS--IYAIDADSCIDCGSCASVCPVGAPNPED-----------------
-------------------------------*
</pre>
<p>
The first line of each sequence entry(序列条目) specifies the protein code after the 
<tt>&gt;P1;</tt> line identifier. The line identifier must occur at the beginning of the
line. For example, <tt>1fdx</tt> is the protein code of the first entry
in the alignment above. The protein code corresponds to the
<i><a href="https://salilab.org/modeller/9v8/manual/node300.html#MEMB:Sequence.code">Sequence.code</a></i><a name="41891"></a> variable. (Conventionally, this code is the PDB code
followed by an optional one-letter chain ID, but this is not required.)

</p><p>
The second line of each entry contains information necessary to extract
atomic coordinates of the segment from the original PDB coordinate set. The 
fields in this line are separated by colon characters(冒号字符), `:'. The fields are 
as follows: 

</p><p>
</p><dl compact="compact">
<dt>Field 1:</dt>
<dd>A specification of whether or not 3D structure is 
available and of the type of the method used to obtain the 
structure (<tt>structureX</tt>, X-ray; <tt>structureN</tt>, NMR; <tt>structureM</tt>,
model; <tt>sequence</tt>, sequence). Only <tt>structure</tt> is also a valid
value.(是否提供3D结构以及获取结构所采用的方法类型（结构X，X射线；结构N，核磁共振；结构M，模型；序列，序列）。仅结构也是一个有效的值。)

<p>
</p></dd>
<dt>Field 2:</dt>
<dd>The PDB filename or code.<a name="41693"></a>
While the protein code in the first line
of an entry, which is used to identify the entry, must be unique for
all proteins in the file, the PDB name in this field, which is used to
get structural data, does not have to be unique. It can be a full file
name with path (<em>e.g.</em>, '/home/foo/pdbs/mystructure.pdb'), a file name without
a path (<em>e.g.</em>, 'mystructure.pdb'), or a PDB code (<em>e.g.</em>, '1abc'; M<small>ODELLER</small> will
automatically convert the code to a filename by adding '.pdb' or '.ent'
file extensions as necessary, and/or a 'pdb' prefix). In the latter two cases,
where no path is given, M<small>ODELLER</small> will search in the directories specified
by <i><a href="https://salilab.org/modeller/9v8/manual/node142.html#MEMB:iodata.atomfilesdirectory">io_data.atom_files_directory</a></i><a name="41908"></a> to find PDB files.

(PDB文件名或代码。
虽然条目首行的蛋白质代码（用于标识该条目）必须在文件中保持唯一，但此字段中的PDB名称（用于获取结构数据）无需唯一。它可以是以下形式：

(1)带路径的完整文件名（如 /home/foo/pdbs/mystructure.pdb）

(2)不带路径的文件名（如 mystructure.pdb）

(3)PDB代码（如 1abc；MODELLER会自动将其转换为文件名，必要时添加 .pdb 或 .ent 扩展名，或 pdb 前缀）。

对于后两种情况（未指定路径时），MODELLER会在 io_data.atom_files_directory 指定的目录中搜索PDB文件。)
<p>
</p></dd>
<dt>Fields 3-6:</dt>
<dd>The residue and chain identifiers (see below) for the first
(fields 3-4) and last residue (fields 5-6) of the sequence in the
subsequent lines. There is no need to edit the coordinate file if a
contiguous sequence of residues is required -- simply specify the
beginning and ending residues of the required contiguous region of the
chain. If the beginning residue is not found, no segment is read
in. If the ending residue identifier is not found in the coordinate
file, the last residue in the coordinate file is used. By default, the
whole file is read in.

<p>
The unspecified beginning and ending residue numbers and chain id's for a 
<tt>structure</tt> entry in an alignment file are taken automatically from 
the corresponding atom file, if possible. The first matching sequence in the
atom file that also satisfies the explicitly specified residue numbers and 
chain id's is used. A residue number is not specified when a blank character
or a dot, `.', is given. A chain id is not specified when a dot, `.', is 
given. This slight difference between residue and chain id's is necessary 
because a blank character is a valid chain id.

(
(0)残基和链标识符（见下文）用于指定后续行中序列的第一个残基（字段3-4）和最后一个残基（字段5-6）。

(1)如果需要一个连续的残基序列，无需编辑坐标文件——只需指定该连续区域的起始和终止残基即可。

(2)如果未找到起始残基，则不会读取任何片段。

(3)如果坐标文件中没有终止残基标识符，则默认使用坐标文件的最后一个残基。

(4)默认情况下，会读取整个文件。

(5)在比对文件中，如果某个结构条目的起始/终止残基编号和链ID未指定，程序会自动从对应的原子文件中提取（如果可能）。

(6)系统会使用原子文件中第一个匹配的序列，并同时满足显式指定的残基编号和链ID的条件。

(7)残基编号未指定的情况：当字段为空白字符或点（.）时。

(8)链ID未指定的情况：当字段为点（.）时。

(9)残基和链ID的细微差别：因为空白字符本身是有效的链ID，所以不能直接用空白表示未指定链ID，而必须用点（.）。)

</p><p>
</p></dd>
<dt>Field 7:</dt>
<dd>Protein name. Optional.

<p>
</p></dd>
<dt>Field 8:</dt>
<dd>Source of the protein. Optional.

<p>
</p></dd>
<dt>Field 9:</dt>
<dd>Resolution of the crystallographic analysis. Optional.

<p>
</p></dd>
<dt>Field 10:</dt>
<dd>R-factor of the crystallographic analysis. Optional.
</dd>
</dl>

<p>
A residue identifier is simply the 5-letter PDB residue number, and a chain
identifier the 1-letter PDB chain code. For example, <tt>'10I:A'</tt> is residue
number <tt>'10I'</tt> in chain <tt>'A'</tt>, and <tt>'6:'</tt> is residue number <tt>'6'</tt> in a chain
without a name. 

</p><p>
The residue number for the first position (resID1) in the 
<i>model_segment</i><a name="41919"></a> range <tt>'resID1:chainID1 resID2:chainID2'</tt> can be either 
a real residue number or <tt>'FIRST'</tt> (which indicates the first residue in a 
matching chain). The residue number for the second position (resID2) in 
the <i>model_segment</i><a name="41924"></a> range can be either: (1) a real residue number; 
(2) <tt>'LAST'</tt> (which indicates the last residue in a matching chain); 
(3) <tt>'+nn'</tt> (which requests the total number of residues to read, in which
case the chain id is ignored);
or <tt>'END'</tt> (which indicates the last residue in the PDB file). The chain id 
for either position in the <i>model_segment</i><a name="41930"></a> range (chainID1 or chainID2) 
can be either: (1) a real chain id (including a blank/space/null/empty); 
or <tt>'@'</tt>, which matches any chain id. 

(在 model_segment 范围 'resID1:chainID1 resID2:chainID2' 中：

(1)第一个位置的残基编号（resID1） 可以是：

    真实的残基编号，或

    'FIRST'（表示匹配链的第一个残基）。

(2)第二个位置的残基编号（resID2） 可以是：

    真实的残基编号；

    'LAST'（表示匹配链的最后一个残基）；

    '+nn'（请求读取的总残基数，此时链ID被忽略）；

    'END'（表示PDB文件的最后一个残基）。
    
(3)链ID（chainID1 或 chainID2） 可以是：

    真实的链ID（包括空白/空格/空值）；

   '@'（匹配任意链ID）。)

</p><p>
Examples, assuming a two chain PDB file (chains A and B): 

</p><p>

</p><ul>
<li><tt>'15:A 75:A'</tt> reads residues 15 to 75 in chain A.(读取链A的残基15至75)

<p>
</p></li>
<li><tt>'FIRST:@ 75:@'</tt> reads the first 75 residues in chain A (the first chain).
( 读取链A（第一条链）的前75个残基)
<p>
</p></li>
<li><tt>'FIRST:@ LAST:@'</tt> reads all residues in chain A, assuming <tt>'FIRST'</tt> is 
not a real number of the non-first residue in chain A.
(读取链A的所有残基（假设'FIRST'不是链A中某个残基的真实编号）)
<p>
</p></li>
<li><tt>'FIRST:@ +125:'</tt> reads a total of 125 residues, regardless of the PDB
numbering, starting from the first residue in chain A.
(从链A的第一个残基开始，连续读取125个残基（忽略PDB编号）)
<p>
</p></li>
<li><tt>'10:@ LAST:'</tt> reads all residues from 10 in chain A to the end of the 
file (chain id for the last residue is irrelevant), again 
assuming <tt>'LAST'</tt> is not a real residue number of a non-last residue.
(从链A的残基10读取至文件末尾（假设'LAST'不是某个非末端残基的真实编号）)
<p>
</p></li>
<li><tt>'FIRST:@ END:'</tt> reads the whole file no matter what, the chainID is 
ignored completely. (强制读取整个文件（完全忽略链ID）)

<p>
</p></li>
</ul>

<p>
For the <i>selection_segment</i><a name="41942"></a> the string containing <tt>'@'</tt> will match 
any residue number and chainID. For example, <tt>'@:A'</tt> is the first residue in 
chain <tt>'A'</tt> and <tt>'@:@'</tt> is the first residue in the coordinate file. The last 
chain can not be specified in a general way, except if it is the last residue 
in the file.

(对于 selection_segment，包含 '@' 的字符串会匹配任意残基编号和链ID。例如：

(1)'@:A' → 链A的第一个残基。

(2)'@:@' → 坐标文件的第一个残基。

(3)最后一个链无法通用指定，除非是文件的最后一个残基。)

</p><p>
When an alignment file is used in conjunction with structural
information, the first two fields must be filled in; the rest of them 
can be empty. If the alignment is not used in conjunction with
structural data, all but the first field can be empty. This means that
in comparative modeling, the template structures must have at least the first 
two fields specified while the target sequence must only have the first
field filled in. Thus, a simple second line of an entry in an alignment file
in the <tt>'PIR'</tt> format is

(当比对文件与结构信息联用时，前两个字段必须填写，其余可留空；若不涉及结构数据，则仅需填写第一个字段。这意味着：

    比较建模中：模板结构必须至少指定前两个字段，而目标序列只需填写第一个字段。)

</p><p>
</p><pre>structure:pdb_file:.:.:.:.::::
</pre>

<p>
This entry will result in reading from PDB file <tt>pdb_file</tt> 
the structure segment corresponding to the sequence in the subsequent
lines of the alignment entry.
(该条目将导致从PDB文件 pdb_file 中读取与比对条目后续行序列对应的结构片段。)

</p><p>
Each sequence must be terminated by the terminating character, `*'.
(每条序列必须以终止字符 * 结尾)

</p><p>
When the first character of the sequence line is the terminating character,
`*', the sequence is obtained from the specified PDB coordinate file
(Section&nbsp;<a href="https://salilab.org/modeller/9v8/manual/node97.html#SECTIONFILENAME">5.1.3</a>).
(若序列行的首个字符是终止字符 *，则序列从指定的PDB坐标文件中获取（参见第5.1.3节）)

</p><p>
Chain breaks are indicated by `/'. There should not be more than one
chain break character to indicate a single chain break (use gap
characters instead, `-'). All residue types specified in 
<tt>$RESTYP_LIB</tt>, but not patching residue types, are 
allowed; there are on the order of 100 residue types specified
in the <tt>$RESTYP_LIB</tt> library. To add your own residue types to 
this library, see Section&nbsp;<a href="https://salilab.org/modeller/9v8/manual/node36.html#SECTION:faq">3.1</a>, Question&nbsp;<a href="https://salilab.org/modeller/9v8/manual/node36.html#FAQ:restop">8</a>.
(链断裂用 / 表示。单个链断裂不应使用多个 / 字符（需用空位字符 - 替代）。
允许使用 $RESTYP_LIB 中定义的所有残基类型（约100种），但修补残基类型（patching residue types）除外。如需添加自定义残基类型，请参阅第3.1节第8问。)

</p><p>
The alignment file can contain any number of blank lines between the protein
entries. Comment lines can occur outside protein entries and must begin 
with the identifiers `C;' or `R;' as the first two characters in the line.
(比对文件中，不同蛋白质条目间可包含任意数量的空行。注释行必须位于蛋白质条目之外，且以标识符 C; 或 R; 开头（作为该行的前两个字符）。)
</p><p>
An alignment file is also used to input non-aligned sequences.
(比对文件也可用于输入未比对的序列。)

</p><p>
</p><hr>
<!--Navigation Panel-->
<a name="tex2html8466" href="https://salilab.org/modeller/9v8/manual/node455.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Alignment%20file%20(PIR)_files/next.png"></a> 
<a name="tex2html8460" href="https://salilab.org/modeller/9v8/manual/node453.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Alignment%20file%20(PIR)_files/up.png"></a> 
<a name="tex2html8454" href="https://salilab.org/modeller/9v8/manual/node453.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Alignment%20file%20(PIR)_files/prev.png"></a> 
<a name="tex2html8462" href="https://salilab.org/modeller/9v8/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Alignment%20file%20(PIR)_files/contents.png"></a> 
<a name="tex2html8464" href="https://salilab.org/modeller/9v8/manual/node470.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Alignment%20file%20(PIR)_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html8467" href="https://salilab.org/modeller/9v8/manual/node455.html">Restraints file</a>
<b> Up:</b> <a name="tex2html8461" href="https://salilab.org/modeller/9v8/manual/node453.html">File formats</a>
<b> Previous:</b> <a name="tex2html8455" href="https://salilab.org/modeller/9v8/manual/node453.html">File formats</a>
 &nbsp; <b>  <a name="tex2html8463" href="https://salilab.org/modeller/9v8/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html8465" href="https://salilab.org/modeller/9v8/manual/node470.html">Index</a></b> 
<!--End of Navigation Panel-->
<address>
Automatic builds
2010-04-21
</address>


</body></html>