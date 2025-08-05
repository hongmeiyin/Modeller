<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<!--Converted with LaTeX2HTML 2018.2 (Released May 16, 2018) -->
<html><head>
<title>Fully automated alignment and modeling</title>
<meta name="description" content="Fully automated alignment and modeling">
<meta name="keywords" content="manual">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">

<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<meta name="Generator" content="LaTeX2HTML v2018.2">
<meta http-equiv="Content-Style-Type" content="text/css">

<link rel="STYLESHEET" href="Fully%20automated%20alignment%20and%20modeling_files/manual.css">
<link rel="STYLESHEET" href="Fully%20automated%20alignment%20and%20modeling_files/pygments.css">

<link rel="previous" href="https://salilab.org/modeller/manual/node31.html">
<link rel="up" href="https://salilab.org/modeller/manual/node17.html">
<link rel="next" href="https://salilab.org/modeller/manual/node33.html">
</head>

<body>

<div class="navigation"><!--Navigation Panel-->
<a name="tex2html1879" href="https://salilab.org/modeller/manual/node33.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Fully%20automated%20alignment%20and%20modeling_files/next.png"></a> 
<a name="tex2html1873" href="https://salilab.org/modeller/manual/node17.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Fully%20automated%20alignment%20and%20modeling_files/up.png"></a> 
<a name="tex2html1869" href="https://salilab.org/modeller/manual/node31.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Fully%20automated%20alignment%20and%20modeling_files/prev.png"></a> 
<a name="tex2html1875" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Fully%20automated%20alignment%20and%20modeling_files/contents.png"></a> 
<a name="tex2html1877" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Fully%20automated%20alignment%20and%20modeling_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html1880" href="https://salilab.org/modeller/manual/node33.html">Loop optimization</a>
<b> Up:</b> <a name="tex2html1874" href="https://salilab.org/modeller/manual/node17.html">More advanced usage</a>
<b> Previous:</b> <a name="tex2html1870" href="https://salilab.org/modeller/manual/node31.html">Accessing output data after</a>
 &nbsp; <b>  <a name="tex2html1876" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html1878" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> 
<br>
<br></div>
<!--End of Navigation Panel-->

<h2><a name="SECTION007215000000000000000"></a>
<a name="SECTION:model-full"></a>
<br>
Fully automated alignment and modeling
</h2>

<p>
If you do not have an initial alignment between your templates and target
sequence, M<small>ODELLER</small> can derive one for you, fully automatically. All
M<small>ODELLER</small> requires is a a PIR file containing the target sequence and the
template PDB codes (their sequences are not required — just use a single '*'
character — as M<small>ODELLER</small> will read these from the PDBs). Use the
<tt>AutoModel</tt> class as per usual, but call the <b><a href="https://salilab.org/modeller/manual/node68.html#CMD:AutoModel.autoalign">AutoModel.auto_align()</a></b><a name="3708"></a>
method before <b><a href="https://salilab.org/modeller/manual/node70.html#CMD:AutoModel.make">AutoModel.make()</a></b><a name="3713"></a>; see the example below. (M<small>ODELLER</small> has
a variety of other alignment methods which you can use instead for this
purpose; see Section&nbsp;<a href="https://salilab.org/modeller/manual/node292.html#SECTION:compare">6.16</a> for more details.)

</p><p>
Please be aware that the single most important factor that determines the
quality of a model is the quality of the alignment. If the alignment is
incorrect, the model will also be incorrect. <span class="textbf">For this reason,
automated alignment for comparative modeling should not be used unless
the sequences are so similar that the calculated alignment is likely to be
correct, which usually requires more than 50% sequence identity.</span>
Instead, the alignment should be carefully inspected, optimized
by hand, and checked by the <b><a href="https://salilab.org/modeller/manual/node301.html#CMD:Alignment.check">Alignment.check()</a></b><a name="3720"></a> command before
used in modeling. Moreover, several iterations of alignment
and modeling may be necessary in general.

</p><p>

  </p><dl>
<dt><strong>Example: <a name="tex2html55" href="https://salilab.org/modeller/examples/automodel/model-full.py">examples/automodel/model-full.py</a></strong></dt>
<dd> <br>  <div class="pygments"><pre><span></span><span class="c1"># A sample script for fully automated comparative modeling</span>
<span class="kn">from</span> <span class="nn">modeller</span> <span class="kn">import</span> <span class="o">*</span>
<span class="kn">from</span> <span class="nn">modeller.automodel</span> <span class="kn">import</span> <span class="o">*</span>    <span class="c1"># Load the AutoModel class</span>

