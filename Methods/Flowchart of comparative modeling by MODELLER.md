<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<!--Converted with LaTeX2HTML 2018.2 (Released May 16, 2018) -->
<html><head>
<title>Flowchart of comparative modeling by MODELLER</title>
<meta name="description" content="Flowchart of comparative modeling by MODELLER">
<meta name="keywords" content="manual">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">

<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<meta name="Generator" content="LaTeX2HTML v2018.2">
<meta http-equiv="Content-Style-Type" content="text/css">

<link rel="STYLESHEET" href="Flowchart%20of%20comparative%20modeling%20by%20MODELLER_files/manual.css">
<link rel="STYLESHEET" href="Flowchart%20of%20comparative%20modeling%20by%20MODELLER_files/pygments.css">

<link rel="next" href="https://salilab.org/modeller/manual/node500.html">
<link rel="previous" href="https://salilab.org/modeller/manual/node496.html">
<link rel="up" href="https://salilab.org/modeller/manual/node486.html">
<link rel="next" href="https://salilab.org/modeller/manual/node500.html">
</head>

<body>

<div class="navigation"><!--Navigation Panel-->
<a name="tex2html9298" href="https://salilab.org/modeller/manual/node500.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Flowchart%20of%20comparative%20modeling%20by%20MODELLER_files/next.png"></a> 
<a name="tex2html9292" href="https://salilab.org/modeller/manual/node486.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Flowchart%20of%20comparative%20modeling%20by%20MODELLER_files/up.png"></a> 
<a name="tex2html9286" href="https://salilab.org/modeller/manual/node498.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Flowchart%20of%20comparative%20modeling%20by%20MODELLER_files/prev.png"></a> 
<a name="tex2html9294" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Flowchart%20of%20comparative%20modeling%20by%20MODELLER_files/contents.png"></a> 
<a name="tex2html9296" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Flowchart%20of%20comparative%20modeling%20by%20MODELLER_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html9299" href="https://salilab.org/modeller/manual/node500.html">Loop modeling method</a>
<b> Up:</b> <a name="tex2html9293" href="https://salilab.org/modeller/manual/node486.html">Methods</a>
<b> Previous:</b> <a name="tex2html9287" href="https://salilab.org/modeller/manual/node498.html">Restraints and their derivatives</a>
 &nbsp; <b>  <a name="tex2html9295" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html9297" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> 
<br>
<br></div>
<!--End of Navigation Panel-->

<h1><a name="SECTION001340000000000000000"></a>
    <a name="SECTION:flowchart"></a>
<br>
Flowchart of comparative modeling by M<small>ODELLER</small>
</h1>
    This section describes a flowchart of comparative modeling by 
M<small>ODELLER</small>, as implemented in the <tt>AutoModel</tt> class (see
chapter&nbsp;<a href="https://salilab.org/modeller/manual/node15.html#CHAPTERAUTOMODEL">2</a>).

<p>
Input: script file, alignment file, PDB file(s) for template(s).

</p><p>
Output: 

</p><p>
<table cellpadding="3">
<tbody><tr><td align="LEFT"><tt>job.log</tt></td>
<td align="LEFT"><tt>log</tt> file</td>
</tr>
<tr><td align="LEFT"><tt>job.ini</tt></td>
<td align="LEFT">initial conformation for optimization</td>
</tr>
<tr><td align="LEFT"><tt>job.rsr</tt></td>
<td align="LEFT">restraints file</td>
</tr>
<tr><td align="LEFT"><tt>job.sch</tt></td>
<td align="LEFT">VTFM schedule file</td>
</tr>
<tr><td align="LEFT"><tt>job.B9999????</tt></td>
<td align="LEFT">PDB atom file(s) for the model(s) of the target sequence(目标序列模型对应的PDB原子文件（单个或多个）)</td>
</tr>
<tr><td align="LEFT"><tt>job.V9999????</tt></td>
<td align="LEFT">violation profiles for the model(s)(模型（们）的违例分布图)</td>
</tr>
<tr><td align="LEFT"><tt>job.D9999????</tt></td>
<td align="LEFT">progress of optimization</td>
</tr>
<tr><td align="LEFT"><tt>job.BL9999????</tt></td>
<td align="LEFT">optional loop model(s)</td>
</tr>
<tr><td align="LEFT"><tt>job.DL9999????</tt></td>
<td align="LEFT">progress of optimization for loop model(s)</td>
</tr>
<tr><td align="LEFT"><tt>job.IL9999????</tt></td>
<td align="LEFT">initial structures for loop model(s)</td>
</tr>
</tbody></table>

