<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<!--Converted with LaTeX2HTML 2018.2 (Released May 16, 2018) -->
<html><head>
<title>Changing the default optimization and refinement protocol</title>
<meta name="description" content="Changing the default optimization and refinement protocol">
<meta name="keywords" content="manual">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">

<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<meta name="Generator" content="LaTeX2HTML v2018.2">
<meta http-equiv="Content-Style-Type" content="text/css">

<link rel="STYLESHEET" href="Changing%20the%20default%20optimization%20and%20refinement%20protocol_files/manual.css">
<link rel="STYLESHEET" href="Changing%20the%20default%20optimization%20and%20refinement%20protocol_files/pygments.css">

<link rel="next" href="https://salilab.org/modeller/manual/node20.html">
<link rel="previous" href="https://salilab.org/modeller/manual/node18.html">
<link rel="up" href="https://salilab.org/modeller/manual/node17.html">
<link rel="next" href="https://salilab.org/modeller/manual/node20.html">
</head>

<body>

<div class="navigation"><!--Navigation Panel-->
<a name="tex2html1699" href="https://salilab.org/modeller/manual/node20.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Changing%20the%20default%20optimization%20and%20refinement%20protocol_files/next.png"></a> 
<a name="tex2html1693" href="https://salilab.org/modeller/manual/node17.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Changing%20the%20default%20optimization%20and%20refinement%20protocol_files/up.png"></a> 
<a name="tex2html1687" href="https://salilab.org/modeller/manual/node18.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Changing%20the%20default%20optimization%20and%20refinement%20protocol_files/prev.png"></a> 
<a name="tex2html1695" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Changing%20the%20default%20optimization%20and%20refinement%20protocol_files/contents.png"></a> 
<a name="tex2html1697" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Changing%20the%20default%20optimization%20and%20refinement%20protocol_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html1700" href="https://salilab.org/modeller/manual/node20.html">Getting a very fast</a>
<b> Up:</b> <a name="tex2html1694" href="https://salilab.org/modeller/manual/node17.html">More advanced usage</a>
<b> Previous:</b> <a name="tex2html1688" href="https://salilab.org/modeller/manual/node18.html">Including water molecules, HETATM</a>
 &nbsp; <b>  <a name="tex2html1696" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html1698" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> 
<br>
<br></div>
<!--End of Navigation Panel-->

<h2><a name="SECTION00722000000000000000"></a>
<a name="SECTION:model-changeopt"></a>
<br>
Changing the default optimization and refinement protocol
</h2>

<p>
See Section&nbsp;<a href="https://salilab.org/modeller/manual/node499.html#SECTION:flowchart">A.4</a> for a detailed description of the
optimization and refinement protocol used by <tt>AutoModel</tt>. To summarize,
each model is first optimized with the variable target function
method<a name="3003"></a>
<a name="3257"></a> (VTFM)
with conjugate gradients (CG), and is then refined using
molecular dynamics (MD) with simulated annealing (SA) [<a href="https://salilab.org/modeller/manual/node517.html#SalBlu93">Šali &amp; Blundell, 1993</a>]. Most of
the time (70%) is spent on the MD&amp;SA part. Our experience is that when
MD&amp;SA are used, if there are violations in the best of the 10 models, they
probably come from an alignment error, not an optimizer failure
(if there are no insertions longer than approximately 15 residues).

</p><p>
The VTFM step can be tuned by adjusting <i class="sans"><a href="https://salilab.org/modeller/manual/node45.html#MEMB:AutoModel.libraryschedule">AutoModel.library_schedule</a></i><a name="3386"></a>,
<i class="sans"><a href="https://salilab.org/modeller/manual/node50.html#MEMB:AutoModel.maxvariterations">AutoModel.max_var_iterations</a></i><a name="3391"></a>, and <i class="sans"><a href="https://salilab.org/modeller/manual/node52.html#MEMB:AutoModel.maxmolpdf">AutoModel.max_molpdf</a></i><a name="3396"></a>.

</p><p>
The MD&amp;SA step can be tuned by adjusting <i class="sans"><a href="https://salilab.org/modeller/manual/node46.html#MEMB:AutoModel.mdlevel">AutoModel.md_level</a></i><a name="3401"></a>.

</p><p>
The whole optimization can be repeated multiple times if desired (by default
it is run only once) by adjusting <i class="sans"><a href="https://salilab.org/modeller/manual/node51.html#MEMB:AutoModel.repeatoptimization">AutoModel.repeat_optimization</a></i><a name="3406"></a>.

</p><p>
The energy function used in both VTFM and MD&amp;SA can be scaled by setting
<i class="sans"><a href="https://salilab.org/modeller/manual/node121.html#MEMB:Environ.schedulescale">Environ.schedule_scale</a></i><a name="3411"></a>. (Note that for VTFM, the function is additionally
scaled by the factors set in <i class="sans"><a href="https://salilab.org/modeller/manual/node45.html#MEMB:AutoModel.libraryschedule">AutoModel.library_schedule</a></i><a name="3416"></a>.)

