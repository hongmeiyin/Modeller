<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<!--Converted with LaTeX2HTML 2018.2 (Released May 16, 2018) -->
<html><head>
<title>Refining only part of the model</title>
<meta name="description" content="Refining only part of the model">
<meta name="keywords" content="manual">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">

<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<meta name="Generator" content="LaTeX2HTML v2018.2">
<meta http-equiv="Content-Style-Type" content="text/css">

<link rel="STYLESHEET" href="Refining%20only%20part%20of%20the%20model_files/manual.css">
<link rel="STYLESHEET" href="Refining%20only%20part%20of%20the%20model_files/pygments.css">

<link rel="next" href="https://salilab.org/modeller/manual/node24.html">
<link rel="previous" href="https://salilab.org/modeller/manual/node22.html">
<link rel="up" href="https://salilab.org/modeller/manual/node17.html">
<link rel="next" href="https://salilab.org/modeller/manual/node24.html">
</head>

<body>

<div class="navigation"><!--Navigation Panel-->
<a name="tex2html1755" href="https://salilab.org/modeller/manual/node24.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Refining%20only%20part%20of%20the%20model_files/next.png"></a> 
<a name="tex2html1749" href="https://salilab.org/modeller/manual/node17.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Refining%20only%20part%20of%20the%20model_files/up.png"></a> 
<a name="tex2html1743" href="https://salilab.org/modeller/manual/node22.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Refining%20only%20part%20of%20the%20model_files/prev.png"></a> 
<a name="tex2html1751" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Refining%20only%20part%20of%20the%20model_files/contents.png"></a> 
<a name="tex2html1753" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Refining%20only%20part%20of%20the%20model_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html1756" href="https://salilab.org/modeller/manual/node24.html">Including disulfide bridges</a>
<b> Up:</b> <a name="tex2html1750" href="https://salilab.org/modeller/manual/node17.html">More advanced usage</a>
<b> Previous:</b> <a name="tex2html1744" href="https://salilab.org/modeller/manual/node22.html">Building an all hydrogen</a>
 &nbsp; <b>  <a name="tex2html1752" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html1754" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> 
<br>
<br></div>
<!--End of Navigation Panel-->

<h2><a name="SECTION00726000000000000000"></a>
<a name="SECTION:model-segment"></a>
<br>
Refining only part of the model
</h2>

<p>
The <tt>AutoModel</tt> class contains a <b><a href="https://salilab.org/modeller/manual/node67.html#CMD:AutoModel.selectatoms">AutoModel.select_atoms()</a></b><a name="3478"></a> function
which selects the atoms to be moved during optimization. By default, the
routine selects all atoms, but you can redefine it to select any subset of
atoms, and then only
those atoms will be refined. (To redefine the routine, it is necessary to
create a ‘subclass’ of <tt>AutoModel</tt>, here called <tt>MyModel</tt>, which
has the modified routine within it. We then use <tt>MyModel</tt> in place of
<tt>AutoModel</tt>. The <tt>select_atoms</tt> routine should return a
<tt>Selection</tt> object; see Section&nbsp;<a href="https://salilab.org/modeller/manual/node233.html#CLASS:Selection">6.9</a> for further
information.)

</p><p>
<a name="SECTION:residue-numbering"></a>In this particular case, we use the <b><a href="https://salilab.org/modeller/manual/node177.html#CMD:Model.residuerange">Model.residue_range()</a></b><a name="3493"></a> function to
select residues 1 and 2 from the first (A) chain. See Section
<a href="https://salilab.org/modeller/manual/node332.html#SECTION:residueid">6.17.10</a> for ways to specify residues, and <b><a href="https://salilab.org/modeller/manual/node234.html#CMD:Selection">Selection()</a></b><a name="3498"></a> for
other examples of selecting atoms or residues. Please note that the residue
numbers and chain IDs refer to the built model, <em>not</em> to the template(s).
This is because template PDB residue numbering can be inconsistent, and in the
case where you have two or more templates, residues from different parts of
the sequence coming from different templates could have the same number.
M<small>ODELLER</small> always names the model residues consistently, counting up from 1.
Chain IDs A, B, C, <em>etc</em> are assigned<a name="tex2html40" href="https://salilab.org/modeller/manual/footnode.html#foot3074"><sup><span class="arabic">2</span>.<span class="arabic">2</span></sup></a>. If in doubt about
residue numbering, first build a model using the simple script in section
<a href="https://salilab.org/modeller/manual/node16.html#SECTION:model-default">2.1</a>, and then look at the final model (or the initial
unoptimized <tt>.ini</tt> model) for the residue numbering.

</p><p>
By default, the selected atoms will “feel” the presence of other atoms via
all the static and possibly dynamic restraints that include both selected and
un-selected atoms. However, you can turn off dynamic interactions between the
selected and unselected regions by setting
<i class="sans"><a href="https://salilab.org/modeller/manual/node141.html#MEMB:EnergyData.nonbondedselatoms">EnergyData.nonbonded_sel_atoms</a></i><a name="3506"></a> to 2 (by default it is 1).

</p><p>
The difference between this script and the one for
loop modeling is that here the selected regions are optimized with the default
optimization protocol and the default restraints, which generally include
template-derived restraints. In contrast, the loop modeling routine does not
use template-dependent restraints, but does a much more thorough optimization.

</p><p>

  </p><dl>
