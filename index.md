<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
	<link
  rel="stylesheet"
  href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css"
  integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh"
  crossorigin="anonymous"
  >
<title>HTML & CSS & JavaScript</title>
</head>
<body onload="Carousel(),initaec();" bgcolor="#FFFFFF">
	<center>
		<div style="border-style: inset;
  border-left: 20px solid #0374C3;
  background-color: #D9DFE3; border-radius: 20px;">
	<p class="tt" style="font-size: 50px "><b>HTML ET CSS ET JAVASCRIPT</b></p>
<b><h1><a href="index.html" class="aec">Lien cliquable - http://www.devschool.com</a></h1></b>
</div>
</center>
<div id="Carousel" style="position:relative;">
		<img src="img/placeholder.png" width="340" height="340">
</div>
</br>	
<div class="container">
  <ul class="list-unstyled">
  <li class="media">
    <img class="mr-3" src="img/devschool.png" alt="Generic placeholder image">
    <div class="media-body">
      <h5 class="mt-0 mb-1">List-based media object</h5>
      Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.
    </div>
  </li>
  <li class="media my-4">
    <img class="mr-3" src="img/devschool.png" alt="Generic placeholder image">
    <div class="media-body">
      <h5 class="mt-0 mb-1">List-based media object</h5>
      Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.
    </div>
  </li>
  <li class="media">
    <img class="mr-3" src="img/devschool.png" alt="Generic placeholder image">
    <div class="media-body">
      <h5 class="mt-0 mb-1">List-based media object</h5>
      Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.
    </div>
  </li>
</ul>
</div>
<div><img src="img/4305157.jpg" alt="" width="100%"></div>
<span class="d-block p-2 bg-primary text-white">Page HTML&CSS&Javascript</span>

<script type="text/javascript">
//http://www.dynamicdrive.com
//Traduction http://www.outils-web.com

//Taille des images, elle doivent avoir toutes les mêmes dimensions
	var Car_Image_Width=340;
	var Car_Image_Height=340;
	var Car_Border=true;		// true ou false
	var Car_Border_Color="white";
	var Car_Speed=4;
	var Car_Direction=true;		// true or false
	var Car_NoOfSides=12;		// nb de faces 4,6,8 ou 12

/* Liste des images et des liens associés 
le nb d'images à déclarer doit être la moitié du nombre de faces
ici 8 faces donc 4 images
*/
	Car_Image_Sources=new Array(
		"img/proglang/java-N5uhyL.jpg","",
		"img/proglang/illu_tout-sur-le-javascript.png","",
		"img/proglang/objective-c.png","", //exemple sans lien
		"img/proglang/image-article-blog-2.png","",//pas de virgule a la derniere

		
		"img/DEV SCHOOL.png","",
		"img/proglang/proglang.jpg","",
		//"img/proglang/objective-c.png","", //exemple sans lien
		"img/proglang/learn_c_sharp.jpg","" //pas de virgule a la derniere
		);