</p><p>
The main M<small>ODELLER</small> routines used in each step are given in parentheses.(每个步骤中使用的常规操作以括号形式给出)

</p><p>

</p><ol>
<li>Read and check the alignment between the target sequence and the template
   structures (阅读并检查目标序列与模板结构之间的对齐情况)
<br>(<b><a href="https://salilab.org/modeller/manual/node296.html#CMD:Alignment.append">Alignment.append()</a></b><a name="45759"></a> and <b><a href="https://salilab.org/modeller/manual/node301.html#CMD:Alignment.check">Alignment.check()</a></b><a name="45764"></a>).

<p>
</p></li>
<li>Calculate restraints on the target from its alignment with the templates:(根据目标与模板的对齐情况计算约束条件)

<p>

</p><ol>
<li>Generate molecular topology for the target sequence
         (<b><a href="https://salilab.org/modeller/manual/node185.html#CMD:Model.generatetopology">Model.generate_topology()</a></b><a name="45769"></a>).
      Disulfides in the target are assigned here from the equivalent 
      disulfides in the templates (<b><a href="https://salilab.org/modeller/manual/node189.html#CMD:Model.patchsstemplates">Model.patch_ss_templates()</a></b><a name="45774"></a>). Any user defined 
      patches are also done here (as defined in the 
      <b><a href="https://salilab.org/modeller/manual/node74.html#CMD:AutoModel.specialpatches">AutoModel.special_patches()</a></b><a name="45779"></a> routine).

(为目标序列生成分子拓扑结构（Model.generate_topology()）。

    目标序列中的二硫键会根据模板中的等效二硫键进行分配（Model.patch_ss_templates()）。

    用户自定义的修补操作（如通过 AutoModel.special_patches() 定义）也会在此阶段完成。)
 
<p>
</p></li>
<li>Calculate coordinates for atoms that have equivalent atoms in the 
      templates as an average over all templates (<b><a href="https://salilab.org/modeller/manual/node192.html#CMD:Model.transferxyz">Model.transfer_xyz()</a></b><a name="45784"></a>)
      (alternatively, read the initial coordinates from a file).

(为模板中具有等效原子的目标原子计算坐标（通过所有模板的平均值计算，使用 Model.transfer_xyz() 方法），或者（替代方案）从文件中读取初始坐标。)
<p>
</p></li>
<li>Build the remaining unknown coordinates using internal coordinates 
      from the C<small>HARMM</small> topology library (<b><a href="https://salilab.org/modeller/manual/node191.html#CMD:Model.build">Model.build()</a></b><a name="45790"></a>).

(使用 CHARMM 拓扑库中的内部坐标（键长、键角、二面角等）来构建剩余未知原子的坐标（通过 Model.build() 方法实现）)
<p>
</p></li>
<li>Write the initial model to a file with extension <tt>.ini</tt> (<b><a href="https://salilab.org/modeller/manual/node183.html#CMD:Model.write">Model.write()</a></b><a name="45795"></a>).

<p>
</p></li>
<li>Generate stereochemical, homology-derived, and special restraints
      (<b><a href="https://salilab.org/modeller/manual/node215.html#CMD:Restraints.make">Restraints.make()</a></b><a name="45800"></a>)
      (alternatively, skip this and assume the restraints file already exists):

