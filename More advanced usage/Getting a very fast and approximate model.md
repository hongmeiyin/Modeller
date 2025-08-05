<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<!--Converted with LaTeX2HTML 2018.2 (Released May 16, 2018) -->
<html><head>
<title>Getting a very fast and approximate model</title>
<meta name="description" content="Getting a very fast and approximate model">
<meta name="keywords" content="manual">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">

<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<meta name="Generator" content="LaTeX2HTML v2018.2">
<meta http-equiv="Content-Style-Type" content="text/css">

<link rel="STYLESHEET" href="Getting%20a%20very%20fast%20and%20approximate%20model_files/manual.css">
<link rel="STYLESHEET" href="Getting%20a%20very%20fast%20and%20approximate%20model_files/pygments.css">

<link rel="next" href="https://salilab.org/modeller/manual/node21.html">
<link rel="previous" href="https://salilab.org/modeller/manual/node19.html">
<link rel="up" href="https://salilab.org/modeller/manual/node17.html">
<link rel="next" href="https://salilab.org/modeller/manual/node21.html">
</head>

<body>

<div class="navigation"><!--Navigation Panel-->
<a name="tex2html1713" href="https://salilab.org/modeller/manual/node21.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Getting%20a%20very%20fast%20and%20approximate%20model_files/next.png"></a> 
<a name="tex2html1707" href="https://salilab.org/modeller/manual/node17.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Getting%20a%20very%20fast%20and%20approximate%20model_files/up.png"></a> 
<a name="tex2html1701" href="https://salilab.org/modeller/manual/node19.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Getting%20a%20very%20fast%20and%20approximate%20model_files/prev.png"></a> 
<a name="tex2html1709" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Getting%20a%20very%20fast%20and%20approximate%20model_files/contents.png"></a> 
<a name="tex2html1711" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Getting%20a%20very%20fast%20and%20approximate%20model_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html1714" href="https://salilab.org/modeller/manual/node21.html">Building a model from</a>
<b> Up:</b> <a name="tex2html1708" href="https://salilab.org/modeller/manual/node17.html">More advanced usage</a>
<b> Previous:</b> <a name="tex2html1702" href="https://salilab.org/modeller/manual/node19.html">Changing the default optimization</a>
 &nbsp; <b>  <a name="tex2html1710" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html1712" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> 
<br>
<br></div>
<!--End of Navigation Panel-->

<h2><a name="SECTION00723000000000000000"></a>
<a name="SECTION:model-fast"></a>
<br>
Getting a very fast and approximate model
</h2>

<p>
To get an approximate model very quickly (to get a rough idea of what it looks
like, or to confirm that the alignment is reasonable) call the
<b><a href="https://salilab.org/modeller/manual/node69.html#CMD:AutoModel.veryfast">AutoModel.very_fast()</a></b><a name="3425"></a> method before <b><a href="https://salilab.org/modeller/manual/node70.html#CMD:AutoModel.make">AutoModel.make()</a></b><a name="3430"></a>. This uses only
a very limited amount of variable target function optimization with conjugate
gradients, and thus is roughly 3 times faster than the default procedure.

</p><p>
Note that no randomization of the starting structure is done in this case, so
only a single model can be produced.

</p><p>
This example also demonstrates the use of the <i class="sans">assess_methods</i><a name="3435"></a> keyword,
to request model assessment. In this case the GA341 method is requested. See
section&nbsp;<a href="https://salilab.org/modeller/manual/node44.html#SECTION:automodelcon">4.1.1</a>.

</p><p>

  </p><dl>
<dt><strong>Example: <a name="tex2html36" href="https://salilab.org/modeller/examples/automodel/model-fast.py">examples/automodel/model-fast.py</a></strong></dt>
<dd> <br>  <div class="pygments"><pre><span></span><span class="c1"># Very fast comparative modeling by the AutoModel class</span>
<span class="kn">from</span> <span class="nn">modeller</span> <span class="kn">import</span> <span class="o">*</span>
<span class="kn">from</span> <span class="nn">modeller.automodel</span> <span class="kn">import</span> <span class="o">*</span>    <span class="c1"># Load the AutoModel class</span>
<span class="c1">#from modeller import soap_protein_od</span>

<span class="n">log</span><span class="o">.</span><span class="n">verbose</span><span class="p">()</span>
<span class="n">env</span> <span class="o">=</span> <span class="n">Environ</span><span class="p">()</span>
<span class="c1"># directories for input atom files</span>
<span class="n">env</span><span class="o">.</span><span class="n">io</span><span class="o">.</span><span class="n">atom_files_directory</span> <span class="o">=</span> <span class="p">[</span><span class="s1">'.'</span><span class="p">,</span> <span class="s1">'../atom_files'</span><span class="p">]</span>

<span class="n">a</span> <span class="o">=</span> <span class="n">AutoModel</span><span class="p">(</span><span class="n">env</span><span class="p">,</span>
              <span class="n">alnfile</span><span class="o">=</span><span class="s1">'alignment.ali'</span><span class="p">,</span>      <span class="c1"># alignment filename</span>
              <span class="n">knowns</span><span class="o">=</span><span class="s1">'5fd1'</span><span class="p">,</span>                <span class="c1"># codes of the templates</span>
              <span class="n">sequence</span><span class="o">=</span><span class="s1">'1fdx'</span><span class="p">,</span>              <span class="c1"># code of the target</span>
              <span class="n">assess_methods</span><span class="o">=</span><span class="n">assess</span><span class="o">.</span><span class="n">GA341</span><span class="p">)</span>  <span class="c1"># request GA341 model assessment</span>
<span class="c1">#             assess_methods=(assess.GA341, assess.DOPE))  # GA341 and DOPE</span>
<span class="c1">#             assess_methods=soap_protein_od.Scorer())  # assess with SOAP</span>

<span class="n">a</span><span class="o">.</span><span class="n">very_fast</span><span class="p">()</span>                       <span class="c1"># prepare for extremely fast optimization</span>

<span class="n">a</span><span class="o">.</span><span class="n">starting_model</span> <span class="o">=</span> <span class="mi">2</span>
<span class="n">a</span><span class="o">.</span><span class="n">ending_model</span> <span class="o">=</span> <span class="mi">2</span>
<span class="n">a</span><span class="o">.</span><span class="n">final_malign3d</span> <span class="o">=</span> <span class="bp">True</span>

<span class="n">a</span><span class="o">.</span><span class="n">make</span><span class="p">()</span>                            <span class="c1"># make the comparative model</span>
</pre></div>
  
</dd>
</dl>  <br>
<p>
<br></p><hr>



</body></html>