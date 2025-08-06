<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html><head>
<link href="Tutorial_advanced_files/modeller.css" rel="stylesheet" type="text/css">
<link rel="canonical" href="https://salilab.org/modeller/tutorial/advanced.html">
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<script type="text/javascript" src="Tutorial_advanced_files/modeller.js"></script>
<script type="text/javascript" src="Tutorial_advanced_files/escramble-new.js"></script>
<title>Tutorial</title>
</head>

<body>

<!-- Auto-generated file: do not edit (any changes will be lost) -->

<div class="rightlink">
<a class="salilab" title="To main Sali lab pages" href="https://salilab.org/">
<img src="Tutorial_advanced_files/salilab.png" alt="To main Sali lab pages"></a>

<a class="mobilemenu" title="Mobile menu" href="#" onclick="show_menu(); return false;">
<img src="Tutorial_advanced_files/mobilemenu.png" alt="Mobile menu"></a></div>

<div class="modheader">
</div>

<div class="blayout">
<div class="lbar">
<ul class="menu">
<li class="menu"><a href="https://salilab.org/modeller/">About MODELLER</a></li>
<li class="menu"><a href="https://salilab.org/modeller/news.html">MODELLER News</a></li>
<li class="menu"><a href="https://salilab.org/modeller/download_installation.html">Download &amp; Installation</a></li>
<li class="submenu"><a href="https://salilab.org/modeller/release.html">Release Notes</a></li>
<li class="submenu"><a href="https://salilab.org/modeller/supplemental.html">Data file downloads</a></li>
<li class="menu"><a href="https://salilab.org/modeller/registration.html">Registration</a></li>
<li class="submenu"><a href="https://salilab.org/modeller/nonacademic.html">Non-academic use</a></li>
<li class="menu"><a href="https://salilab.org/modeller/discussion_forum.html">Discussion Forum</a></li>
<li class="submenu"><a href="https://salilab.org/mm/postorius/lists/modeller_usage.salilab.org/">Subscribe</a></li>
<li class="submenu"><a href="https://salilab.org/mm/hyperkitty/list/modeller_usage@salilab.org/latest">Archives</a></li>
<li class="menu"><a class="this" href="https://salilab.org/modeller/documentation.html">Documentation</a></li>
<li class="submenu"><a href="https://salilab.org/modeller/FAQ.html">FAQ</a></li>
<li class="submenu"><a href="https://salilab.org/modeller/tutorial/">Tutorial</a></li>
<li class="submenu"><a href="https://salilab.org/modeller/manual/">Online manual</a></li>
<li class="submenu"><a href="https://salilab.org/modeller/wiki/">Wiki</a></li>
<li class="menu"><a href="https://salilab.org/modeller/developers_pages1.html">Developers' Pages</a></li>
<li class="menu"><a href="https://salilab.org/modeller/contact.html">Contact Us</a></li>
</ul>

</div>
<div class="main">

<h1>Tutorial</h1>
<hr>

<h2>Advanced example:<br>
Modeling of a protein-ligand complex based on multiple templates, loop
refinement and user specified restraints.</h2>

<p><i>All input and output files for this example are available to download,
in either <a href="https://salilab.org/modeller/tutorial/advanced-example.zip">zip format (for Windows)</a> or
<a href="https://salilab.org/modeller/tutorial/advanced-example.tar.gz">.tar.gz format (for Unix/Linux)</a>.</i></p>

<p><i>For this example we will not describe step-by-step all <span class="progs">MODELLER</span>
commands. Please, refer to the basic-example in the tutorial for more details.</i></p>

<p>An important aim of modeling is to contribute to understanding of the
function of the modeled protein. Inspection of the
<span class="pdb">1bdm:A</span> template structure (built in the
<a href="https://salilab.org/modeller/tutorial/basic.html">basic modeling tutorial</a>) revealed that loop 93-100,
one of the functionally most important parts of the enzyme, is disordered
and does not appear in the PDB structure. Most probably the long active site loop is flexible
in the absence of a ligand and could not be seen in the diffraction map.
The unreliability of the template coordinates and the inability of
<span class="progs">MODELLER</span> to model long insertions is why this loop
was poorly modeled in TvLDH, as indicated by
the DOPE profile. </p>