(生成立体化学约束、同源衍生约束和特殊约束（通过 Restraints.make() 方法），或者跳过此步骤（假设约束文件已存在）)
<p>
<table cellpadding="3">
<tbody><tr><td align="LEFT">stereochemical</td>
<td align="LEFT">restraint_type = 'bond angle dihedral improper'</td>
</tr>
<tr><td align="LEFT">mainchain dihedrals <span class="MATH">Φ</span>, <span class="MATH">Ψ</span></td>
<td align="LEFT">restraint_type = 'phi-psi_binormal'</td>
</tr>
<tr><td align="LEFT">mainchain dihedral <span class="MATH">ω</span></td>
<td align="LEFT">restraint_type = 'omega_dihedral'</td>
</tr>
<tr><td align="LEFT">sidechain dihedral <span class="MATH">χ<sub>1</sub></span></td>
<td align="LEFT">restraint_type = 'chi1_dihedral'</td>
</tr>
<tr><td align="LEFT">sidechain dihedral <span class="MATH">χ<sub>2</sub></span></td>
<td align="LEFT">restraint_type = 'chi2_dihedral'</td>
</tr>
<tr><td align="LEFT">sidechain dihedral <span class="MATH">χ<sub>3</sub></span></td>
<td align="LEFT">restraint_type = 'chi3_dihedral'</td>
</tr>
<tr><td align="LEFT">sidechain dihedral <span class="MATH">χ<sub>4</sub></span></td>
<td align="LEFT">restraint_type = 'chi4_dihedral'</td>
</tr>
<tr><td align="LEFT">mainchain CA-CA distance</td>
<td align="LEFT">restraint_type = 'distance'</td>
</tr>
<tr><td align="LEFT">mainchain N-O distance</td>
<td align="LEFT">restraint_type = 'distance'</td>
</tr>
<tr><td align="LEFT">sidechain-mainchain distance</td>
<td align="LEFT">restraint_type = 'distance'</td>
</tr>
<tr><td align="LEFT">sidechain-sidechain distance</td>
<td align="LEFT">restraint_type = 'distance'</td>
</tr>
<tr><td align="LEFT">ligand distance restraints</td>
<td align="LEFT"><b><a href="https://salilab.org/modeller/manual/node73.html#CMD:AutoModel.nonstdrestraints">AutoModel.nonstd_restraints()</a></b><a name="45805"></a> routine</td>
</tr>
<tr><td align="LEFT">user defined</td>
<td align="LEFT"><b><a href="https://salilab.org/modeller/manual/node72.html#CMD:AutoModel.specialrestraints">AutoModel.special_restraints()</a></b><a name="45810"></a> routine</td>
</tr>
<tr><td align="LEFT">non-bonded pairs distance</td>
<td align="LEFT">restraint_type = 'sphere'; calculated on the fly</td>
</tr>
</tbody></table>

</p><p>
</p></li>
<li>Write all restraints to a file with extension <tt>.rsr</tt> (<b><a href="https://salilab.org/modeller/manual/node228.html#CMD:Restraints.write">Restraints.write()</a></b><a name="45815"></a>).
   
</li>
</ol>

<p>
</p></li>
<li>Calculate model(s) that satisfy the restraints as well as possible.
   For each model:

<p>

</p><ol>
<li>Generate the optimization schedule for the variable target function
         method (VTFM).
(生成用于可变目标函数方法（VTFM）的优化调度方案)
<p>
</p></li>
<li>Read the initial model (usually from the <tt>.ini</tt> file from 2.d)
         (<b><a href="https://salilab.org/modeller/manual/node181.html#CMD:Model.read">Model.read()</a></b><a name="45820"></a>).
(读取初始模型（通常来自2.d中的.ini文件）)
<p>
</p></li>
<li>Randomize the initial structure by adding a random number between
      <span class="MATH"><img width="17" height="28" align="MIDDLE" border="0" src="Flowchart%20of%20comparative%20modeling%20by%20MODELLER_files/img120.png" alt="$\pm$"></span><i class="sans"><a href="https://salilab.org/modeller/manual/node44.html#MEMB:AutoModel.deviation">AutoModel.deviation</a></i><a name="45825"></a> angstroms to all atomic positions
      (<b><a href="https://salilab.org/modeller/manual/node254.html#CMD:Selection.randomizexyz">Selection.randomize_xyz()</a></b><a name="45830"></a>).

(通过在所有原子位置上添加一个介于 ±AutoModel.deviation 埃（Å）之间的随机数，对初始结构进行随机化扰动（使用 Selection.randomize_xyz() 方法）)
<p>
</p></li>
<li>Optimize the model:(优化模型)
      
<ul>
<li>Partially optimize the model by VTFM; Repeat the following steps 
        as many times as specified by the optimization schedule:
(通过可变目标函数方法（VTFM）对模型进行部分优化，并按优化调度方案重复以下步骤：)
<p>

</p><ul>
<li>Select only the restraints that operate on the atoms that are
          close enough in sequence, as specified by the current step of
          VTFM (<b><a href="https://salilab.org/modeller/manual/node219.html#CMD:Restraints.pick">Restraints.pick()</a></b><a name="45835"></a>).
(选择约束：根据当前VTFM阶段的要求，仅选取作用于序列邻近原子的约束（Restraints.pick()）)
</li>
<li>Optimize the model by conjugate gradients, using only currently 
              selected restraints (<b><a href="https://salilab.org/modeller/manual/node269.html#CMD:ConjugateGradients">ConjugateGradients()</a></b><a name="45840"></a>).
(共轭梯度优化：使用当前选定的约束对模型进行共轭梯度优化（ConjugateGradients()）)       
</li>
</ul>

<p>
</p></li>
<li>Refine the model by simulated annealing with molecular dynamics,
        if so selected:(若启用模拟退火细化，则执行以下步骤：)

