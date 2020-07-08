# Bullet-Code-
*******************
Bullet code for asteroids game (this is for a friend)


Put this before everything (replace your other variables that have same name)
```JavaScript
//List of bullet attributes
var lastTheta     = [];
var bulletx       = [];
var bullety       = [];
var lastx         = [];
var lasty         = [];
var bulletShot    = false;
// the interval which you can shoot bullets
var bulletInterval      = 0;  

```

after display function put this -

```JavaScript
 bulletInterval -=dt;
  if (keyIsDown(32)){ //spacebar
    if(bulletShot==false && bulletInterval <= 0) {
        lastTheta.push(theta);
        lastx.push(x);
        lasty.push(y);
        bulletx.push(x);
        bullety.push(y);
        bulletShot = true;
        bulletInterval = 5; // the time of which you have to wait to shoot (another) a bullet after you shot one
    }
        
      
    }
    else {
      
       bulletShot = false;
       

    }
    
    // display bullet(s)
    for(f=0;f<bulletx.length;f++) {
      
      //move bullet in last direction facing
      if(bulletx[f]<width && bulletx[f]>0 && bullety[f]<height && bullety[f]>0) {
       bulletx[f] += (cos(lastTheta[f])*lastx[f])*0.01
       bullety[f] += (sin(lastTheta[f])*lasty[f])*0.01
       drawPoint(bulletx[f], bullety[f])
      }
      // remove bullet if goes off screen (or hits astroid later)
      else {
        lastTheta.splice(f, 1);
        lastx.splice(f, 1);
        lasty.splice(f, 1);
        bulletx.splice(f, 1);
        bullety.splice(f, 1);
      }
      
    }

```
