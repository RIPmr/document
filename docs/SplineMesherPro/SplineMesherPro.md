# SplineMesher Pro

Procedural spline modeling tools.

## 1 New Features
### 1-1 Tree generator

<div align=center><img width="70%" src="_pics/SM_200/Tree.png"/></div>
<center>Tree generator</center>

### 1-2 Automatic LOD

<div align=center><img width="70%" src="_pics/SM_200/lod.png"/></div>

### 1-3 Shape editor

<div align=center><img width="70%" src="_pics/SM_200/shapeEditor_f.png"/></div>
<center>Shape editor</center>

### 1-4 Mesh subdivide

<div align=center><img width="70%" src="_pics/SM_200/Subdiv.png"/></div>
<center>Mesh subdivide</center>

### 1-5 out-of-range displace curve

<div align=center><img width="70%" src="_pics/SM_200/outofrange.png"/></div>
<center>out-of-range displace curve</center>

### 1-6 improved gizmo

<div align=center><img width="70%" src="_pics/SM_200/gizmo_f.png"/></div>
<center>improved gizmo</center>

### 1-7 Support Vertex Format 32

<div align=center><img width="70%" src="_pics/SM_200/format.png"/></div>
<center>Support up to 4 billion vertices</center>

## 2 Getting started
### 2-1 Install SplineMesher
Download and import SplineMesher from Asset Store, and you will see following files:
<div align=center><img width="30%" src="_pics/SM_200/(1).png"/></div>
There are some example scenes in the 'ExampleScenes' folder to help you quickly learn how to use SplineMesher.

### 2-2 Create spline mesh
#### STEP1
First, create an empty gameobject in you scene:
<div align=center><img width="30%" src="_pics/SM/(2).png"/></div>

#### STEP 2
Select your empty gameobject, then search for 'Line Manager' component in the inspector and add the component:
<div align=center><img width="50%" src="_pics/SM/(3).png"/></div>

#### STEP 3
Now you can see the spline in your scene, the white straight lines represents the spline, and the yellow balls represents the vertices (knots) of the spline, and they will inherit the transform of your empty object.
*White circle represents the pivot of the empty object.
<div align=center><img width="50%" src="_pics/SM/(4).png"/></div>

#### STEP 4
You can add new knot to the spline by clicking the '+ knot' button in the inspector. Click any knot (yellow ball) in the scene and you will see the corresponding handle of that knot, then you can edit the spline by using the handle.
<div align=center><img width="80%" src="_pics/SM_200/(5).png"/></div>

#### STEP 5
Tick 'Bezier Curve' and the corner spline will be converted to Cubic Bezier curve, then tick the 'Edit Controller' you will be able to edit the Bezier controllers of each knot. 

Then you can try to tick the 'Tangent Constraint', it means that the two Bezier handles corresponding to the same knot are limited to one straight line (so that they will have same tangent vector, and the spline will keep 'smooth' at the position of that knot).

<div align=center><img width="80%" src="_pics/SM_200/(6).png"/></div>

#### STEP 6
Search for 'Spline Mesher' component in the inspector and add it to your empty gameobject which you have added 'Line Manger' to it before, then you will see a 'strange' pink model appear in your scene:
<div align=center><img width="80%" src="_pics/SM/(7).png"/></div>

#### STEP 7
That's because we haven't added a material to the spline mesh yet. Just add a material to the 'Mesh Renderer' component of the spline, then you will see the correct mesh:
<div align=center><img width="70%" src="_pics/SM/(10).png"/></div>

### 2-3 Shape editor
#### STEP1
Go to the 'Spline Mesher' component, select 'Custom' in 'Contour Type' menu;

#### STEP2
Click the 'Open Shape Editor' button;
<div align=center><img width="80%" src="_pics/SM_200/n1.png"/></div>

#### STEP3
Click the 'Open Shape Editor' button, and the shape editor will open automatically;
<div align=center><img width="80%" src="_pics/SM_200/n2.png"/></div>

<strong>Basic operations:</strong><br>
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Hold middle mouse and move :</strong> drag canvas;<br>
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Hold left mouse and drag :</strong> select points;<br>
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Right click :</strong> open menu or exit edit mode (if in draw mode or insert mode);<br>
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Left click on point :</strong> select point;