<p class="centerimg">
<img class="centerimg" src="Tutorial_advanced_files/basic_model.png" alt="DOPE score profile">
</p>

<p class="smallfilename">DOPE score profile for model TvLDH.B99990001</p>

<p>Since we are interested in understanding differences in specificity between
two similar proteins, we need to build precise and accurate models. Therefore, 
we need to find new strategies to increase the accuracy of the models. 
In this example, we will explore three different approaches:     
</p>

<ul>
<li>Use of multiple templates.</li>
<li>Modeling the loop using <em>ab-initio</em> methods.</li>
<li>Modeling using a known ligand bound to the binding site.</li>
</ul>

<h3>Multiple templates</h3>

<p>The structure of the Malate Dehydrogenase <span class="pdb">1bdm</span>
has been clustered in the <a href="https://salilab.org/DBAli/">DBAli database</a>
within the family <a href="https://salilab.org/DBAli/?page=search&amp;action=s_chainmsa&amp;form=f_chainmsa&amp;chain=1bdmA">fm00495</a> of 4 
members (<span class="pdb">2mdh:A, 2mdh:B. 1b8p:A</span> and 
<span class="pdb">1bdm:A</span>). The multiple alignment generated by the command
<strong>salign()</strong> in <span class="progs">MODELLER</span> is used in DBAli 
to generate a multiple structure alignment of the family. The alignment can be 
downloaded from the DBAli database or you can use the file 
`<span class="filename">salign.py</span>' to calculate it on your computer.</p>

<pre class="filecontent"># Illustrates the SALIGN multiple structure/sequence alignment

from modeller import *

log.verbose()
env = Environ()
env.io.atom_files_directory = ['.', '../atom_files/']

aln = Alignment(env)
for (code, chain) in (('2mdh', 'A'), ('1bdm', 'A'), ('1b8p', 'A')):
    mdl = Model(env, file=code, model_segment=('FIRST:'+chain, 'LAST:'+chain))
    aln.append_model(mdl, atom_files=code, align_codes=code+chain)

for (weights, write_fit, whole) in (((1., 0., 0., 0., 1., 0.), False, True),
                                    ((1., 0.5, 1., 1., 1., 0.), False, True),
                                    ((1., 1., 1., 1., 1., 0.), True, False)):
    aln.salign(rms_cutoff=3.5, normalize_pp_scores=False,
               rr_file='$(LIB)/as1.sim.mat', overhang=30,
               gap_penalties_1d=(-450, -50),
               gap_penalties_3d=(0, 3), gap_gap_score=0, gap_residue_score=0,
               dendrogram_file='fm00495.tree',
               alignment_type='tree', # If 'progresive', the tree is not
                                      # computed and all structues will be
                                      # aligned sequentially to the first
               feature_weights=weights, # For a multiple sequence alignment only
                                        # the first feature needs to be non-zero
               improve_alignment=True, fit=True, write_fit=write_fit,
               write_whole_pdb=whole, output='ALIGNMENT QUALITY')

aln.write(file='fm00495.pap', alignment_format='PAP')
aln.write(file='fm00495.ali', alignment_format='PIR')

aln.salign(rms_cutoff=1.0, normalize_pp_scores=False,
           rr_file='$(LIB)/as1.sim.mat', overhang=30,
           gap_penalties_1d=(-450, -50), gap_penalties_3d=(0, 3),
           gap_gap_score=0, gap_residue_score=0, dendrogram_file='1is3A.tree',
           alignment_type='progressive', feature_weights=[0]*6,
           improve_alignment=False, fit=False, write_fit=True,
           write_whole_pdb=False, output='QUALITY')

</pre>
<p class="smallfilename">File: multiple_template/salign.py</p>

<p>The reads in all of the sequences from PDB files (using the
<strong>append_model</strong> command), and then uses <strong>salign</strong>
multiple times, to generate an initial rough alignment and then improve upon
it by using more information. The alignment is then written out in both PIR
and PAP formats, and a quality score is calculated by calling
<strong>salign</strong> one more time.</p>

<p>After inspecting the multiple structure alignment it is evident that chain B
of <span class="pdb">2mdh</span> contains an unusual number of LYS residues.
The HEADER of the PDB file indicates that the sequence of the protein was
unknown at the time of refinement and it was difficult to identify most of the
residues in the structure. Therefore, the <span class="pdb">2mdh:B</span> entry
was removed from the multiple structure alignment.</p>

<pre class="filecontent"> _aln.pos         10        20        30        40        50        60
2mdhA     GSMQIRVLVTG-AAQLAFTLLYSIGDGSVFGKNQPILLSLMDVVP--KQQTSEAVNMQLQNCALP-LL 
1bdmA     MKAPVRVAVTGAAGQIGYSLLFRIAAGEMLGKDQPVILQLLEIPQ--AMKALEGVVMELEDCAFPLLA 
1b8pA     -KTPMRVAVTGAAGQICYSLLFRIANGDMLGKDQPVILQLLEIPNEKAQKALQGVMMEIDDCAFPLLA 
 _consrvd      ** *** * *    **  *  *   ** **  * *              * *    ** * *

 _aln.p   70        80        90       100       110       120       130
2mdhA     KSQFGKNSGN-YASQNVGVLLAGQRAKNAAKN---LKANVKIFKCQGAALNKYWKKSVIVIVVGNPAT 
1bdmA     GLEATDDPDVAFKDADYALLVGAAPR---------LQVNGKIFTEQGRALAEVAKKDVKVLVVGNPAN 
1b8pA     GMTAHADPMTAFKDADVALLVGARPRGPGMERKDLLEANAQIFTVQGKAIDAVASRNIKVLVVGNPAN 
 _consrvd                    *               *  *  **  ** *          * ******

 _aln.pos  140       150       160       170       180       190       200
2mdhA     NNCLTASKNSAQLNKAKQVNSVKLNHNRAKSMLSQKLGNSPKLSKNVILYGQHGQSQFSGLIQLQLQN 
1bdmA     TNALIAYKNAPGLNPRNFTAMTRLDHNRAKAQLAKKTGTGVDRIRRMTVWGNHSSIMFPDLFHAEVD- 
1b8pA     TNAYIAMKSAPSLPAKNFTAMLRLDHNRALSQIAAKTGKPVSSIEKLFVWGNHSPTMYADYRYAQID- 
 _consrvd  *   * *    *          * ****      * *            * *

 _aln.pos    210       220       230       240       250       260       270
2mdhA     KQSAGVR-ASKNQSWKTSIYNNVIQQRGVVHVQARTANNSMKTGFALNLYVKHLWKGISQ-KLAQMGL 
1bdmA     --GRPALELV-DMEWYEKVFIPTVAQRGAAIIQARGASSAASAANAAIEHIRDWALGTPEGDWVSMAV 
1b8pA     --GASVKDMINDDAWNRDTFLPTVGKRGAAIIDARGVSSAASAANAAIDHIHDWVLGTAG-KWTTMGI 
 _consrvd               *           **     **          *          *        *

 _aln.pos      280       290       300       310       320       330
2mdhA     IAHGKAAASPKQNFSCVTRLQNKTWKIVEGLPINDFSREKMNETAKELAEEETEFAEKNSNA 
1bdmA     PSQGEYGIPEGIVYSFPVTAKDGAYRVVEGLEINEFARKRMEITAQELLDEMEQVKALGLI- 
1b8pA     PSDGSYGIPEGVIFGFPVTTENGEYKIVQGLSIDAFSQERINVTLNELLEEQNGVQ-HLLG- 
 _consrvd    *                       * ** *  *       *  **  *
</pre>
<p class="smallfilename">File: multiple_template/fm00495.pap</p>

<p>As for the basic example in the tutorial, next we need to align our query
sequence to the template structures. For that task we again use the
<strong>salign()</strong> command (file
`<span class="filename">align2d_mult.py</span>').
We set the <strong>align_block</strong> parameter to equal the number of
structures in the template alignment, len(aln), (i.e. 3), and request a
pairwise alignment, since we do not want to change the existing alignment
between the templates. By setting <strong>gap_function</strong> we request
the use of a structure-dependent gap penalty, using structural information for
these 3 sequences. Only sequence information is used for the final TvLDH
sequence.</p>

