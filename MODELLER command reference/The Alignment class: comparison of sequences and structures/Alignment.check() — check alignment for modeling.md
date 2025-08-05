<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<!--Converted with LaTeX2HTML 2018.2 (Released May 16, 2018) -->
<html><head>
<title>Alignment.check() — check alignment for modeling</title>
<meta name="description" content="Alignment.check() — check alignment for modeling">
<meta name="keywords" content="manual">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">

<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<meta name="Generator" content="LaTeX2HTML v2018.2">
<meta http-equiv="Content-Style-Type" content="text/css">

<link rel="STYLESHEET" href="Alignment.check()%20%E2%80%94%20check%20alignment%20for%20modeling_files/manual.css">
<link rel="STYLESHEET" href="Alignment.check()%20%E2%80%94%20check%20alignment%20for%20modeling_files/pygments.css">

<link rel="next" href="https://salilab.org/modeller/manual/node302.html">
<link rel="previous" href="https://salilab.org/modeller/manual/node300.html">
<link rel="up" href="https://salilab.org/modeller/manual/node292.html">
<link rel="next" href="https://salilab.org/modeller/manual/node302.html">
</head>

<body>

<div class="navigation"><!--Navigation Panel-->
<a name="tex2html6334" href="https://salilab.org/modeller/manual/node302.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Alignment.check()%20%E2%80%94%20check%20alignment%20for%20modeling_files/next.png"></a> 
<a name="tex2html6328" href="https://salilab.org/modeller/manual/node292.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Alignment.check()%20%E2%80%94%20check%20alignment%20for%20modeling_files/up.png"></a> 
<a name="tex2html6322" href="https://salilab.org/modeller/manual/node300.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Alignment.check()%20%E2%80%94%20check%20alignment%20for%20modeling_files/prev.png"></a> 
<a name="tex2html6330" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Alignment.check()%20%E2%80%94%20check%20alignment%20for%20modeling_files/contents.png"></a> 
<a name="tex2html6332" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Alignment.check()%20%E2%80%94%20check%20alignment%20for%20modeling_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html6335" href="https://salilab.org/modeller/manual/node302.html">Alignment.compare_with()   compare</a>
<b> Up:</b> <a name="tex2html6329" href="https://salilab.org/modeller/manual/node292.html">The Alignment class: comparison</a>
<b> Previous:</b> <a name="tex2html6323" href="https://salilab.org/modeller/manual/node300.html">Alignment.check_sequence_structure()   check</a>
 &nbsp; <b>  <a name="tex2html6331" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html6333" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> 
<br>
<br></div>
<!--End of Navigation Panel-->

<h2><a name="SECTION0011169000000000000000">
Alignment.check() — check alignment for modeling</a>
</h2> <a name="28740"></a><a name="CMD:Alignment.check"></a>  
<a name="28743"></a><tt>check(io=None)</tt>
<br><blockquote>
This command evaluates an alignment to be used for
comparative modeling, by calling <b><a href="https://salilab.org/modeller/manual/node299.html#CMD:Alignment.checkstructurestructure">Alignment.check_structure_structure()</a></b><a name="28753"></a>
and <b><a href="https://salilab.org/modeller/manual/node300.html#CMD:Alignment.checksequencestructure">Alignment.check_sequence_structure()</a></b><a name="28758"></a>.

</blockquote>

  <dl>
<dt><strong>Example: <a name="tex2html173" href="https://salilab.org/modeller/examples/commands/read_alignment.py">examples/commands/read_alignment.py</a></strong></dt>
<dd> <br>  <div class="pygments"><pre><span></span><span class="c1"># Example for: Alignment.append(), Alignment.write(),</span>
<span class="c1">#              Alignment.check()</span>

<span class="c1"># Read an alignment, write it out in the 'PAP' format, and</span>
<span class="c1"># check the alignment of the N-1 structures as well as the</span>
<span class="c1"># alignment of the N-th sequence with each of the N-1 structures.</span>

<span class="kn">from</span> <span class="nn">modeller</span> <span class="kn">import</span> <span class="o">*</span>

<span class="n">log</span><span class="o">.</span><span class="n">level</span><span class="p">(</span><span class="n">output</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">notes</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">warnings</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">errors</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">memory</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
<span class="n">env</span> <span class="o">=</span> <span class="n">Environ</span><span class="p">()</span>
<span class="n">env</span><span class="o">.</span><span class="n">io</span><span class="o">.</span><span class="n">atom_files_directory</span> <span class="o">=</span> <span class="p">[</span><span class="s1">'../atom_files'</span><span class="p">]</span>

<span class="n">aln</span> <span class="o">=</span> <span class="n">Alignment</span><span class="p">(</span><span class="n">env</span><span class="p">)</span>
<span class="n">aln</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="nb">file</span><span class="o">=</span><span class="s1">'toxin.ali'</span><span class="p">,</span> <span class="n">align_codes</span><span class="o">=</span><span class="s1">'all'</span><span class="p">)</span>
<span class="n">aln</span><span class="o">.</span><span class="n">write</span><span class="p">(</span><span class="nb">file</span><span class="o">=</span><span class="s1">'toxin.pap'</span><span class="p">,</span> <span class="n">alignment_format</span><span class="o">=</span><span class="s1">'PAP'</span><span class="p">)</span>
<span class="n">aln</span><span class="o">.</span><span class="n">write</span><span class="p">(</span><span class="nb">file</span><span class="o">=</span><span class="s1">'toxin.fasta'</span><span class="p">,</span> <span class="n">alignment_format</span><span class="o">=</span><span class="s1">'FASTA'</span><span class="p">)</span>
<span class="n">aln</span><span class="o">.</span><span class="n">check</span><span class="p">()</span>
</pre></div>
  
</dd>
</dl>  <br>
<p>
<br></p><hr>



</body></html>