<strong>Buttons at the top left of the window:</strong><br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>clear canvas: </strong>clear all points in the window;<br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>draw segments: </strong>start drawing segments, right click to quit drawing;<br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>delete point(s): </strong>delete selected points;<br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>insert point: </strong>insert points to any segment;<br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>snap: </strong>snap mouse to coordinate grid.<br>

!> *NOTE: in current version of shape editor, you should draw the contour shape anticlockwise, otherwise the generated pipe mesh will flip inside and outside.


### 2-4 Automatic LOD
#### STEP1
in current version, automatic LOD only work in 'Bezier Curve' mode, so first you should tick 'Bezier Curve' and the 'Auto LOD' in the 'Line Manager' component;
<div align=center><img width="40%" src="_pics/SM_200/n3.png"/></div>

#### STEP2
'LodDist' represents the distance of each simplified model from the camera:
<div align=center><img width="80%" src="_pics/SM_200/n4.png"/></div>

The maximum subdivision level of the spline is determined by 'Subdiv Range', and the minimum is 1 .

### 2-5 Tree generator
#### STEP1
create an empty gameobject, then add a 'Tree Generator' component to it;
<div align=center><img width="40%" src="_pics/SM_200/n5.png"/></div>

#### STEP2
Assign 'Branch' and 'Leaf' located at 'SplineMesherPro/Resources/Prefabs' to the 'Bark Template' and 'Leaf Template', otherwise you can using your own templates; 
<div align=center><img width="40%" src="_pics/SM_200/n6.png"/></div>

#### STEP3
Run the game, and you will see the generated tree. If tick 'Grow Animation', the generated tree will have growth animation.

!> *NOTE: grow animation is dependent on the new Timeline system of Unity, default animation file path is 'Assets/SplineMesherPro/Examples/Animation', if the path does not exist, an error will occur. You can modify it to a custom path.

!> *NOTE: please note that the generating speed will be significantly slower when 'grow animation' is checked.


## 3 System options
### 3-1 Line Manager component
<div align=center>
<table class=67  border=1  cellspacing=0  style="border-collapse:collapse;width:389.8000pt;mso-table-layout-alt:fixed;
border:none;mso-border-left-alt:0.5000pt solid rgb(175,185,187);mso-border-top-alt:0.5000pt solid rgb(175,185,187);
mso-border-right-alt:0.5000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);mso-border-insideh:0.5000pt solid rgb(175,185,187);
mso-padding-alt:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;" ><tr style="height:27.1000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(122,140,142);
mso-border-left-alt:0.5000pt solid rgb(122,140,142);border-right:none;border-top:1.0000pt solid rgb(122,140,142);
mso-border-top-alt:0.5000pt solid rgb(122,140,142);border-bottom:1.0000pt solid rgb(122,140,142);mso-border-bottom-alt:0.5000pt solid rgb(122,140,142);
background:rgb(122,140,142);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,255,255);
font-weight:bold;font-size:18.0000pt;" >Parameter</span></b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,255,255);font-weight:bold;
font-size:16.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(122,140,142);mso-border-right-alt:0.5000pt solid rgb(122,140,142);border-top:1.0000pt solid rgb(122,140,142);
mso-border-top-alt:0.5000pt solid rgb(122,140,142);border-bottom:1.0000pt solid rgb(122,140,142);mso-border-bottom-alt:0.5000pt solid rgb(122,140,142);
background:rgb(122,140,142);" ><p class=MsoNormal  align=center  style="margin-bottom:0.0000pt;text-align:center;" ><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,255,255);font-weight:bold;
font-size:16.0000pt;" ><o:p>&nbsp;</o:p></span></b></p></td></tr><tr style="height:21.6000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >+ knot / - knot</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Add/delete knot from the spline.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >B</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ezier curve fitting</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Fitting corner type spline data with a Bezier curve based on least-square method.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >A</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >uto LOD</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >E</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >nable automatic LOD.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >L</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >od Dist</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Represents the distance of each simplified model from the camera.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >A</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >uto Gizmo Size</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >K</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >eep the display size of Gizmos (yellow balls) while the distance between spline and camera changes.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >S</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >cale Gizmo</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >C</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >hange size of Gizmos (yellow balls).</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >K</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >not Count</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >It shows the total knot number of the spline, you can change it directly and the spline will be updated in real-time.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';
mso-hansi-font-family:'Calibri Light';mso-bidi-font-family:'Calibri Light';color:rgb(255,0,0);
font-size:10.5000pt;" >* </span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
color:rgb(255,0,0);font-size:10.5000pt;" >minimum knot number is 2</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >K</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >not List</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >I</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >t shows the coordinates of spline knots, you can change it directly in the inspector.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
color:rgb(255,0,0);font-size:10.5000pt;" >* coordinates are shown in local coordinate space</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >B</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ezier Curve</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >T</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >urn it on to convert the corner spline to Cubic Bezier curve.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >Tangent Constraint</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Turn it on and the two Bezier handles corresponding to the same knot will be limited to one straight line.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >Subdiv Range</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >The higher, the smoother the Bezier curve will be. It also determines the maximum level of &#8216;Auto LOD&#8217; subdivision.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
color:rgb(255,0,0);font-size:10.5000pt;" >* maximum smooth level is 255, you can change it in source code of the component</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >Bezier </span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >C</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ontroller List</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >I</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >t shows the coordinates of Bezier controllers, you can change it directly in the inspector.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
color:rgb(255,0,0);font-size:10.5000pt;" >* coordinates are shown in local coordinate space</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr></table>
</div>