<pre class="filecontent">from modeller import *

log.verbose()
env = Environ()

env.libs.topology.read(file='$(LIB)/top_heav.lib')

# Read aligned structure(s):
aln = Alignment(env)
aln.append(file='fm00495.ali', align_codes='all')
aln_block = len(aln)

# Read aligned sequence(s):
aln.append(file='TvLDH.ali', align_codes='TvLDH')

# Structure sensitive variable gap penalty sequence-sequence alignment:
aln.salign(output='', max_gap_length=20,
           gap_function=True,   # to use structure-dependent gap penalty
           alignment_type='PAIRWISE', align_block=aln_block,
           feature_weights=(1., 0., 0., 0., 0., 0.), overhang=0,
           gap_penalties_1d=(-450, 0),
           gap_penalties_2d=(0.35, 1.2, 0.9, 1.2, 0.6, 8.6, 1.2, 0., 0.),
           similarity_flag=True)

aln.write(file='TvLDH-mult.ali', alignment_format='PIR')
aln.write(file='TvLDH-mult.pap', alignment_format='PAP')
</pre>
<p class="smallfilename">File: multiple_template/align2d_mult.py</p>

<p>Next, we build the new model for the TvLDH target sequence based on the
alignment against the multiple templates using the
`<span class="filename">model_mult.py</span>' file:</p>

<pre class="filecontent">from modeller import *
from modeller.automodel import *

env = Environ()
a = AutoModel(env, alnfile='TvLDH-mult.ali',
              knowns=('1bdmA','2mdhA','1b8pA'), sequence='TvLDH')
a.starting_model = 1
a.ending_model = 5
a.make()
</pre>
<p class="smallfilename">File: multiple_template/model_mult.py</p>

<p>Finally, we use the DOPE potential to evaluate the new model coordinates using the `<span class="filename">evaluate_model.py</span>' file:</p>

