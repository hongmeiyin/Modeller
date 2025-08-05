<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<!--Converted with LaTeX2HTML 2018.2 (Released May 16, 2018) -->
<html><head>
<title>AutoModel.rand_method — control initial model randomization</title>
<meta name="description" content="AutoModel.rand_method — control initial model randomization">
<meta name="keywords" content="manual">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">

<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<meta name="Generator" content="LaTeX2HTML v2018.2">
<meta http-equiv="Content-Style-Type" content="text/css">

<link rel="STYLESHEET" href="AutoModel.rand_method%20%E2%80%94%20control%20initial%20model%20randomization_files/manual.css">
<link rel="STYLESHEET" href="AutoModel.rand_method%20%E2%80%94%20control%20initial%20model%20randomization_files/pygments.css">

<link rel="next" href="https://salilab.org/modeller/manual/node49.html">
<link rel="previous" href="https://salilab.org/modeller/manual/node47.html">
<link rel="up" href="https://salilab.org/modeller/manual/node43.html">
<link rel="next" href="https://salilab.org/modeller/manual/node49.html">
</head>

<body>

<div class="navigation"><!--Navigation Panel-->
<a name="tex2html2197" href="https://salilab.org/modeller/manual/node49.html">
<img width="37" height="24" align="BOTTOM" border="0" alt="next" src="AutoModel.rand_method%20%E2%80%94%20control%20initial%20model%20randomization_files/next.png"></a> 
<a name="tex2html2191" href="https://salilab.org/modeller/manual/node43.html">
<img width="26" height="24" align="BOTTOM" border="0" alt="up" src="AutoModel.rand_method%20%E2%80%94%20control%20initial%20model%20randomization_files/up.png"></a> 
<a name="tex2html2185" href="https://salilab.org/modeller/manual/node47.html">
<img width="63" height="24" align="BOTTOM" border="0" alt="previous" src="AutoModel.rand_method%20%E2%80%94%20control%20initial%20model%20randomization_files/prev.png"></a> 
<a name="tex2html2193" href="https://salilab.org/modeller/manual/node1.html">
<img width="65" height="24" align="BOTTOM" border="0" alt="contents" src="AutoModel.rand_method%20%E2%80%94%20control%20initial%20model%20randomization_files/contents.png"></a> 
<a name="tex2html2195" href="https://salilab.org/modeller/manual/node518.html">
<img width="43" height="24" align="BOTTOM" border="0" alt="index" src="AutoModel.rand_method%20%E2%80%94%20control%20initial%20model%20randomization_files/index.png"></a> 
<br>
<b> Next:</b> <a name="tex2html2198" href="https://salilab.org/modeller/manual/node49.html">AutoModel.generate_method   control</a>
<b> Up:</b> <a name="tex2html2192" href="https://salilab.org/modeller/manual/node43.html">AutoModel reference</a>
<b> Previous:</b> <a name="tex2html2186" href="https://salilab.org/modeller/manual/node47.html">AutoModel.outputs   all</a>
 &nbsp; <b>  <a name="tex2html2194" href="https://salilab.org/modeller/manual/node1.html">Contents</a></b> 
 &nbsp; <b>  <a name="tex2html2196" href="https://salilab.org/modeller/manual/node518.html">Index</a></b> 
<br>
<br></div>
<!--End of Navigation Panel-->

<h2><a name="SECTION00915000000000000000">
AutoModel.rand_method — control initial model randomization</a>
</h2> <a name="6128"></a><a name="MEMB:AutoModel.randmethod"></a><blockquote>
This is used to randomize the initial model before producing
each final model. If set to <tt>None</tt> then no randomization is done, and every
model will be the same. You can set it to one of the functions in the
<tt>randomize</tt> module — <tt>randomize.xyz</tt> (the default) to randomize all
coordinates of standard residues, or <tt>randomize.dihedrals</tt> to randomize
dihedral angles. (The amount of randomization carried out by these two
functions can be tuned by changing <i class="sans"><a href="https://salilab.org/modeller/manual/node44.html#MEMB:AutoModel.deviation">AutoModel.deviation</a></i><a name="6146"></a>.)
Finally, you could provide your own Python function; see the <tt>randomize</tt>
module in <tt>modlib/modeller/automodel/randomize.py</tt> for examples to get you
started.
                             
</blockquote>

<p>
<br></p><hr>



</body></html>