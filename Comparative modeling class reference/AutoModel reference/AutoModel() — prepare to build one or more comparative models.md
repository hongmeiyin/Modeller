<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<!--Converted with LaTeX2HTML 2018.2 (Released May 16, 2018) -->
<html><head>
<title>AutoModel() — prepare to build one or more comparative models</title>
<meta name="description" content="AutoModel() — prepare to build one or more comparative models">
<meta name="keywords" content="manual">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">

<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<meta name="Generator" content="LaTeX2HTML v2018.2">
<meta http-equiv="Content-Style-Type" content="text/css">

<link rel="STYLESHEET" href="AutoModel()%20%E2%80%94%20prepare%20to%20build%20one%20or%20more%20comparative%20models_files/manual.css">
<link rel="STYLESHEET" href="AutoModel()%20%E2%80%94%20prepare%20to%20build%20one%20or%20more%20comparative%20models_files/pygments.css">

<link rel="next" href="https://salilab.org/modeller/manual/node45.html">
<link rel="previous" href="https://salilab.org/modeller/manual/node43.html">
<link rel="up" href="https://salilab.org/modeller/manual/node43.html">
<link rel="next" href="https://salilab.org/modeller/manual/node45.html">
</head>

<body>

<div class="navigation"><!--Navigation Panel-->
<a name="tex2html2141" href="https://salilab.org/modeller/manual/node45.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="AutoModel()%20%E2%80%94%20prepare%20to%20build%20one%20or%20more%20comparative%20models_files/next.png"></a> 
<a name="tex2html2135" href="https://salilab.org/modeller/manual/node43.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="AutoModel()%20%E2%80%94%20prepare%20to%20build%20one%20or%20more%20comparative%20models_files/up.png"></a> 
<a name="tex2html2129" href="https://salilab.org/modeller/manual/node43.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="AutoModel()%20%E2%80%94%20prepare%20to%20build%20one%20or%20more%20comparative%20models_files/prev.png"></a> 
<a name="tex2html2137" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="AutoModel()%20%E2%80%94%20prepare%20to%20build%20one%20or%20more%20comparative%20models_files/contents.png"></a> 
<a name="tex2html2139" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="AutoModel()%20%E2%80%94%20prepare%20to%20build%20one%20or%20more%20comparative%20models_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html2142" href="https://salilab.org/modeller/manual/node45.html">AutoModel.library_schedule   select</a>
<b> Up:</b> <a name="tex2html2136" href="https://salilab.org/modeller/manual/node43.html">AutoModel reference</a>
<b> Previous:</b> <a name="tex2html2130" href="https://salilab.org/modeller/manual/node43.html">AutoModel reference</a>
 &nbsp; <b>  <a name="tex2html2138" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html2140" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> 
<br>
<br></div>
<!--End of Navigation Panel-->

<h2><a name="SECTION00911000000000000000">
AutoModel() — prepare to build one or more comparative models</a>
</h2> <a name="5851"></a><a name="CMD:AutoModel"></a><a name="5854"></a><tt>AutoModel(env,
 alnfile, knowns, sequence, deviation=None, library_schedule=None, 
csrfile=None, inifile=None, assess_methods=None, root_name=None)</tt>
<br><a name="SECTION:automodelcon"></a><blockquote>
<i class="sans">alnfile</i><a name="5923"></a> is required, and usually specifies the name of the PIR file which
contains an alignment between <i class="sans">knowns</i><a name="5926"></a> (the templates) and <i class="sans">sequence</i><a name="5929"></a>
(the target sequence).
</blockquote>
<p>
</p><blockquote><i class="sans">alnfile</i><a name="5932"></a> can instead be a readable file handle (see <b><a href="https://salilab.org/modeller/manual/node458.html#CMD:modfile.File">modfile.File()</a></b><a name="5937"></a>) from which the alignment
will be read, or an existing <tt>Alignment</tt> object containing <i class="sans">knowns</i><a name="5944"></a>
and <i class="sans">sequence</i><a name="5947"></a>. (Note that this is only supported with a subset of
<tt>AutoModel</tt> functionality; in particular, it does not work with parallel
jobs, <i class="sans"><a href="https://salilab.org/modeller/manual/node53.html#MEMB:AutoModel.initialmalign3d">AutoModel.initial_malign3d</a></i><a name="5952"></a>, or <i class="sans"><a href="https://salilab.org/modeller/manual/node56.html#MEMB:AutoModel.finalmalign3d">AutoModel.final_malign3d</a></i><a name="5957"></a>.)
</blockquote>
<p>
</p><blockquote><a name="MEMB:AutoModel.deviation"></a><i class="sans">deviation</i><a name="5962"></a> controls the amount of randomization done by <tt>randomize.xyz</tt>
or <tt>randomize.dihedrals</tt>; see also <i class="sans"><a href="https://salilab.org/modeller/manual/node48.html#MEMB:AutoModel.randmethod">AutoModel.rand_method</a></i><a name="5967"></a>. (This can also
be set after the object is created, by assigning to <tt>'AutoModel.deviation'</tt>.
The default is 4Å.)
</blockquote>
<p>
</p><blockquote><i class="sans">library_schedule</i><a name="5973"></a>, if given, sets an initial value for
<i class="sans"><a href="https://salilab.org/modeller/manual/node45.html#MEMB:AutoModel.libraryschedule">AutoModel.library_schedule</a></i><a name="5976"></a>
</blockquote>
<p>
</p><blockquote>If <i class="sans">csrfile</i><a name="5981"></a> is set, restraints are not constructed, but are instead read
from the user-supplied file of the same name. See
section&nbsp;<a href="https://salilab.org/modeller/manual/node26.html#SECTION:model-myrsr">2.2.9</a> for an example.
</blockquote>
<p>
</p><blockquote>If <i class="sans">inifile</i><a name="5984"></a> is set, an initial model is read from the user-supplied file of
the same name. See section&nbsp;<a href="https://salilab.org/modeller/manual/node27.html#SECTION:model-myini">2.2.10</a> for an example.
</blockquote>
<p>
</p><blockquote>If <i class="sans">root_name</i><a name="5987"></a> is set, it is used to name any output files (see also
<b><a href="https://salilab.org/modeller/manual/node76.html#CMD:AutoModel.getmodelfilename">AutoModel.get_model_filename()</a></b><a name="5990"></a>). By default, files are named using
<i class="sans">sequence</i><a name="5995"></a>.
</blockquote>
<p>
</p><blockquote><a name="MEMB:AutoModel.assessmethods"></a><i class="sans">assess_methods</i><a name="5998"></a> allows you to request assessment of the generated models
(by default, none is done).
You can provide a function (or callable), or list of functions, for this
purpose, including any of the SOAP potentials (<em>e.g.</em>, <b><a href="https://salilab.org/modeller/manual/node286.html#CMD:soaploop.Scorer">soap_loop.Scorer()</a></b><a name="6002"></a>,
<b><a href="https://salilab.org/modeller/manual/node291.html#CMD:soapproteinod.Scorer">soap_protein_od.Scorer()</a></b><a name="6007"></a>), or any of the standard functions provided
in the <tt>assess</tt> module:
</blockquote>
<ul>
<li><tt>assess.GA341</tt>, which uses the GA341 method (see
<b><a href="https://salilab.org/modeller/manual/node205.html#CMD:Model.assessga341">Model.assess_ga341()</a></b><a name="6014"></a>).