<p>

</p><ul>
<li>Do a short conjugate gradients optimization (<b><a href="https://salilab.org/modeller/manual/node269.html#CMD:ConjugateGradients">ConjugateGradients()</a></b><a name="45845"></a>).
(短暂共轭梯度优化（ConjugateGradients()）)
</li>
<li>Increase temperature in several steps and do molecular dynamics 
              optimization at each temperature (<b><a href="https://salilab.org/modeller/manual/node271.html#CMD:MolecularDynamics">MolecularDynamics()</a></b><a name="45850"></a>).
(升温阶段：分步升高温度，并在每步温度下进行分子动力学优化（MolecularDynamics()）)
</li>
<li>Decrease temperature in several steps and do molecular dynamics 
          optimization at each temperature (<b><a href="https://salilab.org/modeller/manual/node271.html#CMD:MolecularDynamics">MolecularDynamics()</a></b><a name="45855"></a>).
(降温阶段：分步降低温度，并在每步温度下进行分子动力学优化（MolecularDynamics()）)
</li>
<li>Do a short conjugate gradients optimization (<b><a href="https://salilab.org/modeller/manual/node269.html#CMD:ConjugateGradients">ConjugateGradients()</a></b><a name="45860"></a>).
(短暂共轭梯度优化（ConjugateGradients()）)
       
</li>
</ul>
</li>
</ul>

<p>
</p></li>
<li>Calculate the remaining restraint violations and write them out
      (<b><a href="https://salilab.org/modeller/manual/node259.html#CMD:Selection.energy">Selection.energy()</a></b><a name="45865"></a>).
(计算并输出剩余约束违例（Selection.energy()）)
<p>
</p></li>
<li>Write out the final model to a file with extension <tt>.B9999????.pdb</tt>
    where <tt>????</tt> indicates the model number (<b><a href="https://salilab.org/modeller/manual/node183.html#CMD:Model.write">Model.write()</a></b><a name="45870"></a>). Also write
    out the violations profile.

(输出最终模型：

    模型文件：.B9999????.pdb（???? 为模型编号）。

    违例分布文件。)
<p>
</p></li>
<li>Superpose the models and the templates, if so selected by
         <i class="sans"><a href="https://salilab.org/modeller/manual/node56.html#MEMB:AutoModel.finalmalign3d">AutoModel.final_malign3d</a></i><a name="45875"></a> = <tt>True</tt>, and write
         them out (<b><a href="https://salilab.org/modeller/manual/node303.html#CMD:Alignment.appendmodel">Alignment.append_model()</a></b><a name="45881"></a>, <b><a href="https://salilab.org/modeller/manual/node317.html#CMD:Alignment.malign3d">Alignment.malign3d()</a></b><a name="45886"></a>).
         
(若设置 AutoModel.final_malign3d = True，则进行结构叠合：
将模型与模板叠合并输出（Alignment.append_model(), Alignment.malign3d()）)
<p>
</p></li>
<li>Do loop modeling if so selected using the <tt>LoopModel</tt> class.
(若启用循环建模，则使用 LoopModel 类进行局部优化)
   
</li>
</ol>
</li>
</ol>

<p>

</p><div class="navigation"><hr>
<!--Navigation Panel-->
<a name="tex2html9298" href="https://salilab.org/modeller/manual/node500.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="Flowchart%20of%20comparative%20modeling%20by%20MODELLER_files/next.png"></a> 
<a name="tex2html9292" href="https://salilab.org/modeller/manual/node486.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="Flowchart%20of%20comparative%20modeling%20by%20MODELLER_files/up.png"></a> 
<a name="tex2html9286" href="https://salilab.org/modeller/manual/node498.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="Flowchart%20of%20comparative%20modeling%20by%20MODELLER_files/prev.png"></a> 
<a name="tex2html9294" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="Flowchart%20of%20comparative%20modeling%20by%20MODELLER_files/contents.png"></a> 
<a name="tex2html9296" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="Flowchart%20of%20comparative%20modeling%20by%20MODELLER_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html9299" href="https://salilab.org/modeller/manual/node500.html">Loop modeling method</a>
<b> Up:</b> <a name="tex2html9293" href="https://salilab.org/modeller/manual/node486.html">Methods</a>
<b> Previous:</b> <a name="tex2html9287" href="https://salilab.org/modeller/manual/node498.html">Restraints and their derivatives</a>
 &nbsp; <b>  <a name="tex2html9295" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html9297" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> </div>
<!--End of Navigation Panel-->



</body></html>
