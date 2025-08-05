<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<!--Converted with LaTeX2HTML 2018.2 (Released May 16, 2018) -->
<html><head>
<title>AutoModel.md_level — control the model refinement level</title>
<meta name="description" content="AutoModel.md_level — control the model refinement level">
<meta name="keywords" content="manual">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">

<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<meta name="Generator" content="LaTeX2HTML v2018.2">
<meta http-equiv="Content-Style-Type" content="text/css">

<link rel="STYLESHEET" href="AutoModel.md_level%20%E2%80%94%20control%20the%20model%20refinement%20level_files/manual.css">
<link rel="STYLESHEET" href="AutoModel.md_level%20%E2%80%94%20control%20the%20model%20refinement%20level_files/pygments.css">

<link rel="next" href="https://salilab.org/modeller/manual/node47.html">
<link rel="previous" href="https://salilab.org/modeller/manual/node45.html">
<link rel="up" href="https://salilab.org/modeller/manual/node43.html">
<link rel="next" href="https://salilab.org/modeller/manual/node47.html">
</head>

<body>

<div class="navigation"><!--Navigation Panel-->
<a name="tex2html2169" href="https://salilab.org/modeller/manual/node47.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="AutoModel.md_level%20%E2%80%94%20control%20the%20model%20refinement%20level_files/next.png"></a> 
<a name="tex2html2163" href="https://salilab.org/modeller/manual/node43.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="AutoModel.md_level%20%E2%80%94%20control%20the%20model%20refinement%20level_files/up.png"></a> 
<a name="tex2html2157" href="https://salilab.org/modeller/manual/node45.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="AutoModel.md_level%20%E2%80%94%20control%20the%20model%20refinement%20level_files/prev.png"></a> 
<a name="tex2html2165" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="AutoModel.md_level%20%E2%80%94%20control%20the%20model%20refinement%20level_files/contents.png"></a> 
<a name="tex2html2167" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="AutoModel.md_level%20%E2%80%94%20control%20the%20model%20refinement%20level_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html2170" href="https://salilab.org/modeller/manual/node47.html">AutoModel.outputs   all</a>
<b> Up:</b> <a name="tex2html2164" href="https://salilab.org/modeller/manual/node43.html">AutoModel reference</a>
<b> Previous:</b> <a name="tex2html2158" href="https://salilab.org/modeller/manual/node45.html">AutoModel.library_schedule   select</a>
 &nbsp; <b>  <a name="tex2html2166" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html2168" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> 
<br>
<br></div>
<!--End of Navigation Panel-->

<h2><a name="SECTION00913000000000000000">
AutoModel.md_level — control the model refinement level</a>
</h2> <a name="6087"></a><a name="MEMB:AutoModel.mdlevel"></a><blockquote>
This allows the degree of MD refinement of the models to be
adjusted. You can define your own function for this purpose, set it to the
special <a name="tex2html70" href="https://www.python.org/">Python</a> value <tt>None</tt> (in which case no additional refinement is
done) or use one of the predefined functions in the <tt>refine</tt> module —
<tt>refine.very_fast</tt>, <tt>refine.fast</tt>, <tt>refine.slow</tt>, <tt>refine.very_slow</tt>
or <tt>refine.slow_large</tt> — which perform different amounts of MD annealing.
See the <tt>modlib/modeller/automodel/refine.py</tt> file for more information.
</blockquote>
<p>
</p><blockquote>See Section&nbsp;<a href="https://salilab.org/modeller/manual/node19.html#SECTION:model-changeopt">2.2.2</a> for an example.
                             
</blockquote>

<p>
<br></p><hr>



</body></html>