<dt><strong>Example: <a name="tex2html41" href="https://salilab.org/modeller/examples/automodel/model-segment.py">examples/automodel/model-segment.py</a></strong></dt>
<dd> <br>  <div class="pygments"><pre><span></span><span class="c1"># Comparative modeling by the AutoModel class</span>
<span class="c1">#</span>
<span class="c1"># Demonstrates how to refine only a part of the model.</span>
<span class="c1">#</span>
<span class="c1"># You may want to use the more exhaustive "loop" modeling routines instead.</span>
<span class="c1">#</span>
<span class="kn">from</span> <span class="nn">modeller</span> <span class="kn">import</span> <span class="o">*</span>
<span class="kn">from</span> <span class="nn">modeller.automodel</span> <span class="kn">import</span> <span class="o">*</span>    <span class="c1"># Load the AutoModel class</span>

<span class="n">log</span><span class="o">.</span><span class="n">verbose</span><span class="p">()</span>

<span class="c1"># Override the 'select_atoms' routine in the 'AutoModel' class:</span>
<span class="c1"># (To build an all-hydrogen model, derive from AllHModel rather than AutoModel</span>
<span class="c1"># here.)</span>
<span class="k">class</span> <span class="nc">MyModel</span><span class="p">(</span><span class="n">AutoModel</span><span class="p">):</span>
    <span class="k">def</span> <span class="nf">select_atoms</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
        <span class="c1"># Select residues 1 and 2 in chain A (PDB numbering)</span>
        <span class="k">return</span> <span class="n">Selection</span><span class="p">(</span><span class="bp">self</span><span class="o">.</span><span class="n">residue_range</span><span class="p">(</span><span class="s1">'1:A'</span><span class="p">,</span> <span class="s1">'2:A'</span><span class="p">))</span>

        <span class="c1"># Residues 4, 6, 10 in chain A:</span>
        <span class="c1"># return Selection(self.residues['4:A'], self.residues['6:A'],</span>
        <span class="c1">#                  self.residues['10:A'])</span>

        <span class="c1"># All residues except 1-5 in chain A:</span>
        <span class="c1"># return Selection(self) - Selection(self.residue_range('1:A', '5:A'))</span>


<span class="n">env</span> <span class="o">=</span> <span class="n">Environ</span><span class="p">()</span>
<span class="c1"># directories for input atom files</span>
<span class="n">env</span><span class="o">.</span><span class="n">io</span><span class="o">.</span><span class="n">atom_files_directory</span> <span class="o">=</span> <span class="p">[</span><span class="s1">'.'</span><span class="p">,</span> <span class="s1">'../atom_files'</span><span class="p">]</span>
<span class="c1"># selected atoms do not feel the neighborhood</span>
<span class="n">env</span><span class="o">.</span><span class="n">edat</span><span class="o">.</span><span class="n">nonbonded_sel_atoms</span> <span class="o">=</span> <span class="mi">2</span>

<span class="c1"># Be sure to use 'MyModel' rather than 'AutoModel' here!</span>
<span class="n">a</span> <span class="o">=</span> <span class="n">MyModel</span><span class="p">(</span><span class="n">env</span><span class="p">,</span>
            <span class="n">alnfile</span>  <span class="o">=</span> <span class="s1">'alignment.ali'</span><span class="p">,</span>     <span class="c1"># alignment filename</span>
            <span class="n">knowns</span>   <span class="o">=</span> <span class="s1">'5fd1'</span><span class="p">,</span>              <span class="c1"># codes of the templates</span>
            <span class="n">sequence</span> <span class="o">=</span> <span class="s1">'1fdx'</span><span class="p">)</span>              <span class="c1"># code of the target</span>

<span class="n">a</span><span class="o">.</span><span class="n">starting_model</span><span class="o">=</span> <span class="mi">3</span>                <span class="c1"># index of the first model</span>
<span class="n">a</span><span class="o">.</span><span class="n">ending_model</span>  <span class="o">=</span> <span class="mi">3</span>                <span class="c1"># index of the last model</span>
                                   <span class="c1"># (determines how many models to calculate)</span>
<span class="n">a</span><span class="o">.</span><span class="n">make</span><span class="p">()</span>                           <span class="c1"># do comparative modeling</span>
</pre></div>
  
</dd>
</dl>  <br>
<p>

</p><div class="navigation"><hr>
<!--Navigation Panel-->
<a name="tex2html1755" href="https://salilab.org/modeller/manual/node24.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Refining%20only%20part%20of%20the%20model_files/next.png"></a> 
<a name="tex2html1749" href="https://salilab.org/modeller/manual/node17.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Refining%20only%20part%20of%20the%20model_files/up.png"></a> 
<a name="tex2html1743" href="https://salilab.org/modeller/manual/node22.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Refining%20only%20part%20of%20the%20model_files/prev.png"></a> 
<a name="tex2html1751" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Refining%20only%20part%20of%20the%20model_files/contents.png"></a> 
<a name="tex2html1753" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Refining%20only%20part%20of%20the%20model_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html1756" href="https://salilab.org/modeller/manual/node24.html">Including disulfide bridges</a>
<b> Up:</b> <a name="tex2html1750" href="https://salilab.org/modeller/manual/node17.html">More advanced usage</a>
<b> Previous:</b> <a name="tex2html1744" href="https://salilab.org/modeller/manual/node22.html">Building an all hydrogen</a>
 &nbsp; <b>  <a name="tex2html1752" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html1754" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> </div>
<!--End of Navigation Panel-->



</body></html>