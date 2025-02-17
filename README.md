
</head>
<body bgcolor="#E6E6FA">
<meta charset="utf-8">
<h1>TMM</h1>

<div id="copyright">Developed by Mingtao(Milo) Lu </div>
<br>
Note: program was written in Java 7
<div id="note">

<br>
<br>
The program is based on Transfer Matrix Method. To run the program, installation of JRE is required. However, JDK is not necessary. In the model following assumptions have be made:
<ul>
		<li>The optical stack is placed in air under one sun condition AM1.5. The incident light is a plane wave from the air to "Layer0".</li>
		<li>The interfaces of all the optical layers are 100% flat.</li>
		<li>If light propagates in z-direction (for normal incidence), the dimensions of the optical layers in xy-plane are infinitely large.</li>
		<li>No polarization in optical layers.</li>
		<li>Materials within each layer are isotropic and homogeneous. The optical properties can be described by a dielectric function &#949(&#969) and a magnetic permeability &#956(&#969).</li>
		<li>To start the calculation, more than one wavelength should be provided, as required by the interpolation method.</li>
		<li>At least two different structures should be calculated, as required by the thickness permutation method.</li>
</ul>	
</div>

<h4>version 2.64</h4> 
2014/01/02
<ul>
	<li>A GUI has been added. Optical layers can be added or removed.</li>
	<li>An external library (<a href="http://commons.apache.org/proper/commons-math/"><b>The Apache Commons Mathematics Library</b></a>) is used for handling calculations with complex number and interpolation.</li>
	<li>TM and TE modes are calculated separately. Angle of the incident beam can be set.</li>
	<li>For an incoherent layer the thickness can be set as zero. In that case, there will be no contribution to the phase, only interface matters. However the ART values will NOT be accurate.</li>
	<li>Only power dissipation in <b>active layers</b> will be taken into account. "file0" represents the optical structure with the largest power dissipation in active layers; "file1" the second largest...etc</li>
</ul>

<h4>version 2.65</h4>
2014/05/20
<ul>
	<li>Serialization ID is added.</li>
	<li>A progress bar is added for monitoring the development of the main thread using SwingWorker.</li>
	<li>Further optimize the data structure to reduce the running time</li>
</ul>

<h4>version 2.70</h4>
2014/07/08
<br>
<br>
Two programs are created, <b>TMM 2.70 ART</b> and <b>TMM 2.70 Profile</b>. Results are recorded in two set of txt files. Numbers in the output files are truncated to 5 numbers after the decimal point.
<br>
<h5>TMM 2.70 ART</h5> Detailed information about programming can be found in <a href="TMM 2.70 ART/TMM ART Doc/index.html">TMM ART doc</a> 
<ul>
	<li>The ART of Coherent and incoherent stacks can be calculated (Appl. Phys. B 39, 165-170).</li>
	<li>Coherent and incoherent layers can be in arbitrary order.</li>
</ul>
<h5>TMM 2.70 Profile</h5> Detailed information about programming can be found in <a href="TMM Profile Doc/index.html">TMM Profile doc</a>.
<ul>
	<li>EQE is calculated.</li>
	<li>With one active layer in the system, Jsc can be calculated under the assumption of 100% IQE. A 2D plot with <i>Jsc vs Active Layer Thickness</i> will be generated. In this case, only the thickness of the active layer varies and the thicknesses of all the other layers are fixed to their starting thicknesses.</li>
	<li>An external library (<a href="http://www.jfree.org/jfreechart/"><b>JFreeChart</b></a>) is used for generating the 2D plot.</li>
	<li>In the next version, a 3D plot will be generated if two active layers are chosen.</li>
	<li>If "Calculate Jsc" is chosen, the thickness of all the non-active layers will be set to their "Start Thickness", which is the only thickness for non-active layers.</li>
	<li>Note in principle, T&ne;|t&sup2;|. Here a term like (n1cos&theta;1)/(n0cos&theta;0) is dropped, because both of the front and the back interfaces of the entire stack are in touch with the same medium, air. Also, when calculating TAB*TBA, this term cancels itself.</li>
</ul>

<h4>version 2.71</h4>
2014/09/23
<ul>
	<li>To avoid "magic numbers", Complex.ONE is replaced by a constant variable N_Air.</li>
	<li>The declaration of <i>angle</i> is changed from "Complex" to "double".</li>
	<li>s- and p-polarized light are separated in the incoherent matrix too, i.e., matrix related to Rs, Ts and Rp, Tp are processed independently through the entire stack before calculating Rtotal and Ttotal.</li>
	<li>The layer matrix for incoherent calculation is modified. Transmission in two directions (TAB & TBA) are separated. For coherent stacks, this is accomplished by calculating matrix in reversed order. Incoherent stack contains only one layer, which simplifies the scenario. Reflections are not separated, since RAB and RBA are same.</li>
</ul>

<h4>version 2.72</h4>
2014/11/04
<ul>
	<li><i>angle</i> is changed back to "Complex". The physical meaning of a complex angle of refraction can be found in <i>Thin Film Optics and Polarized Light</i> &#151 Hans Arwin</li>
	<li>Results under normal incidence are verified using <a href="http://web.stanford.edu/group/fan/S4/"><b>S4</b></a>.</li>
	<li>For oblique incidence, calculations of the electric field for s- and p-polarized light are to be updated.</li>
	<br>
	Things to be done:
	<li>In TMM 2.72 Profile, a GUI related bug need to be fixed. After the first run of the program, the JScrollPane should be updated with the correct format.</li>
	<li>Permutation of different thickness combinations is generated through recursion. When dealing with only one thickness set, special treatment is required for the calculation to proceed.</li>
</ul>
</body></html>
