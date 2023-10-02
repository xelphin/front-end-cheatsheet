# CSS Grid

## General 
HTML

```html
<div class="container" id="<specific grid>">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
```
```css
.container{
    display: grid;
}
```

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Grid - CSS</title>
  <!-- Google Fonts -->
	<link rel="preconnect" href="https://fonts.gstatic.com">
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,300;0,500;0,700;1,500&display=swap" rel="stylesheet">


  <style>
* {
  box-sizing: border-box;
}

body {
  font-family: Arial;
  padding: 10px;
  margin:0;
}

main{
  padding:40px;
}

.example{
  margin:10px;
}


.d1{background:LightSkyBlue;}
.d2{background:LightSalmon;}
.d3{background:PaleTurquoise;}
.d4{background:LightPink;}
.d5{background:PaleGreen;}


/*GRID*/


/*DISPLAY GRID*/
.container{
    font-size: 40px;
    width: 100%;
    background: #4f4d48;
    display: grid;
    color:rgb(156, 141, 141);
    padding:5px;
}
.generic-grid{
  grid-template-columns: 50px 50px 50px;
  grid-template-rows: 50px 50px;
  grid-gap:20px 20px;
}


/*GRID TEMPLATE COLUMNS*/
#c1{grid-template-columns: 30px 30px;}
#c1-2{grid-template-columns: 200px auto 10%;}
#c1-3{grid-template-columns: 200px 2fr 10% 1fr 2fr;}

/*GRID TEMPLATE ROWS*/
#c2{
  grid-template-columns: 50px 50px 50px 50px 50px;
  grid-template-rows: 80px;
}
#c2-2{
  grid-template-columns: 50px 50px 50px;
  grid-template-rows: 65px auto;
}


/*GRID TEMPLATE ROWS*/
#c3{grid-gap:20px 30px;}


/*GRID COLUMN/ROW*/
#e4{grid-column:2/4; font-size:10px;}
#e4-2{grid-row:2/5; font-size:10px;}


/*JUSTIFY SELF*/
.c5{grid-template-columns: 1fr 1fr 1fr; grid-template-rows: 1fr 1fr 1fr;}
#e5{justify-self:center;}
#e5-2{justify-self:end;}

/*JUSTIFY ITEMS*/
.c6{justify-items:center;}


/*GRID TEMPLATE AREA*/
.c7{
  grid-template-areas:
      "header header header"
      "advert content content"
      "footer footer footer";
}
#e7{grid-area:header;}
#e7-2{grid-area:content;}


/*REPEAT*/
/*repeat 3 times 1fr == 1fr 1fr 1fr*/
.c8{grid-template-columns: repeat(3,1fr);}

/*MINMAX*/
.c9{grid-template-columns: repeat(3, minmax(150px,300px));}


/*AUTOFILL*/
.c10{grid-template-columns: repeat(auto-fill, minmax(150px, 1fr))}


/*AUTOFIT*/
.c11{grid-template-columns: repeat(auto-fit, minmax(150px, 1fr))}


/*WITH MEDIA QUERIES*/
#e12-1{grid-area: header;}
#e12-2{grid-area: advert;}
#e12-3{grid-area: content;}
#e12-4{grid-area: footer;}
.c12{
  min-height: 300px;
  grid-template-columns: 1fr;
  grid-template-rows: 50px auto 1fr auto;
  grid-gap: 10px;
  grid-template-areas:
    "header"
    "advert"
    "content"
    "footer";
}
@media (min-width: 700px){
  .c12{
    grid-template-columns: auto 1fr;
    grid-template-rows: auto 1fr auto;
    grid-template-areas:
      "advert header"
      "advert content"
      "advert footer";
  }
}
@media (min-width: 900px){
  .c12{
    grid-template-areas:
      "header header"
      "advert content"
      "footer footer";
  }
}




  </style>

  
</head>
<body>


<main>

<h2 class="title">Display Grid</h2>
    <div class="container">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>

<h2 class="title">Grid-Template-Columns</h2>
<h3>30px 30px</h3>
<div class="container" id="c1">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
<h4> > grid-template-columns: 30px 30px;</h4>

<h3>200px auto 10%</h3>
<div class="container" id="c1-2">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
<h4> > grid-template-columns: 200px auto 10%;</h4>

<h3>200px 2fr 10% 1fr 2fr</h3>
<div class="container" id="c1-3">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
<h4> > grid-template-columns: 200px 2fr 10% 1fr 2fr; </h4>

<h2 class="title">Grid-Template-Rows</h2>
<h3>80px</h3>
<div class="container" id="c2">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
<h4> > grid-template-columns: 50px 50px 50px 50px 50px;
<br> > grid-template-rows: 80px; </h4>

<h3>65px auto</h3>
<div class="container" id="c2-2">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
<h4> >  grid-template-columns: 50px 50px 50px;
<br> >  grid-template-rows: 65px auto; </h4>