### 3-2 Spline Mesher component
<div align=center>
<table class=67  border=1  cellspacing=0  style="border-collapse:collapse;width:389.8000pt;mso-table-layout-alt:fixed;
border:none;mso-border-left-alt:0.5000pt solid rgb(175,185,187);mso-border-top-alt:0.5000pt solid rgb(175,185,187);
mso-border-right-alt:0.5000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);mso-border-insideh:0.5000pt solid rgb(175,185,187);
mso-padding-alt:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;" ><tr style="height:27.1000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(122,140,142);
mso-border-left-alt:0.5000pt solid rgb(122,140,142);border-right:none;border-top:1.0000pt solid rgb(122,140,142);
mso-border-top-alt:0.5000pt solid rgb(122,140,142);border-bottom:1.0000pt solid rgb(122,140,142);mso-border-bottom-alt:0.5000pt solid rgb(122,140,142);
background:rgb(122,140,142);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,255,255);
font-weight:bold;font-size:18.0000pt;" >Parameter</span></b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,255,255);font-weight:bold;
font-size:16.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(122,140,142);mso-border-right-alt:0.5000pt solid rgb(122,140,142);border-top:1.0000pt solid rgb(122,140,142);
mso-border-top-alt:0.5000pt solid rgb(122,140,142);border-bottom:1.0000pt solid rgb(122,140,142);mso-border-bottom-alt:0.5000pt solid rgb(122,140,142);
background:rgb(122,140,142);" ><p class=MsoNormal  align=center  style="margin-bottom:0.0000pt;text-align:center;" ><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,255,255);font-weight:bold;
font-size:16.0000pt;" ><o:p>&nbsp;</o:p></span></b></p></td></tr><tr style="height:21.6000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >Vertex Format 32</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Enable this to support more vertices. (maximum is 4 billion)</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:21.6000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >C</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ontour Type</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';
mso-hansi-font-family:'Calibri Light';mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >3 </span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Types of contour is supported now: Rectangle, Radial and Custom, you can choose one of them here. </span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:21.6000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >S</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ize</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Width and Height of the Rectangle contour.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:21.6000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >S</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ides</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >The number of edges of the Radial contour.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:21.6000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >Radius</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >R</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >adius of the contour if section type is set to Radial.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:21.6000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >Open Shape Editor</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >O</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >pen the shape editor if section type is set to Custom.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >C</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >enter Pivot</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" >T</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';
mso-hansi-font-family:'Calibri Light';mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >urn it on to put pivot of each section to the bottom of the section.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >C</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >orner Correction</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >If the angle between two spline segments is very small, some vertices of the generated tube mesh may erroneously deviate from the mesh. Checking it can largely repair the problem.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >R</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >adius Multiply</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Multiply the radius of the contour if section type is set to Custom.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >Flip</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Flip the normal of side faces of generated tube mesh. (It can be used to create tunnels, etc.)</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >Cap</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Whether cap the top and bottom face of generated tube mesh.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >S</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >mooth</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Switch the display method of the side faces of the tube mesh. If checked, the side will be displayed smoothly.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >R</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >otate</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Taking the spline as axis center to rotate the tube mesh.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >T</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >wist</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >The rotation angle of each segment of tube mesh is multiplied by an adjustment coefficient.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >The closer the segment is to the end of the spline, the greater the adjustment coefficient is.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >G</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >rowth</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Range: [0, 1]. Controlling the growth percentage of the spline mesh.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >G</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >rowth Offset</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Controls the shape of the tip of the spline mesh while growing.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >S</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ubdivide</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';
mso-hansi-font-family:'Calibri Light';mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >Subdivid</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >e the spline mesh.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >S</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ubdivIteration</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >The number of subdivisions per segment of the spline mesh.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >Disp Curve</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Adjust radius of each tube mesh segment by using custom curve. </span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
color:rgb(255,0,0);font-size:10.5000pt;" >* the abscissa of the curve must be between [0,1]</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >D</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >isp Threshold</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >R</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >ange: [0, 181]. Controls the range of the vertices to be displaced in the spline mesh.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
color:rgb(255,0,0);font-size:10.5000pt;" >* As shown in the picture below, vertices with an angle less than the threshold will be displaced:</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,0,0);
font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:Calibri;mso-fareast-font-family:ËÎÌå;mso-bidi-font-family:'Times New Roman';" ><img width="228"  height="241"  src="_pics/SM_200/README_V2.0.0_withFonts8732.png" ></span><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" ><o:p>&nbsp;</o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >Disp Multiply</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >The value of the &#8216;Disp Curve&#8217; will be multiplied by this coefficient.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >O</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ut Of Range</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >E</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >xtends the &#8216;Disp Curve&#8217; automatically.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:Calibri;mso-fareast-font-family:ËÎÌå;mso-bidi-font-family:'Times New Roman';" ><img width="265"  height="172"  src="_pics/SM_200/README_V2.0.0_withFonts8873.png" ></span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p>&nbsp;</o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >R</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >elative</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >W</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >orks with &#8216;Out Of Range&#8217;, Affects the starting point of the extended curve.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >M</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >apping Range</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >For example, if we set it to 100. SplineMesher will mapping the first 100 vertices of the spline mesh to the [0,1] range of the &#8216;Disp Curve&#8217;, the next 100 vertices to (1,2], and so on.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:Calibri;mso-fareast-font-family:ËÎÌå;mso-bidi-font-family:'Times New Roman';" ><img width="310"  height="262"  src="_pics/SM_200/README_V2.0.0_withFonts9162.png" ></span><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" ><o:p>&nbsp;</o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >U</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >V Tile</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';
mso-hansi-font-family:'Calibri Light';mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >UV </span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >tile of generated tube mesh.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >(Cap) </span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >UV </span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >Offset</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';
mso-hansi-font-family:'Calibri Light';mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >UV</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >&nbsp;offset of generated tube mesh.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >C</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ap UV Tile</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >The &#8216;x&#8217; component of &#8216;Cap UV Tile&#8217; is used to rotate the UV of top and bottom faces of tube mesh.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >The &#8216;y&#8217; component of &#8216;Cap UV Tile&#8217; is used to rescale the UV of top and bottom faces of tube mesh. </span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  rowspan=3  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:none;border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >UV Tile Method</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-weight:bold;font-size:10.5000pt;" >&#8216;Simple01&#8217;:</span></b><b><span style="font-family:Calibri;mso-fareast-font-family:ËÎÌå;mso-bidi-font-family:'Times New Roman';
font-weight:bold;" >&nbsp;</span></b><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >The vertex UV of the top position of the spline is set to (0,0), and the vertex UV of the tail is set to (1,1).</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-weight:bold;font-size:10.5000pt;" >&#8216;Edge vertex distance&#8217;:</span></b><span style="font-family:Calibri;mso-fareast-font-family:ËÎÌå;mso-bidi-font-family:'Times New Roman';" >&nbsp;</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >The UV position of the vertex is calculated based on the cumulative distance between each segments of the spline.</span><b><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:10.5000pt;" ><o:p></o:p></span></b></p></td></tr><tr style="height:31.2000pt;" ><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-weight:bold;font-size:10.5000pt;" >&#8216;Projection&#8217;:</span></b><span style="font-family:Calibri;mso-fareast-font-family:ËÎÌå;mso-bidi-font-family:'Times New Roman';" >&nbsp;</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Each triangle of the mesh will firstly be projected into a virtual plane which its normal points, and then the UV is calculated.</span><b><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:10.5000pt;" ><o:p></o:p></span></b></p></td></tr></table>
</div>