<pre class="filecontent">from modeller import *
from modeller.scripts import complete_pdb

log.verbose()    # request verbose output
env = Environ()
env.libs.topology.read(file='$(LIB)/top_heav.lib') # read topology
env.libs.parameters.read(file='$(LIB)/par.lib') # read parameters

# read model file
mdl = complete_pdb(env, 'TvLDH.B99990001.pdb')

# Assess all atoms with DOPE:
s = Selection(mdl)
s.assess_dope(output='ENERGY_PROFILE NO_REPORT', file='TvLDH.profile',
              normalize_profile=True, smoothing_window=15)
</pre>
<p class="smallfilename">File: multiple_template/evaluate_model.py</p>

<p>The evaluation of the model indicates that the problematic loop (residues 90
to 100) has improved by using multiple structural templates. The global DOPE
score for the models also improved from -38999.7 to -39164.4.
<span class="progs">MODELLER</span> was able to use the variability in the
loop region from the three templates to generate a more accurate conformation
of the loop. However, the conformation of a loop in the region around the
residue 275 at the C-terminal end of the sequence has higher DOPE score than
for the model based on a single template.</p>

<p class="centerimg">
<img class="centerimg" src="Tutorial_advanced_files/multiple_templates.png" alt="DOPE score profile">
</p>
<p class="smallfilename">DOPE score profile for model TvLDH.B99990001.pdb</p>