<p>
</p></li>
<li><tt>assess.DOPE</tt>, which uses the DOPE method (see
<b><a href="https://salilab.org/modeller/manual/node261.html#CMD:Selection.assessdope">Selection.assess_dope()</a></b><a name="6020"></a>).

<p>
</p></li>
<li><tt>assess.DOPEHR</tt>, which uses the DOPE-HR method (see
<b><a href="https://salilab.org/modeller/manual/node262.html#CMD:Selection.assessdopehr">Selection.assess_dopehr()</a></b><a name="6026"></a>).

<p>
</p></li>
<li><tt>assess.normalized_dope</tt>, which uses the normalized DOPE method
(see <b><a href="https://salilab.org/modeller/manual/node206.html#CMD:Model.assessnormalizeddope">Model.assess_normalized_dope()</a></b><a name="6032"></a>).
</li>
</ul><blockquote>
(This can also be set after the object is created, by assigning to
<tt>'AutoModel.assess_methods'</tt>.) See Section&nbsp;<a href="https://salilab.org/modeller/manual/node20.html#SECTION:model-fast">2.2.3</a> for an
example. Only the region selected by <b><a href="https://salilab.org/modeller/manual/node67.html#CMD:AutoModel.selectatoms">AutoModel.select_atoms()</a></b><a name="6038"></a> is
assessed, although most assessment functions take the interaction with the
rest of the system into account.
Note that only standard models are assessed in this way; if you are
also building loop models, see <i class="sans"><a href="https://salilab.org/modeller/manual/node83.html#MEMB:LoopModel.loop.assessmethods">LoopModel.loop.assess_methods</a></i><a name="6043"></a>.
</blockquote>
<p>
</p><blockquote>By default, models are built using heavy atom-only parameters and topology. If
you want to use different parameters, read them in before creating the
<tt>AutoModel</tt> object with <b><a href="https://salilab.org/modeller/manual/node159.html#CMD:Topology.read">Topology.read()</a></b><a name="6050"></a> and <b><a href="https://salilab.org/modeller/manual/node162.html#CMD:Parameters.read">Parameters.read()</a></b><a name="6055"></a>.
</blockquote>
<p>
</p><blockquote>See section&nbsp;<a href="https://salilab.org/modeller/manual/node16.html#SECTION:model-default">2.1</a> for a general example of using this
class.

</blockquote>

<p>

</p><div class="navigation"><hr>
<!--Navigation Panel-->
<a name="tex2html2141" href="https://salilab.org/modeller/manual/node45.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="AutoModel()%20%E2%80%94%20prepare%20to%20build%20one%20or%20more%20comparative%20models_files/next.png"></a> 
<a name="tex2html2135" href="https://salilab.org/modeller/manual/node43.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="AutoModel()%20%E2%80%94%20prepare%20to%20build%20one%20or%20more%20comparative%20models_files/up.png"></a> 
<a name="tex2html2129" href="https://salilab.org/modeller/manual/node43.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="AutoModel()%20%E2%80%94%20prepare%20to%20build%20one%20or%20more%20comparative%20models_files/prev.png"></a> 
<a name="tex2html2137" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="AutoModel()%20%E2%80%94%20prepare%20to%20build%20one%20or%20more%20comparative%20models_files/contents.png"></a> 
<a name="tex2html2139" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="AutoModel()%20%E2%80%94%20prepare%20to%20build%20one%20or%20more%20comparative%20models_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html2142" href="https://salilab.org/modeller/manual/node45.html">AutoModel.library_schedule   select</a>
<b> Up:</b> <a name="tex2html2136" href="https://salilab.org/modeller/manual/node43.html">AutoModel reference</a>
<b> Previous:</b> <a name="tex2html2130" href="https://salilab.org/modeller/manual/node43.html">AutoModel reference</a>
 &nbsp; <b>  <a name="tex2html2138" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html2140" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> </div>
<!--End of Navigation Panel-->



</body></html>