### 3-3 Tree generator (experimental)
<div align=center>
<table class=67  border=1  cellspacing=0  style="border-collapse:collapse;width:389.8000pt;mso-table-layout-alt:fixed;
border:none;mso-border-left-alt:0.5000pt solid rgb(175,185,187);mso-border-top-alt:0.5000pt solid rgb(175,185,187);
mso-border-right-alt:0.5000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);mso-border-insideh:0.5000pt solid rgb(175,185,187);
mso-padding-alt:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;" ><tr style="height:27.1000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(122,140,142);
mso-border-left-alt:0.5000pt solid rgb(122,140,142);border-right:none;border-top:1.0000pt solid rgb(122,140,142);
mso-border-top-alt:0.5000pt solid rgb(122,140,142);border-bottom:1.0000pt solid rgb(122,140,142);mso-border-bottom-alt:0.5000pt solid rgb(122,140,142);
background:rgb(122,140,142);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,255,255);
font-weight:bold;font-size:18.0000pt;" >Parameter</span></b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,255,255);font-weight:bold;
font-size:16.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(122,140,142);mso-border-right-alt:0.5000pt solid rgb(122,140,142);border-top:1.0000pt solid rgb(122,140,142);
mso-border-top-alt:0.5000pt solid rgb(122,140,142);border-bottom:1.0000pt solid rgb(122,140,142);mso-border-bottom-alt:0.5000pt solid rgb(122,140,142);
background:rgb(122,140,142);" ><p class=MsoNormal  align=center  style="margin-bottom:0.0000pt;text-align:center;" ><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,255,255);font-weight:bold;
font-size:16.0000pt;" ><o:p>&nbsp;</o:p></span></b></p></td></tr><tr style="height:21.6000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >Grow Animation</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Generating plant growth animation.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
color:rgb(255,0,0);font-size:10.5000pt;" >*please note that the generating speed will be significantly slower when &#8216;grow animation&#8217; is checked.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >Anim File Path</span><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Default grow animation file saving path is:</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >&#8216;Assets/SplineMesherPro/Examples/Animation&#8217;</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >if the path does not exist, an error will occur. </span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >You can modify it to a custom path.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >G</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >enerate Leaf</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >T</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >ick this option to generate leaf.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >B</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ark Template</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Template used for generating tree branch.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >L</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >eaf Template</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >T</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >emplate used for generating tree leaf.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >I</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >nit Radius</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" >I</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';
mso-hansi-font-family:'Calibri Light';mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >nitial </span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >radius (that is, the radius of the trunk of the tree). On this basis, the radius of the branch generated later will be smaller and smaller</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >H</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >eight</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >H</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >eight of the tree.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >M</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ax Depth</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >The maximum branch depth, for example: trunk is level 0, the first layer of branches is level 1.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >M</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ax Knot Num</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >Range of knot number per individual branch.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >B</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ranch Chance</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >R</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >ange: [0.0, 1.0]. The closer the value to 1, the greater the probability is to generating new child branches on each branch knot.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >M</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ax Branch Num</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >The maximum number of child branches generated on each branch knot.</span><span style="font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >B</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >ranch Rotate Range</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >R</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >otate range of child branches.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=179  valign=top  style="width:134.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(175,185,187);
mso-border-left-alt:0.5000pt solid rgb(175,185,187);border-right:none;border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  style="margin-bottom:0.0000pt;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" >L</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;
font-size:12.0000pt;" >eaf Size Range</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=340  valign=top  style="width:255.4000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
border-right:1.0000pt solid rgb(175,185,187);mso-border-right-alt:0.5000pt solid rgb(175,185,187);border-top:none;
mso-border-top-alt:0.5000pt solid rgb(175,185,187);border-bottom:1.0000pt solid rgb(175,185,187);mso-border-bottom-alt:0.5000pt solid rgb(175,185,187);
background:rgb(228,231,232);" ><p class=MsoNormal  align=justify  style="margin-bottom:0.0000pt;mso-pagination:none;text-align:justify;
text-justify:inter-ideograph;" ><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" >S</span><span style="mso-spacerun:'yes';font-family:'Calibri Light';mso-fareast-font-family:'Î¢ÈíÑÅºÚ Light';
font-size:10.5000pt;" >ize range of each leaf.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';mso-ascii-font-family:'Calibri Light';mso-hansi-font-family:'Calibri Light';
mso-bidi-font-family:'Calibri Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr></table>
</div>