</p><p>

  </p><dl>
<dt><strong>Example: <a name="tex2html35" href="https://salilab.org/modeller/examples/automodel/model-changeopt.py">examples/automodel/model-changeopt.py</a></strong></dt>
<dd> <br>  <div class="pygments"><pre><span></span><span class="c1"># Example of changing the default optimization schedule</span>
<span class="kn">from</span> <span class="nn">modeller</span> <span class="kn">import</span> <span class="o">*</span>
<span class="kn">from</span> <span class="nn">modeller.automodel</span> <span class="kn">import</span> <span class="o">*</span>

<span class="n">log</span><span class="o">.</span><span class="n">verbose</span><span class="p">()</span>
<span class="n">env</span> <span class="o">=</span> <span class="n">Environ</span><span class="p">()</span>

<span class="c1"># Give less weight to all soft-sphere restraints:</span>
<span class="n">env</span><span class="o">.</span><span class="n">schedule_scale</span> <span class="o">=</span> <span class="n">physical</span><span class="o">.</span><span class="n">Values</span><span class="p">(</span><span class="n">default</span><span class="o">=</span><span class="mf">1.0</span><span class="p">,</span> <span class="n">soft_sphere</span><span class="o">=</span><span class="mf">0.7</span><span class="p">)</span>
<span class="n">env</span><span class="o">.</span><span class="n">io</span><span class="o">.</span><span class="n">atom_files_directory</span> <span class="o">=</span> <span class="p">[</span><span class="s1">'.'</span><span class="p">,</span> <span class="s1">'../atom_files'</span><span class="p">]</span>

<span class="n">a</span> <span class="o">=</span> <span class="n">AutoModel</span><span class="p">(</span><span class="n">env</span><span class="p">,</span> <span class="n">alnfile</span><span class="o">=</span><span class="s1">'alignment.ali'</span><span class="p">,</span> <span class="n">knowns</span><span class="o">=</span><span class="s1">'5fd1'</span><span class="p">,</span> <span class="n">sequence</span><span class="o">=</span><span class="s1">'1fdx'</span><span class="p">)</span>
<span class="n">a</span><span class="o">.</span><span class="n">starting_model</span> <span class="o">=</span> <span class="n">a</span><span class="o">.</span><span class="n">ending_model</span> <span class="o">=</span> <span class="mi">1</span>

<span class="c1"># Very thorough VTFM optimization:</span>
<span class="n">a</span><span class="o">.</span><span class="n">library_schedule</span> <span class="o">=</span> <span class="n">autosched</span><span class="o">.</span><span class="n">slow</span>
<span class="n">a</span><span class="o">.</span><span class="n">max_var_iterations</span> <span class="o">=</span> <span class="mi">300</span>

<span class="c1"># Thorough MD optimization:</span>
<span class="n">a</span><span class="o">.</span><span class="n">md_level</span> <span class="o">=</span> <span class="n">refine</span><span class="o">.</span><span class="n">slow</span>

<span class="c1"># Repeat the whole cycle 2 times and do not stop unless obj.func. &gt; 1E6</span>
<span class="n">a</span><span class="o">.</span><span class="n">repeat_optimization</span> <span class="o">=</span> <span class="mi">2</span>
<span class="n">a</span><span class="o">.</span><span class="n">max_molpdf</span> <span class="o">=</span> <span class="mf">1e6</span>

<span class="n">a</span><span class="o">.</span><span class="n">make</span><span class="p">()</span>
</pre></div>
  
</dd>
</dl>  <br>
<p>

</p><div class="navigation"><hr>
<!--Navigation Panel-->
<a name="tex2html1699" href="https://salilab.org/modeller/manual/node20.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Changing%20the%20default%20optimization%20and%20refinement%20protocol_files/next.png"></a> 
<a name="tex2html1693" href="https://salilab.org/modeller/manual/node17.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Changing%20the%20default%20optimization%20and%20refinement%20protocol_files/up.png"></a> 
<a name="tex2html1687" href="https://salilab.org/modeller/manual/node18.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Changing%20the%20default%20optimization%20and%20refinement%20protocol_files/prev.png"></a> 
<a name="tex2html1695" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Changing%20the%20default%20optimization%20and%20refinement%20protocol_files/contents.png"></a> 
<a name="tex2html1697" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Changing%20the%20default%20optimization%20and%20refinement%20protocol_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html1700" href="https://salilab.org/modeller/manual/node20.html">Getting a very fast</a>
<b> Up:</b> <a name="tex2html1694" href="https://salilab.org/modeller/manual/node17.html">More advanced usage</a>
<b> Previous:</b> <a name="tex2html1688" href="https://salilab.org/modeller/manual/node18.html">Including water molecules, HETATM</a>
 &nbsp; <b>  <a name="tex2html1696" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html1698" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> </div>
<!--End of Navigation Panel-->



</body></html>