//ne rien modifier ci-dessous
	CW_I=new Array(Car_NoOfSides/2+1);C_ClcW=new Array(Car_NoOfSides/2);
	C_Coef=new Array(
		3*Math.PI/2,0,3*Math.PI/2,11*Math.PI/6,Math.PI/6,3*Math.PI/2,7*Math.PI/4,	0,
		Math.PI/4,3*Math.PI/2,5*Math.PI/3,11*Math.PI/6,0,Math.PI/6,Math.PI/3);
	var C_CoefOf=Car_NoOfSides==4?0:Car_NoOfSides==6?2:Car_NoOfSides==8?5:9;
	C_Pre_Img=new Array(Car_Image_Sources.length);
	var C_Angle=Car_Direction?Math.PI/(Car_NoOfSides/2):0,C_CrImg=Car_NoOfSides,C_MaxW,C_TotalW,
	C_Stppd=false,i,C_LeftOffset,C_HalfNo=Car_NoOfSides/2;

	function Carousel(){
		if(document.getElementById){
			for(i=0;i<Car_Image_Sources.length;i+=2){
				C_Pre_Img[i]=new Image();C_Pre_Img[i].src=Car_Image_Sources[i]}
			C_MaxW=Car_Image_Width/Math.sin(Math.PI/Car_NoOfSides)+C_HalfNo+1;
			Car_Div=document.getElementById("Carousel");
			for(i=0;i<C_HalfNo;i++){
				CW_I[i]=document.createElement("img");Car_Div.appendChild(CW_I[i]);	
				CW_I[i].style.position="absolute";
				CW_I[i].style.top=0+"px";
				CW_I[i].style.height=Car_Image_Height+"px";
				if(Car_Border){
					CW_I[i].style.borderStyle="solid";
					CW_I[i].style.borderWidth=1+"px";
					CW_I[i].style.borderColor=Car_Border_Color}
				CW_I[i].src=Car_Image_Sources[2*i];
				CW_I[i].lnk=Car_Image_Sources[2*i+1];
				CW_I[i].onclick=C_LdLnk;
				}
			CarImages()}}

	function CarImages(){
		if(!C_Stppd){
			C_TotalW=0;
			for(i=0;i<C_HalfNo;i++){
				C_ClcW[i]=Math.round(Math.cos(Math.abs(C_Coef[C_CoefOf+i]+C_Angle))*Car_Image_Width);
				C_TotalW+=C_ClcW[i]}
			C_LeftOffset=(C_MaxW-C_TotalW)/2;
			for(i=0;i<C_HalfNo;i++){
				CW_I[i].style.left=C_LeftOffset+"px";
				CW_I[i].style.width=C_ClcW[i]+"px";
				C_LeftOffset+=C_ClcW[i]}
			C_Angle+=Car_Speed/720*Math.PI*(Car_Direction?-1:1);
			if((Car_Direction&&C_Angle<=0)||(!Car_Direction&&C_Angle>=Math.PI/C_HalfNo)){
				if(C_CrImg==Car_Image_Sources.length)C_CrImg=0;
				if(Car_Direction){
					CW_I[C_HalfNo]=CW_I[0];
					for(i=0;i<C_HalfNo;i++)CW_I[i]=CW_I[i+1];
					CW_I[C_HalfNo-1].src=Car_Image_Sources[C_CrImg];
					CW_I[C_HalfNo-1].lnk=Car_Image_Sources[C_CrImg+1]}
				else{	for(i=C_HalfNo;i>0;i--)CW_I[i]=CW_I[i-1];
					CW_I[0]=CW_I[C_HalfNo];
					CW_I[0].src=Car_Image_Sources[C_CrImg];
					CW_I[0].lnk=Car_Image_Sources[C_CrImg+1]}
				C_Angle=Car_Direction?Math.PI/C_HalfNo:0;C_CrImg+=2}}
		setTimeout("CarImages()",50)}

	function C_LdLnk(){if(this.lnk)window.location.href=this.lnk}
</script>
	
<!-- Lien clignant -->
<script type="text/javascript" language="javascript">
var lien = "";
function rand(max) {
  return (Math.floor(Math.random() * max));
}

function initaec() {
	for (var i=0;i<document.links.length;i++) {
		if (document.links[i].className == "aec") {
			document.links[i].onmouseover = aec;
			document.links[i].onmouseout = unaec;
			document.links[i].aecTimer = null;
		}
	}
}

function aec(isFF) {
	if (isFF) {
		lien = isFF.target;
		isFF.target.aecTimer = setInterval('lien.style.color = "rgb("+rand(256)+","+rand(256)+","+rand(256)+")";',100);
	}
}

function unaec(isFF) {
	if (isFF) { 
		clearInterval(isFF.target.aecTimer);
		isFF.target.aecTimer = null;
		isFF.target.style.color = "";
	}
}
</script>
</body>
</html>
