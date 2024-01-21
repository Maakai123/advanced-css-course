https://bennettfeely.com/clippy/ for clipping sites 

clip-path: polygon(xy, xy, xy xy)
                   00, 100 = distance from 1st point in x direction 0

link: link sudo class
.btn:link => state of the btn selector, user hovers over the button 

visited state:  when user has already visted a btn before and visit it again before clicked it will be blue, when you visit again it will be purple.

to put them togther, you want both the visited state and link state to be the same.

note: an in-line block element is treated like a text




THREE PILLARS OF WRITING GOOD HTML AND CSS

-Responsive web design: Media queries, Responsive images, Desktop first vs Mobile first 

-Maintainable and Scalable code: clean, easy to understand, Growth, Reuseable, how to organize files, how to name classes and how to structure html


-Web performance : Less http requests, less code, compress code
use a css preprocessor, less images and compress images


What Happens to Css when we load up a webpage 

-1  Load HTML => PARSE HTML =>           DOCUMENT OBJECT MODEL (DOM) =(Tree)                                                                |
                    |
               load CSS => PARSE CSS
                              |
                            1. Resolve conflicting
                             CSS declarations 
                              (cascade)             => CSS OBJECT MODEL
                                                       (cssom)
                                                                                                                                             | 
                              2.Process final css 
                                values
                               like converting % to px




                                                            =========
final rendering of site <=   Website rendering visual formating model                                                 <= Render Tree 


CASCADE AND SPECIFICITY 

-CSS declaration marked !important have the highest priority 
-But only use !important as a last resource. its better to use correct specificies-  Maintainable code

inline-styles will always have priority over styles in external stylesheets;

A selector that conatians  1 id is more specific than one with 1000 classes

A selector that contains 1 class is more specific than one with 1000 elements;

The universal selector * has no specificity value(0,0,0,0)

Rely more on specificity than on the order selectors
but rely on order when using 3rd-partry stylesheets- always put your author stylesheet last




npm install node-sass --save-dev
create sass folder
create sass file => touch main.scss  sassy css

npm run compile: sass
incase of issues
npm install node-sass


touch _variable.scss   _mixins.scss _functions.scsss to create folders in terminal

<img src="" alt="" class="composition__photo  composition__photo--p1 => modifier"> 


html Entity Reference ccs Tricks

/*
COLORS:

Light green: #7ed56f
Medium green: #55c57a
Dark green: #28b485

*/

/*after and befor pseodo class to get everything in the universal selector*/

/*
*,
*::after,
*::before{
    margin: 0;
    padding: 0;
    box-sizing: inherit;
}


html {
 font-size: 62.5% /*100px / 16*/

 /*
}

body{
    font-family: "Lato", sans-serif;  /*The whole body will Inherite the font size*/
    /*font-weight: 400;
    /*font-size: 16px;*/
    /*
    line-height: 1.7;
    color:#777;
    padding:3rem;
   
}

.header {
    height:95vh; /*This will not allow whole page to be full,
    the space in the bottom*/
    background-image: linear-gradient( 
        to  right  bottom,
    rgba(126, 213, 111, 0.8),
    rgba(40, 180, 131, 0.8)),url(../img/hero.jpg); /*Add color to the bg-img*/
    background-size: cover;
    background-position: top;
    clip-path:polygon(0 0, 100% 0, 100% 75vh, 0 100%);
    position: relative;
}

.header__logo-container{
    position: absolute;
    top:4rem;
    left: 4rem;
}

.header__logo{
    height: 35px;
}

.header__text-conatiner{
 position: absolute;
 /*top: 40% relative to the parent(header), left:50%*/
 top:40%;
 left:50%; 

 /*Center them, this will be in relative to the  individual elements span*/
transform: translate(-50%, -50%); 

text-align: center;
}

.heading-primary{
 color:#fff;
 text-transform: uppercase;
 /*Stop anim from bouncing*/

 backface-visibility: hidden;
}

.heading-primary--main{
    display: block; /*Push span down(Inline element)*/
    font-size: 6rem;
    font-weight: 400;
    letter-spacing: 3.5rem;

    /*Animation*/
    animation-name: moveInLeft; /*Move to left*/
    animation-duration: 1s;
    animation-timing-function: ease-out;


    /*
    animation-deley: 3s delay anim for 3s;
    animation-iteration-count:3 repeat anim 3 times b4 stoping
    */
}

.heading-primary--sub{
    display: block;
    font-size:2rem ;
    font-weight: 700;
    letter-spacing: 17.4px;
    animation: moveInRight 1s ease-out;
    margin-bottom: 5rem;
}

/*Animation to the left */
@keyframes moveInLeft {
 /*start 0%*/
 0% {
    opacity:0;/*Dont show at the start*/
    transform:translateX(-10rem) /*from left to right horizontal which is also -*/
 } 
 
 80% {
    transform: translateX(1rem) /*move it to right a little before back to original position*/
 }

 /*end 100%*/
 100% {
    opacity: 1;
    transform: translate(0);
 }
 
}



/*Animation to the right */
@keyframes moveInRight {
    /*start 0%*/
    0% {
       opacity:0;/*Dont show at the start*/
       transform:translateX(10rem) /*move from right to left horizontal which is also + */
    } 
    
    80% {
       transform: translateX(-1rem) /*move it to left  a little before back to original position*/
    }
   
    /*end 100%*/
    100% {
       opacity: 1;
       transform: translate(0);
    }
    
   }



   @keyframes moveInBottom{
    /*start 0%*/
    0% {
       opacity:0;/*Dont show at the start*/
       transform:translateY(3rem) /*move from TOP to Bottom vertical which is also + */
    } 
     /*end 100%*/
    100% {
       opacity: 1;
       transform: translate(0);
    }
    
   }
   .btn:link,
   .btn:visited {
    text-transform: uppercase;
    text-decoration: none;
    padding: 1.5rem 4rem;
    display: inline-block;
    border-radius: 100px;
    transition: all .2s;
    position: relative;
    font-size: 1.5rem;
   }


   .btn--white{
    background-color: #fff;
    color:#777;
   }
   .btn:hover {
    transform:translateY(-3px); /*move from top to bottom and scale upwards -3*/
    box-shadow: 0 1rem 2rem rgba(0,0,0,.2);
   }

   .btn:active {
    transform:translateY(-1px);
    box-shadow: 0 .5rem 1rem rgba(0,0,0,.2)
   }

   /*Create another imaginary button behind the main the btn*/

   .btn::after { /*Create an imaginary btn*/
    content: "";
    display:inline-block;
    height: 100%;
    width: 100%;
    border-radius:10rem;
    position:absolute; /*push to any direction*/
    top:0;
    left:0;
    z-index: -1; /*push it behind the main btn*/
    transition: all .5s; /*animation stay on for 0.4secs*/

   }


   .btn--white::after {
    background-color:#fff /*Give it the same color like the original*/
   }

  .btn:hover::after {
    transform: scaleX(1.4) scaleY(1.5);
    opacity:0;
  }

  .btn--animated {
    /*animation: name  duration timing-function delay iteration-count direction fill-mode*/
    animation: moveInBottom  .5s ease-out 0.7s ;
    animation-fill-mode: backwards; /*Stop it from loading from the start*/
  }
  