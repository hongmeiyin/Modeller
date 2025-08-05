<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<!--Converted with LaTeX2HTML 2018.2 (Released May 16, 2018) -->
<html><head>
<title>Residues and chains in multi-chain models</title>
<meta name="description" content="Residues and chains in multi-chain models">
<meta name="keywords" content="manual">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">

<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<meta name="Generator" content="LaTeX2HTML v2018.2">
<meta http-equiv="Content-Style-Type" content="text/css">

<link rel="STYLESHEET" href="Residues%20and%20chains%20in%20multi-chain%20models_files/manual.css">
<link rel="STYLESHEET" href="Residues%20and%20chains%20in%20multi-chain%20models_files/pygments.css">

<link rel="next" href="https://salilab.org/modeller/manual/node31.html">
<link rel="previous" href="https://salilab.org/modeller/manual/node29.html">
<link rel="up" href="https://salilab.org/modeller/manual/node17.html">
<link rel="next" href="https://salilab.org/modeller/manual/node31.html">
</head>

<body>

<div class="navigation"><!--Navigation Panel-->
<a name="tex2html1853" href="https://salilab.org/modeller/manual/node31.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Residues%20and%20chains%20in%20multi-chain%20models_files/next.png"></a> 
<a name="tex2html1847" href="https://salilab.org/modeller/manual/node17.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Residues%20and%20chains%20in%20multi-chain%20models_files/up.png"></a> 
<a name="tex2html1841" href="https://salilab.org/modeller/manual/node29.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Residues%20and%20chains%20in%20multi-chain%20models_files/prev.png"></a> 
<a name="tex2html1849" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Residues%20and%20chains%20in%20multi-chain%20models_files/contents.png"></a> 
<a name="tex2html1851" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Residues%20and%20chains%20in%20multi-chain%20models_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html1854" href="https://salilab.org/modeller/manual/node31.html">Accessing output data after</a>
<b> Up:</b> <a name="tex2html1848" href="https://salilab.org/modeller/manual/node17.html">More advanced usage</a>
<b> Previous:</b> <a name="tex2html1842" href="https://salilab.org/modeller/manual/node29.html">Building multi-chain models</a>
 &nbsp; <b>  <a name="tex2html1850" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html1852" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> 
<br>
<br></div>
<!--End of Navigation Panel-->

<h2><a name="SECTION007213000000000000000"></a>
<a name="SECTION:model-multichain"></a>
<br>
Residues and chains in multi-chain models
</h2>

<p>
Just as M<small>ODELLER</small> automatically assigns residue numbers starting from 1 for
the model sequence, it automatically assigns chain IDs.
Chain IDs are assigned alphabetically: A, B, <em>etc</em>.
Thus, in the previous example (see Section&nbsp;<a href="https://salilab.org/modeller/manual/node29.html#SECTION:model-multichain-sym">2.2.12</a>)
the model contains residues labeled 1 through 74 in chain A, and 75 through
148 in chain B. You can change this behavior and label the chains and residues
yourself by calling <b><a href="https://salilab.org/modeller/manual/node194.html#CMD:Model.renamesegments">Model.rename_segments()</a></b><a name="3632"></a> from within the
<b><a href="https://salilab.org/modeller/manual/node74.html#CMD:AutoModel.specialpatches">AutoModel.special_patches()</a></b><a name="3637"></a> method.

</p><p>
You must <span class="textit">always</span> specify the chain
ID when referring to an atom (see <i class="sans"><a href="https://salilab.org/modeller/manual/node174.html#MEMB:Model.atoms">Model.atoms</a></i><a name="3642"></a>) or residue
(see <i class="sans"><a href="https://salilab.org/modeller/manual/node332.html#MEMB:Sequence.residues">Sequence.residues</a></i><a name="3647"></a>). M<small>ODELLER</small> will not 'guess' the chain
for you if you leave it out. For example, the CA atom in residue 30 in chain
B can be specified with the identifier 'CA:30:B'.

</p><p>
In the example below, the model is relabeled to contain residues 1 through 74
in chain X and 1 through 74 in chain Y. A user-defined restraint is also
added between two atoms in the new chain Y. Note that in this example the two
chains are <span class="textit">not</span> constrained to be symmetric; however, the symmetry
restraint from the previous example can be added in if desired.

</p><p>

  </p><dl>
<dt><strong>Example: <a name="tex2html50" href="https://salilab.org/modeller/examples/automodel/model-multichain.py">examples/automodel/model-multichain.py</a></strong></dt>
<dd> <br>  <div class="pygments"><pre><span></span><span class="c1"># Comparative modeling by the AutoModel class</span>
<span class="c1">#</span>
<span class="c1"># Demonstrates how to build multi-chain models</span>
<span class="c1">#</span>
<span class="kn">from</span> <span class="nn">modeller</span> <span class="kn">import</span> <span class="o">*</span>
<span class="kn">from</span> <span class="nn">modeller.automodel</span> <span class="kn">import</span> <span class="o">*</span>    <span class="c1"># Load the AutoModel class</span>

<span class="n">log</span><span class="o">.</span><span class="n">verbose</span><span class="p">()</span>