## 4 Script examples
### 4-1 Create spline and tube mesh
```C#
	// create empty gameobject
    splineMesh = new GameObject();
    splineMesh.name = "spline mesh";

    // add components to the empty gameobject
    lineMgrComp = splineMesh.AddComponent<LineManager>();
    spMeshComp = splineMesh.AddComponent<SplineMesher>();

    // add knot to spline
    lineMgrComp.knotNum++;

    // *** update is needed ***
    lineMgrComp.ManualUpdate();

    // change position of the knot which we added above
    // get knot list first
    // *** note: the coordinates in knotList obtained by using lineMgrComp.GetLineKnots() is in local space ***
    // *** note: if you need world space coordinates, using knotList = lineMgrComp.GetActualLineKnots(); instead ***
    List<Vector3> knotList = lineMgrComp.GetLineKnots();
    knotList[knotList.Count - 1] = knotList[knotList.Count - 2] + Vector3.up;

    // *** update is needed ***
    lineMgrComp.ManualUpdate();

    // set other parameters of spline mesh
    spMeshComp.UVmethod = UVType.Projection;
    spMeshComp.contourType = ContourType.circle;
    spMeshComp.tubeRadius = 0.5f;
    spMeshComp.sides = 24;

    // assign material to spline mesh
    splineMesh.GetComponent<Renderer>().sharedMaterial = matForMesh;

    // *** update is needed ***
    spMeshComp.ManualUpdate();
```