<p> We will use the <strong>LoopModel</strong> class in
<span class="progs">MODELLER</span> to refine the conformation of the loop
between residues 273 and 283 (in the A chain).
We will use the model number 1 created in the
previous example as a starting structure to refine the loop. You can find this
structure renamed as `<span class="filename">TvLDH-mult.pdb</span>' in the
<tt>loop_modeling</tt> subdirectory.</p>

<h3>Loop refining</h3>

The loop optimization method relies on a scoring function and optimization schedule 
adapted for loop modeling. It is used automatically to refine comparative models if 
you use the <strong>LoopModel</strong> class rather than <strong>AutoModel</strong>; 
see the example below.

<pre class="filecontent"># Loop refinement of an existing model
from modeller import *
from modeller.automodel import *

log.verbose()
env = Environ()

# directories for input atom files
env.io.atom_files_directory = ['.', '../atom_files']

# Create a new class based on 'LoopModel' so that we can redefine
# select_loop_atoms (necessary)
class MyLoop(LoopModel):
    # This routine picks the residues to be refined by loop modeling
    def select_loop_atoms(self):
        # 10 residue insertion 
        return Selection(self.residue_range('273:A', '283:A'))

m = MyLoop(env,
           inimodel='TvLDH-mult.pdb', # initial model of the target
           sequence='TvLDH')          # code of the target

m.loop.starting_model= 1           # index of the first loop model 
m.loop.ending_model  = 10          # index of the last loop model
m.loop.md_level = refine.very_fast # loop refinement method; this yields
                                   # models quickly but of low quality;
                                   # use refine.slow for better models

m.make()

</pre>
<p class="smallfilename">File: loop_modeling/loop_refine.py</p>

<p>In this example, the <strong>LoopModel</strong> class is used to refine a
region of an existing coordinate file. Note that this example also redefines
the <strong>LoopModel.select_loop_atoms</strong> routine. This is necessary in
this case, as the default selection selects all gaps in the alignment for
refinement, and in this case no alignment is available. You can still redefine
the routine, even if you do have an alignment, if you want to select a
different region for
optimization. Note that for the sake of time, we will be building only 10
different independently optimized loop conformations by setting the
<strong>loop.ending_model</strong> parameter to 10. The next image shows the
superimposition of the 10 conformations of the loop modeling. In blue, green
and red we have marked the initial, best and worst loop
conformations as scored by DOPE, respectively.</p>

<p class="centerimg">
<img class="centerimg" src="Tutorial_advanced_files/superposed_loops.png" alt="Loop refinement">
</p>
<p class="smallfilename">Superimposition of all 10 calculated loop conformations rendered by Chimera.</p>

<p>The file `<span class="filename">model_energies.py</span>' computes the 
DOPE score for all built models by using a Python <em>for</em> loop. The best
energy loop corresponds to the 8th model
(file: `<span class="filename">model_energies.py</span>') with
a global DOPE score of -39099.1. Its energy profile calculated by
`<span class="filename">evaluate_model.py</span>' is shown next.

</p><p class="centerimg">
<img class="centerimg" src="Tutorial_advanced_files/loop_refinement.png" alt="DOPE score profile">
</p>
<p class="smallfilename">DOPE score profile for model TvLDH.BL00080001.pdb</p>

<p>There is only a very small increase of global DOPE score by <em>ab-initio</em> refinement of the loop.
However, there is a small decrease in the DOPE score in the region of the loop. Therefore, we 
will continue the next step using the best refined structure (file: `<span class="filename">TvLDH.BL00080001.pdb</span>'), which is renamed in the <em>ligand</em> directory as
`<span class="filename">TvLDH-loop.pdb</span>'. It is important to note that a most accurate approach to
loop refinement requires the modeling of hundreds of independent conformations and their clustering to
select the most representative structures of the loop.</p>

<h3>Modeling ligands in the binding site</h3>
 
<p><span class="pdb">1emd</span>, a malate dehydrogenase from <em>E. coli</em>,
was identified in PDB. While the <span class="pdb">1emd</span> sequence shares
only 32% sequence identity with TvLDH, the active site loop and its environment
are more conserved. The loop for residues 90 to 100 in the <span class="pdb">1emd</span> 
structure is well resolved. Moreover, <span class="pdb">1emd</span> was solved in the
presence of a citrate substrate analog and the NADH cofactor. The new alignment
in the PAP format is shown below (file
`<span class="filename">TvLDH-1emd_bs.pap</span>').</p>

<pre class="filecontent"> _aln.pos            10        20        30        40        50        60
TvLDH        MSEAAHVLITGAAGQIGYILSHWIASGELYGDRQVYLHLLDIPPAMNRLTALTMELEDCAFPHLA 
TvLDH_model  MSEAAHVLITGAAGQIGYILSHWIASGELYGDRQVYLHLLDIPPAMNRLTALTMELEDCAFPHLA 
1emd         ----------------------------------------------------------------- 
 _consrvd


 _aln.pos       70        80        90       100       110       120       130
TvLDH        GFVATTDPKAAFKDIDCAFLVASMPLKPGQVRADLISSNSVIFKNTGEYLSKWAKPSVKVLVIGN 
TvLDH_model  GFVATTDPKAAFKDIDCAFLVASMPLKPGQVRADLISSNSVIFKNTGEYLSKWAKPSVKVLVIGN 
1emd         ----------------------GVRRKPGMDRSDLFNVN-------------------------- 
 _consrvd                              ***  * **   *


 _aln.pos           140       150       160       170       180       190
TvLDH        PDNTNCEIAMLHAKNLKPENFSSLSMLDQNRAYYEVASKLGVDVKDVHDIIVWGNHGESMVADLT 
TvLDH_model  PDNTNCEIAMLHAKNLKPENFSSLSMLDQNRAYYEVASKLGVDVKDVHDIIVWGNHGESMVADLT 
1emd         ----------------------------------------------------------------- 
 _consrvd


 _aln.pos      200       210       220       230       240       250       260
TvLDH        QATFTKEGKTQKVVDVLDHDYVFDTFFKKIGHRAWDILEHRGFTSAASPTKAAIQHMKAWLFGTA 
TvLDH_model  QATFTKEGKTQKVVDVLDHDYVFDTFFKKIGHRAWDILEHRGFTSAASPTKAAIQHMKAWLFGTA 
1emd         ----------------------------------------------------------------- 
 _consrvd


 _aln.pos           270       280       290       300       310       320
TvLDH        PGEVLSMGIPVPEGNPYGIKPGVVFSFPCNVDKEGKIHVVEGFKVNDWLREKLDFTEKDLFHEKE 
TvLDH_model  PGEVLSMGIPVPEGNPYGIKPGVVFSFPCNVDKEGKIHVVEGFKVNDWLREKLDFTEKDLFHEKE 
1emd         ----------------------------------------------------------------- 
 _consrvd


 _aln.pos      330
TvLDH        IALNHLAQGG/.. 
TvLDH_model  IALNHLAQGG/-- 
1emd         ----------/.. 
 _consrvd
</pre>
<p class="smallfilename">File: ligand/TvLDH-1emd_bs.pap</p>

<p>The modified alignment refers to an edited <span class="pdb">1emd</span>
structure (<span class="pdb">1emd_bs</span>), as a second template. The
alignment corresponds to a model that is based on <span class="pdb">1emd_bs</span> 
in its active site loop and on <span class="pdb">TvLDH_model</span>, which
corresponds to the best model from the previous step, in the rest of the fold. 
Four residues on both sides of the active site loop are aligned with both templates to 
ensure that the loop has a good orientation relative to the rest of the model.</p>

<p>The modeling script below has several changes with respect to
`<span class="filename">model-single.py</span>'. First, the name of the
alignment file assigned to <strong>alnfile</strong> is updated. Next, the
variable <strong>knowns</strong> is redefined to include both templates.
Another change is an addition of the `<strong>env.io.hetatm = True</strong>'
command to allow reading of the non-standard pyruvate and NADH residues from
the input PDB files. The script is shown next (file
`<span class="filename">model-multiple-hetero.py</span>').</p>

<pre class="filecontent">from modeller import *
from modeller.automodel import *

class MyModel(AutoModel):
    def special_restraints(self, aln):
        rsr = self.restraints
        for ids in (('NH1:161:A', 'O1A:336:B'),
                    ('NH2:161:A', 'O1B:336:B'),
                    ('NE2:186:A', 'O2:336:B')):
            atoms = [self.atoms[i] for i in ids]
            rsr.add(forms.UpperBound(group=physical.upper_distance,
                                     feature=features.Distance(*atoms),
                                     mean=3.5, stdev=0.1))

env = Environ()
env.io.hetatm = True
a = MyModel(env, alnfile='TvLDH-1emd_bs.ali',
              knowns=('TvLDH_model','1emd'), sequence='TvLDH')
a.starting_model = 1
a.ending_model = 5
a.make()
</pre>
<p class="smallfilename">File: ligand/model-multiple-hetero.py</p>

<p>A ligand can be included in a model in two ways by
<span class="progs">MODELLER</span>. The first case corresponds to the ligand
that is not present in the template structure, but is defined in the
<span class="progs">MODELLER</span> residue topology library. Such ligands
include water molecules, metal ions, nucleotides, heme groups, and many other
ligands (see <a href="https://salilab.org/modeller/10.0/FAQ.html#8">question 8</a> in the
the <span class="progs">MODELLER</span> FAQ). This situation is not explored
further here. The second case
corresponds to the ligand that is already present in the template structure. We
can assume either that the ligand interacts similarly with the target and the
template, in which case we can rely on <span class="progs">MODELLER</span> to
extract and satisfy distance restraints automatically, or that the relative
orientation is not necessarily conserved, in which case the user needs to
supply restraints on the relative orientation of the ligand and the target (the
conformation of the ligand is assumed to be rigid). The two cases are
illustrated by the NADH cofactor and pyruvate modeling, respectively. Both NADH
and cofactor are indicated by the `.' characters at the end of each sequence in
the alignment file above (the `/' character indicates a chain break). In
general, the `.' character in <span class="progs">MODELLER</span> indicates an
arbitrary generic residue called a ``block'' residue (for details see the
<a href="https://salilab.org/modeller/10.0/manual/node107.html#SECTION:block">section on block
residues</a> in the <span class="progs">MODELLER</span> manual). Note that the
`.' characters are present <b>both</b> in <b>one</b> of the template structures
and in the model sequence. The former tells <span class="progs">MODELLER</span>
to read the ligands from the template, and the latter tells it to include the
ligands in the model. The <span class="pdb">1emd</span> structure file
contains a citrate substrate analog. To obtain a model with pyruvate, the
physiological substrate of TvLDH, we convert the citrate analog in
<span class="pdb">1emd</span> into pyruvate by deleting the group
CH(COOH)<span class="style2">2</span>, thus obtaining the
<span class="pdb">1emd_bs</span> template file. A major advantage of using the
`.' characters is that it is not necessary to define the residue topology.</p>

<p>To obtain the restraints on pyruvate, we first superpose the structures of
several LDH and MDH enzymes solved with ligands. Such a comparison allows us to
identify absolutely conserved electrostatic interactions involving catalytic
residues Arg161 and His186 on one hand, and the oxo groups of the lactate and
malate ligands on the other hand. The modeling script can now be expanded by
creating a new class 'MyModel', which is derived from <strong>AutoModel</strong>
but which differs in one important respect: the
<strong>special_restraints</strong> routine is redefined to add, to the
default restraints, some user defined distance restraints between the
conserved atoms of the active site residues and their substrate. In this case,
a harmonic upper bound restraint of 3.5±0.1Å is imposed on the
distances between the three specified pairs of atoms. A trick is used to prevent
<span class="progs">MODELLER</span> from automatically calculating distance
restraints on the pyruvate-TvLDH complex; the ligand in the
<span class="pdb">1emd_bs</span> template is moved beyond the upper bound on
the ligand-protein distance restraints (i.e., 10).</p>

<p>The final selected model (shown in the ribbons image below) has a DOPE global
score of -37640.9. The DOPE score is increased due to the new interactions of the
protein with the ligand that are not accounted when calculating the DOPE score.</p>

<p class="centerimg">
<img class="centerimg" src="Tutorial_advanced_files/ligand_modeling.png" alt="DOPE score profile">
</p>
<p class="smallfilename">Final model with NAD and LAC ligands in the binding site rendered by Chimera.</p>


</div></div>

<div class="copyright">
<p><a class="ucsflogo" href="https://www.ucsf.edu/"><img src="Tutorial_advanced_files/ucsf-logo.png" alt="UCSF Logo"></a>
MODELLER (copyright © 1989-2025 Andrej Sali) is
maintained by <a href="https://salilab.org/modeller/contact.html">Ben Webb</a>
at the Departments of Biopharmaceutical Sciences and Pharmaceutical Chemistry,
and California Institute for Quantitative Biomedical Research, Mission Bay
Byers Hall, University of California San Francisco, San Francisco,
CA 94143, USA.
Any selling or distribution of the program or its parts, original or modified,
is prohibited without a written permission from Andrej Sali.
This file last modified: Wed Feb 10 12:01:19 PST 2021.</p>
</div>


</body></html>