<h2 class="title">Grid Gap</h2>
<h3>20px 30px</h3>
<div class="container generic-grid" id="c3">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
<h4> > grid-gap:20px 30px; </h4>

<h2 class="title">Grid Column/Row</h2>
<h3>Grid Column</h3>
<div class="container generic-grid">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5" id="e4">5 grid-column: 2/4 (start verical line2 till line4)</div>
</div>
<h4> 5th div > grid-column:2/4; font-size:10px; </h4>

<h3>Grid Row</h3>
<div class="container generic-grid">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5" id="e4-2">5 grid-column: 2/5 (start horizontal line2 till line5)</div>
</div>
<h4> 5th div > grid-row:2/5; font-size:10px; </h4>


<h2 class="title">Justify Self</h2>
<h3>Center</h3>
<div class="container c5">
    <div class="d1">1</div>
    <div class="d2" id="e5">-2-</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
<h4> > grid-template-columns: 1fr 1fr 1fr
<br> > grid-template-rows: 1fr 1fr 1fr;
<br> 2nd div > justify-self:center; </h4>

<h3>End</h3>
<div class="container c5">
    <div class="d1">1</div>
    <div class="d2" id="e5-2">-2-</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
<h4> > grid-template-columns: 1fr 1fr 1fr
<br> > grid-template-rows: 1fr 1fr 1fr;
<br> 2nd div > justify-self:end; </h4>


   <h2 class="title">Justify Items</h2>
    <h3>Center</h3>
    <div class="container c5 c6">
      <div class="d1">1</div>
      <div class="d2">2</div>
      <div class="d3">3</div>
      <div class="d4">4</div>
      <div class="d5">5</div>
    </div>
<h4> > grid-template-columns: 1fr 1fr 1fr
<br> > grid-template-rows: 1fr 1fr 1fr;
<br> > justify-items:center; </h4>


   <h2 class="title">Grid Template Area</h2>
    <div class="container c5 c7">
      <div class="d1">1</div>
      <div class="d2" id="e7-2">2</div>
      <div class="d3">3</div>
      <div class="d4">4</div>
      <div class="d5" id="e7">5</div>
    </div>
<h4> > grid-template-columns: 1fr 1fr 1fr
<br> > grid-template-rows: 1fr 1fr 1fr;
<br> >   grid-template-areas: <br>
      "header header header" <br>
      "advert content content" <br>
      "footer footer footer"; <br>
<br> 2nd div > grid-area:content; 
<br> 5th div > grid-area:header; 
</h4>

   <h2 class="title">Repeat</h2>
    <div class="container c8">
      <div class="d1">1</div>
      <div class="d2">2</div>
      <div class="d3">3</div>
      <div class="d4">4</div>
      <div class="d5">5</div>
    </div>
<h4> > grid-template-columns: repeat(3,1fr); </h4>

   <h2 class="title">MinMax</h2>
   <h3>Change size of screen to see minmax effect<h3>
    <div class="container c9">
      <div class="d1">1</div>
      <div class="d2">2</div>
      <div class="d3">3</div>
      <div class="d4">4</div>
      <div class="d5">5</div>
    </div>
<h4> > grid-template-columns: repeat(3, minmax(150px,300px)); </h4>

<h2 class="title">AutoFill</h2>
<h3>Change size of screen to see autofill effect<h3>
<div class="container c10">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
<h4> > grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)) </h4>

<h2 class="title">AutoFit</h2>
<h3>Change size of screen to see autofit effect<h3>
<div class="container c11">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
<h4> > grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)) </h4>


<h2 class="title">With Media Queries</h2>
<h3>Change size of screen to see media query effect<h3>
<div class="container c12">
    <div class="d1" id="e12-1">header</div>
    <div class="d2" id="e12-2">advert</div>
    <div class="d3" id="e12-3">content</div>
    <div class="d4" id="e12-4">footer</div>
</div>
<h4> 
#e12-1{grid-area: header;} <br>
#e12-2{grid-area: advert;} <br>
#e12-3{grid-area: content;} <br>
#e12-4{grid-area: footer;} <br>
.c12{ <br>
  min-height: 300px; <br>
  grid-template-columns: 1fr; <br>
  grid-template-rows: 50px auto 1fr auto; <br>
  grid-gap: 10px; <br>
  grid-template-areas: <br>
    "header" <br>
    "advert" <br>
    "content" <br>
    "footer"; <br>
} <br>
@media (min-width: 700px){ <br>
  .c12{ <br>
    grid-template-columns: auto 1fr; <br>
    grid-template-rows: auto 1fr auto; <br>
    grid-template-areas: <br>
      "advert header" <br>
      "advert content" <br>
      "advert footer"; <br>
  } <br>
} <br>
@media (min-width: 900px){ <br>
  .c12{ <br>
    grid-template-areas: <br>
      "header header" <br>
      "advert content" <br>
      "footer footer"; <br>
  } <br>
} <br>
</h4>

  </main>
  </body>
</html>