### 4-2 Code driven spline animation
```C#
	// animating the spline
    List<Vector3> knotList = lineMgrComp.GetLineKnots();

    // check the boundary
    Vector3 move = new Vector3(Random.Range(-1, 2), Random.Range(-1, 2), Random.Range(-1, 2));
    var currPos = knotList[knotList.Count - 1];
    var prevPos = knotList[knotList.Count - 2];
    var newPos = currPos + move;
    if (newPos.x < -moveRange.x || newPos.x > moveRange.x ||
        newPos.y < -moveRange.y || newPos.y > moveRange.y ||
        newPos.z < -moveRange.z || newPos.z > moveRange.z || 
        newPos == prevPos || newPos == currPos) return;

    // each node follows the previous node
    for (int i = 0; i < lineMgrComp.knotNum - 1; i++) knotList[i] = knotList[i + 1];
    knotList[knotList.Count - 1] += move;

    // *** update is needed ***
    // if you have updated the 'LineManager' component, it will update the 'SplineMesher' attached
    // to it automatically, so there's no need to call 'spMeshComp.ManualUpdate();' again here.
    lineMgrComp.ManualUpdate();
```

### 4-3 Using shape editor in custom script
```C#
	// define a bool variable (optional, used to display an 'open shape editor' button on the inspector)
    [InspectorButton("OpenShapeEditor")]
    public bool openShapeEditor;

	// prepare a container for the custom contour shape
    [HideInInspector]
    public List<Vector2> contourCurve = new List<Vector2>();

	// implement the 'OpenShapeEditor' method to open the shape editor
	private void OpenShapeEditor() {
        ShapeEditor.OpenWindow(ref contourCurve);
    }

	// if the shape has been edited, 'ShapeEditor.changed' will set to 'true'
	// *Note: you have to set it back to 'false' manually
	if (ShapeEditor.changed) {
		// do something ...
		ShapeEditor.changed = false;
	}
```

### 4-4 Caculate normal,tangent and bitangent for custom spline
```C#
	// create a list for your spline
    List<Vector3> mySpline = new List<Vector3>();
    mySpline.Add(Vector3.zero);
    mySpline.Add(new Vector3(0, 0, 1));
    mySpline.Add(new Vector3(0, 0, 2));
    mySpline.Add(new Vector3(0, 1, 2));

    // prepare normal, tangent and bitangent list
    List<Vector3> normal = new List<Vector3>();
    List<Vector3> tangent = new List<Vector3>();
    List<Vector3> bitangent = new List<Vector3>();

    // calculate normal, tangent and bitangent for each vertex
    // results will be stored to above lists
    MathUtils.CalcVectors(mySpline, ref normal, ref tangent, ref bitangent);

    // debug result
    foreach (Vector3 vt in normal) Debug.Log(vt);
```

## Support
If you have any questions, comments, or requests for new features, please email me directly at: hztmailbox@gmail.com.

</br>
</br>

Welcome to visit my homepage: https://huanime.com.cn/.