<span class="n">log</span><span class="o">.</span><span class="n">verbose</span><span class="p">()</span>
<span class="n">env</span> <span class="o">=</span> <span class="n">Environ</span><span class="p">()</span>

<span class="c1"># directories for input atom files</span>
<span class="n">env</span><span class="o">.</span><span class="n">io</span><span class="o">.</span><span class="n">atom_files_directory</span> <span class="o">=</span> <span class="p">[</span><span class="s1">'.'</span><span class="p">,</span> <span class="s1">'../atom_files'</span><span class="p">]</span>

<span class="n">a</span> <span class="o">=</span> <span class="n">AutoModel</span><span class="p">(</span><span class="n">env</span><span class="p">,</span>
              <span class="c1"># file with template codes and target sequence</span>
              <span class="n">alnfile</span>  <span class="o">=</span> <span class="s1">'alignment.seg'</span><span class="p">,</span>
              <span class="c1"># PDB codes of the templates</span>
              <span class="n">knowns</span>   <span class="o">=</span> <span class="p">(</span><span class="s1">'5fd1'</span><span class="p">,</span> <span class="s1">'1fdn'</span><span class="p">,</span> <span class="s1">'1fxd'</span><span class="p">,</span> <span class="s1">'1iqz'</span><span class="p">),</span>
              <span class="c1"># code of the target</span>
              <span class="n">sequence</span> <span class="o">=</span> <span class="s1">'1fdx'</span><span class="p">)</span>
<span class="n">a</span><span class="o">.</span><span class="n">auto_align</span><span class="p">()</span>                      <span class="c1"># get an automatic alignment</span>
<span class="n">a</span><span class="o">.</span><span class="n">make</span><span class="p">()</span>                            <span class="c1"># do comparative modeling</span>
</pre></div>
  
</dd>
</dl>  <br>
<p>

</p><dl>
<dt><strong>Example: <a name="tex2html56" href="https://salilab.org/modeller/examples/automodel/alignment.seg">examples/automodel/alignment.seg</a></strong></dt>
<dd> <br>
<br>
<pre class="verbatim">&gt;P1;1fdx
sequence::::::ferredoxin:Peptococcus aerogenes:-1.00:-1.00
AYVINDSCIACGACKPECPVNIIQGSIYAIDADSCIDCGSCASVCPVGAPNPED*
&gt;P1;1fdn
structureX:1fdn:FIRST:@:55:@:ferredoxin:Clostrodium acidiurici: 1.84:-1.0
*
&gt;P1;5fd1
structureX:5fd1:FIRST:@:60:@:ferredoxin:Azotobacter vinelandii: 1.90:0.192
*
&gt;P1;1fxd
structureX:1fxd:FIRST:@:58:@:ferredoxin:Desolfovibrio gigas: 1.70:-1.0
*
&gt;P1;1iqz
structureX:1iqz:FIRST:@:60:@:ferredoxin:Bacillus thermoproteolyticus: 2.30:-1.0
*
</pre>
</dd>
</dl>  <br>
<p>

</p><div class="navigation"><hr>
<!--Navigation Panel-->
<a name="tex2html1879" href="https://salilab.org/modeller/manual/node33.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Fully%20automated%20alignment%20and%20modeling_files/next.png"></a> 
<a name="tex2html1873" href="https://salilab.org/modeller/manual/node17.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Fully%20automated%20alignment%20and%20modeling_files/up.png"></a> 
<a name="tex2html1869" href="https://salilab.org/modeller/manual/node31.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Fully%20automated%20alignment%20and%20modeling_files/prev.png"></a> 
<a name="tex2html1875" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Fully%20automated%20alignment%20and%20modeling_files/contents.png"></a> 
<a name="tex2html1877" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Fully%20automated%20alignment%20and%20modeling_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html1880" href="https://salilab.org/modeller/manual/node33.html">Loop optimization</a>
<b> Up:</b> <a name="tex2html1874" href="https://salilab.org/modeller/manual/node17.html">More advanced usage</a>
<b> Previous:</b> <a name="tex2html1870" href="https://salilab.org/modeller/manual/node31.html">Accessing output data after</a>
 &nbsp; <b>  <a name="tex2html1876" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html1878" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> </div>
<!--End of Navigation Panel-->



</body></html>