<span class="k">class</span> <span class="nc">MyModel</span><span class="p">(</span><span class="n">AutoModel</span><span class="p">):</span>
    <span class="k">def</span> <span class="nf">special_patches</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">aln</span><span class="p">):</span>
        <span class="c1"># Rename both chains and renumber the residues in each</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">rename_segments</span><span class="p">(</span><span class="n">segment_ids</span><span class="o">=</span><span class="p">[</span><span class="s1">'X'</span><span class="p">,</span> <span class="s1">'Y'</span><span class="p">],</span>
                             <span class="n">renumber_residues</span><span class="o">=</span><span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">1</span><span class="p">])</span>
        <span class="c1"># Another way to label individual chains:</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">chains</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span><span class="o">.</span><span class="n">name</span> <span class="o">=</span> <span class="s1">'X'</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">chains</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">name</span> <span class="o">=</span> <span class="s1">'Y'</span>

    <span class="k">def</span> <span class="nf">special_restraints</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">aln</span><span class="p">):</span>
        <span class="n">rsr</span> <span class="o">=</span> <span class="bp">self</span><span class="o">.</span><span class="n">restraints</span>
        <span class="n">at</span> <span class="o">=</span> <span class="bp">self</span><span class="o">.</span><span class="n">atoms</span>
<span class="c1">#       Restrain the specified CB-CB distance to 8 angstroms (st. dev.=0.1)</span>
<span class="c1">#       Use a harmonic potential and X-Y distance group.</span>
<span class="c1">#       Note that because special_patches is called before special_restraints,</span>
<span class="c1">#       we must use the relabeled chain IDs and residue numbers here.</span>
        <span class="n">rsr</span><span class="o">.</span><span class="n">add</span><span class="p">(</span><span class="n">forms</span><span class="o">.</span><span class="n">Gaussian</span><span class="p">(</span><span class="n">group</span><span class="o">=</span><span class="n">physical</span><span class="o">.</span><span class="n">xy_distance</span><span class="p">,</span>
                               <span class="n">feature</span><span class="o">=</span><span class="n">features</span><span class="o">.</span><span class="n">Distance</span><span class="p">(</span><span class="n">at</span><span class="p">[</span><span class="s1">'CB:40:Y'</span><span class="p">],</span>
                                                         <span class="n">at</span><span class="p">[</span><span class="s1">'CB:71:Y'</span><span class="p">]),</span>
                               <span class="n">mean</span><span class="o">=</span><span class="mf">8.0</span><span class="p">,</span> <span class="n">stdev</span><span class="o">=</span><span class="mf">0.1</span><span class="p">))</span>

<span class="n">env</span> <span class="o">=</span> <span class="n">Environ</span><span class="p">()</span>
<span class="c1"># directories for input atom files</span>
<span class="n">env</span><span class="o">.</span><span class="n">io</span><span class="o">.</span><span class="n">atom_files_directory</span> <span class="o">=</span> <span class="p">[</span><span class="s1">'.'</span><span class="p">,</span> <span class="s1">'../atom_files'</span><span class="p">]</span>

<span class="c1"># Be sure to use 'MyModel' rather than 'AutoModel' here!</span>
<span class="n">a</span> <span class="o">=</span> <span class="n">MyModel</span><span class="p">(</span><span class="n">env</span><span class="p">,</span>
            <span class="n">alnfile</span>  <span class="o">=</span> <span class="s1">'twochain.ali'</span> <span class="p">,</span>     <span class="c1"># alignment filename</span>
            <span class="n">knowns</span>   <span class="o">=</span> <span class="s1">'2abx'</span><span class="p">,</span>              <span class="c1"># codes of the templates</span>
            <span class="n">sequence</span> <span class="o">=</span> <span class="s1">'1hc9'</span><span class="p">)</span>              <span class="c1"># code of the target</span>

<span class="n">a</span><span class="o">.</span><span class="n">starting_model</span><span class="o">=</span> <span class="mi">2</span>                <span class="c1"># index of the first model</span>
<span class="n">a</span><span class="o">.</span><span class="n">ending_model</span>  <span class="o">=</span> <span class="mi">2</span>                <span class="c1"># index of the last model</span>
                                   <span class="c1"># (determines how many models to calculate)</span>
<span class="n">a</span><span class="o">.</span><span class="n">make</span><span class="p">()</span>                           <span class="c1"># do comparative modeling</span>
</pre></div>
  
</dd>
</dl>  <br>
<p>

</p><div class="navigation"><hr>
<!--Navigation Panel-->
<a name="tex2html1853" href="https://salilab.org/modeller/manual/node31.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Residues%20and%20chains%20in%20multi-chain%20models_files/next.png"></a> 
<a name="tex2html1847" href="https://salilab.org/modeller/manual/node17.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Residues%20and%20chains%20in%20multi-chain%20models_files/up.png"></a> 
<a name="tex2html1841" href="https://salilab.org/modeller/manual/node29.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Residues%20and%20chains%20in%20multi-chain%20models_files/prev.png"></a> 
<a name="tex2html1849" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Residues%20and%20chains%20in%20multi-chain%20models_files/contents.png"></a> 
<a name="tex2html1851" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Residues%20and%20chains%20in%20multi-chain%20models_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html1854" href="https://salilab.org/modeller/manual/node31.html">Accessing output data after</a>
<b> Up:</b> <a name="tex2html1848" href="https://salilab.org/modeller/manual/node17.html">More advanced usage</a>
<b> Previous:</b> <a name="tex2html1842" href="https://salilab.org/modeller/manual/node29.html">Building multi-chain models</a>
 &nbsp; <b>  <a name="tex2html1850" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html1852" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> </div>
<!--End of Navigation Panel-->



</body></html>