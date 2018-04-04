---
title: "Notes: Using JavaScript Libraries for Game Development"
date: 2018-02-24T14:07:29-05:00
draft: false
type: notes
tags:
- JavaScript
- coding
- games
- p5.js
- conference
- HTML5
- HTML canvas
categories:
- coding
author: Keisha S Perkins
---

This talk is about using JavaScript to create games on the [HTML5 canvas](https://www.w3schools.com/html/html5_canvas.asp). Though you won’t create the next Halo, you’ll learn so much about JavaScript and programming as a whole when you create games with it. In this talk, I’ll introduce you to a library that’s perfect for beginners and “non-coders” alike called [p5.js.](https://cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/highlight.min.js)

## Why JavaScript?

JavaScript is everywhere. If you use the internet, you’ve almost certainly encountered JavaScript. You’ve seen it move objects across the screen, fetch information to a webpage, or maybe drive the logic behind a fun game you’ve played.

With JavaScript’s ubiquity comes career opportunity and a huge community of developers. Rest assured, if you want to learn JavaScript, you’ll be learning a tool that is used across the internet by millions every day.

## Why p5.js

P5.js is the perfect place to begin your foray into programming with JavaScript as it is designed with the beginner, the artist, the poet, and the educator in mind. If you're anything like me, you want to see a results quickly. P5.js gets you up and running right away. With just a few lines of code, you can have interativity.

With p5, you can add and remove functionality as you need it with p5’s [extender libraries](https://p5js.org/libraries/). Want to make a speech analysis tool? Use [p5.speech](http://abilitylab.nyu.edu/p5.js-speech/). Want to make music in the browser? How about [p5.gibber](http://charlie-roberts.com/gibber/p5-gibber/)? Interested in physical computing? Try [p5.bots](https://github.com/sarahgp/p5bots).

And don’t worry if you’re just starting out. You’ll see how easy it can be when the p5 library helps to do some of the work for you!

### What is p5.js?

P5.js is “a JavaScript library that starts with the original goal of [Processing](http://processing.org/), to make coding accessible for artists, designers, eductaors, and beginners, and reinterprets this for today's web,” according to the [official p5.js website](https://p5js.org/). What this means is that p5 was first developed in order to make it easier to start programming no matter your background or skill level.

## Using P5.js

The first thing we need to know about p5.js is that there are two main functions built into it: the `setup()` function and the `draw()` function. The `setup()` function is where we want to put things that we only want the computer to do once at the start of our program. The `draw()` function is where we put things we want the computer to do many time every second. The default is 60 executions every second.

### Creating the Canvas

So let’s start by creating the canvas we want to draw on. We’ll tell the computer we want the canvas to be 800 pixels wide and 300 pixels tall. We’ll also tell it that we want the canvas to be black. Here's the code:

    function setup() {

    	createCanvas(800, 300);

    	background('black');

    }

    

    function draw() {

    

    }

    	

[Here's the result](http://keishasperkins.com/talks/activate2018/examples/blankCanvas.html)

### Adding Some Interest

Not terribly impressive. But let’s draw on that canvas. In the draw function, let’s add an ellipse that is 80 pixels in from the left and 50 pixels down from the top. We’ll also make it 20 pixels wide and 60 pixels tall.

Here's the code:

    function setup() {

    	createCanvas(800, 300);

    	background('black');

    }

    

    function draw() {

    	ellipse(80,50,20,60)

    

    }

    	

[Here's the result](http://keishasperkins.com/talks/activate2018/examples/blankCanvasWithEllipse.html)

Though this ellipse appears to be still, it is being drawn 60 times each second. Let's add some movement so we can see why the `draw()` function is so important.

### Adding More Interactivity

Now let’s add some movement. We can use a set of p5.js variables called `mouseX` and `mouseY` to make the ellipse follow our mouse instead of telling the computer a specific location. At the start of every draw function, the computer will look to see where our mouse cursor is and draw our ellipse right underneath.

Here's the code:

    function setup() {

    	createCanvas(800, 300);

    	background('black');

    }

    

    function draw() {

    	ellipse(mouseX, mouseY, 50, 50);

    }

    	

[Here's the result](http://keishasperkins.com/talks/activate2018/examples/ellipseFollowsMouseWithPath.html)

### Get Rid of that Tail

Remember that we said things in the `setup()` function only happen once? What if we put our instructions for our background in the `draw()` function so that it is draw at the start of every frame?

The result is that the ellipse’s “tail” has gone away because the background is draw at the start of each frame, covering the ellipse from the last frame. This simple loop allows us to simulate the real-world look of movement on our 2D canvas

Here's the code:    


    function setup() {

    	createCanvas(800, 300);

    }

    

    function draw() {

    	background('black');

    	ellipse(mouseX, mouseY, 50, 50);

    }

    	


[Here's the result](http://keishasperkins.com/talks/activate2018/examples/ellipseFollowsMouseNoPath.html)

This is just a small introduction to the library, but have a look at some of the things others have built with p5.js! Perhaps it will inspire to you build something, too.

*   [Noisefactor’s Pen “Simple paint program”](https://codepen.io/noisefactor/pen/rezrQW)
*   [Yugam’s Pen “Card’s Rotation”](https://codepen.io/pizza3/pen/rjaPNY)
*   [P5.js Example: Reach 1](https://p5js.org/examples/interaction-reach-1.html)
*   [shaggy’s Pen “Wave Gen – p5.js”](https://codepen.io/sha99y8oy/pen/KrbPzx)

## But Where Are the Games?!

P5.js is great for building games all by itself. But with the help of extender libraries, making games is even easier. Let’s have a look at the [p5.play](http://p5play.molleindustria.org/) and [p5.sound](https://p5js.org/reference/#/libraries/p5.sound) extender libraries.

### P5.play

P5.play is a library “for the creation of games and playthings” written Paolo Pedercini. P5.play provides sprites, animations, input and collision functions for games and gamelike applications. It’s built for accessibility over performance.

#### What Is a Sprite?

The main building block of p5.play, a sprite is an element able to store images or animations with a set of properties such as position and visibility. Sprites can have a collider that defines the active area to detect collisions or overlappings with other sprites and mouse interactions. This means that you use sprites to represent things in your game environment and p5.play will keep up with where they are, what they overlap, and how they should be moving.

#### Let’s Add a Sprite!

Adding a sprite is pretty simple, we just need a variable for our sprite to live in. We use the `CreateSprite()` function to make a sprite that is 150 pixels down from the top and 150 pixels down from the bottom. The sprite will be 50 pixels wide and 160 pixels tall. In our `draw()` function, we use `drawSprites()` to let the computer know that we want to see our sprites.

Here's the code:

    var robot;

    function setup() {

    	robot = createSprite(150,150,50,160);

    	createCanvas(800, 300);

    }

    function draw() {

    	background('black');

    	drawSprites();

    }

    	

[Here's the result](http://keishasperkins.com/talks/activate2018/examples/addOurFirstSprite.html)

Though it may not look like it, that rectangle has velocity, space, depth, collision, and lots of other properties already built in. It’s ready for us to start manipulating it. First, let’s add an animation to the sprite!

#### Adding an Animation to Our Sprite

Sprites can take on several animations, and animations can be in the form of a series of pictures or a spritesheet. Here, we’ll tell the computer that our sprite should have an animation that we’ll call “idle” and that the animation should consist of all images from “idle01.png” to “idle09.png” from our files.

P5.play very convieniently keeps track of these for us. We just need to name the images according to the order they appear in our animation. P5.play will read the titles and do the rest.

**Note:** The files referenced here are saved in the same folder as the p5.js sketch. In order for your animations to work, you will need images to assign. A great place to find free sprites is[opengameart.com](http://opengameart.org)

Hers's the code:

    var robot;

    

    function setup() {

    	robot = createSprite(150,150,50,160);

    	robot.addAnimation("idle", "images/Idle02.png", "images/Idle09.png");

    	createCanvas(800, 300);

    }

    

    function draw() {

    	background('black');

    	drawSprites();

    }

    	

[Here's the result](http://keishasperkins.com/talks/activate2018/examples/animateOurSprite.html)

And there she is! Our little robot!

#### Adding Interactivity to our sprite

What if we want to add some interaction? Let’s give the computer some instructions on what to do when we press a certain key. In our setup function we’ll add another animation called “run” with similar syntax as before.

Then, in our draw function, we’ll put a bit of logic that first checks to see if someone is pressing the right arrow key, and then changes the robot’s velocity so that she moves to the right. The robot will also change animations when the key is pressed, creating the effect of running.

Here's the code:

    var robot;

    

    function setup() {

    	robot = createSprite(150,150,50,160);

    	robot.addAnimation("idle", "images/idle01.png", "images/idle09.png");

    	robot.addAnimation("jump", "images/jump01.png", "images/jump10.png");

    	createCanvas(800, 300);			

    }

    

    function draw() {

    	background('black');			

    	if(keyIsDown(32)){

    		robot.changeAnimation("jump");

    	} else if(!keyIsDown(32)) {

    		robot.changeAnimation("idle");

    	}

    	drawSprites();

    }

    	

[Here's the result](http://keishasperkins.com/talks/activate2018/examples/keyPressSpriteAction.html)

Using functions like the ones we’ve used above, we can make games that are simple and fun to play. [This game](http://keishasperkins.com/talks/activate2018/examples/gameExampleSilent.html) was built with less than 200 lines of code using these libraries.

**Note:** A great little resource I like to use is [Keycode.info](http://keycode.info) by Wes Bos. This nifty little website gives you keycodes for the keys on your keyboard. It's very helpful when writing in keyboard event handlers.

Check out some of these other things built with this wonderful library:

*   [Yuki Kayashima’s Pen “p5.js_breakout”](https://codepen.io/seil/pen/LxzZxM)
*   [Joseph Palmezano’s Pen “Angry PacMan p5.js”](https://codepen.io/matedemorphy/pen/bREMZJ)
*   [Setup Draw’s Pen “ASTEROIDS”](https://codepen.io/SetupDraw/pen/yoXZbR)

### But Where Is the Sound?

Notice how all of these examples have been silent. To add sound to our game, we will use the p5.sound extender library. p5.sound extends p5 with Web Audio functionality including audio input, playback, analysis and synthesis.

It will allow us to trigger songs and sounds at certain parts in the game. For instance, let’s add a song at the start of the game we saw earlier.

We'll add this code into our `setup()` function and introduce a new function, `preload()`.

Here's the code:

    var gameMusic;

    

    function preload(){

    	gameMusic = loadSound('gameMusic.mp3');

    }

    

    function setup(){

    	gameMusic.play();

    }

    	

[Here's the result](http://keishasperkins.com/talks/activate2018/examples/gameExample.html)

The `preload()` function allows us to load all of our assets before the program begins. This is very useful for when we have large files or have many files to load. In the preload function, we will load our sound to a variable called “gameMusic”. At the start of the setup function, we can play the song.

We don't want to put our `play()` call in the `draw()` function because that would cause a new instance of our song to start playing, overlapping 60 times in one second!

With a bit more coding, we can trigger sounds for when the game is being played, when the game is over and even when a certain action occurs in the game.

## Conclusion

I hope this quick introduction to p5.js and its extender libraries p5.play and p5.sound helped to inspire your creativity. I encourage you to continue learning about the libraries. There is so much you can do with them.

Here is a list of resources that may help you in learning a bit more

*   [p5.js Website](http://p5js.org)
*   [p5.play Website](http://p5play.molleindustria.org/)
*   [Daniel Shiffman: The Coding Train](https://www.youtube.com/watch?v=8j0UDiN7my4)
*   [Book: _Getting Started with P5.js_](http://www.amazon.com/Make-Interactive-Graphics-JavaScript-Processing/dp/1457186772)

Here is a list of resources that may help you in creating games.

*   [Open Game Art](http://opengameart.org)
*   [KeyCode.info](http://keycode.info)
*   [CodePen](https://codepen.io)
*   [Free Sound](http://freesound.org)

If you like that robot game. You can see how it's built on [its accompanying tutorial site](https://la-wit.github.io/build-an-infinite-runner). And you'd like to jump right into making with p5.js, you can fork this pen start right away. The pen already has p5.js, p5.play, p5.sound, and another extender library, [p5.dom](https://p5js.org/reference/#/libraries/p5.dom) linked.

Have fun!