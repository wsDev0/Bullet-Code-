# Bullet-Code-
*******************
Bullet code for asteroids game

Put this before everything (replace your other variables that have same name)
```JavaScript
//List of bullet attributes
var lastTheta     = [];
var bulletx       = [];
var bullety       = [];
var lastx         = [];
var lasty         = [];
var bulletShot    = false;
// the interval of which you can shoot bullets
var bulletInterval      = 0;  

```

any where after variables put this -

```JavaScript
 bulletInterval -=dt;
  if (keyIsDown(32)){ //spacebar
    if(bulletShot==false && bulletInterval <= 0) {
        //pushes the last position and data of the ship into lists which each bullet needs
        lastTheta.push(theta);
        lastx.push(x);
        lasty.push(y);
        bulletx.push(x);
        bullety.push(y);
        // set bulletShot to false if you want to be able to auto shoot
        bulletShot = true;
        bulletInterval = 5; // the time of which you have to wait to shoot (another/a) bullet after you shot one
    }
        
      
    }
    else {
       
       //makes it so when you press space again you can shoot (but bulletInterval has to be 0)
       bulletShot = false;
       

    }
   ```
    
after display function put this -
    
```JavaScript
       // display bullet(s)
       for(f=0;f<bulletx.length;f++) {
      
         //move bullet in last direction facing
         if(bulletx[f]<width && bulletx[f]>0 && bullety[f]<height && bullety[f]>0) {
       
          //adds the bulletx and bullety of each bullet
          bulletx[f] += (cos(lastTheta[f])*lastx[f])*0.01 // change 0.01 to something else if you want your bullet to be faster or slower
          bullety[f] += (sin(lastTheta[f])*lasty[f])*0.01 // change 0.01 to something else if you want your bullet to be faster or slower
          drawPoint(bulletx[f], bullety[f]) // this draws the bullet with a simple point function ( you can make it something else )
         }
         // remove bullet if goes off screen (or hits astroid later)
         else {
           // splice removes something from a list, in this case, it is removing f (the picked bullets data (by index) from lists) if the current bullet goes off screen
           // splices syntax (in my words) is: list.splice(from (index/int), to (index/int, always put 1 if you want it only to delete 1 object))
          lastTheta.splice(f, 1);
          lastx.splice(f, 1);
          lasty.splice(f, 1);
          bulletx.splice(f, 1);
          bullety.splice(f, 1);
        }
      
      }

   ```
