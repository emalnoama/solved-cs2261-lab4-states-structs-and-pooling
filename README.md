Download Link: https://assignmentchef.com/product/solved-cs2261-lab4-states-structs-and-pooling
<br>
States, Structs, and Pooling

<h1>Provided Files</h1>

<ul>

 <li>c</li>

 <li>c</li>

 <li>h</li>

 <li>c</li>

 <li>h</li>

</ul>

<h1>Files to Edit/Add</h1>

<ul>

 <li>c</li>

 <li>c</li>

 <li>h</li>

 <li>Makefile</li>

 <li>.vscode</li>

</ul>

○ tasks.json




<h1>Instructions</h1>

In this lab, you will be completing several different TODOs, which will piece by piece, make a simple Space-Invaders-like game. Each TODO represents a component of the game, and is broken down into sub-TODOs. Your code will likely not compile until you complete an entire TODO block, at which point the game should compile with the new component added and working.

After you download and unzip the files, add your Makefile and your tasks.json, and then compile and run it. At this point, you should see just a blank black screen. Complete the TODOs in order, paying close attention to the instructions.

<strong> </strong>

<strong> </strong>

<h2>TODO 1 – State Machine</h2>

<ul>

 <li>For our game to be user-friendly, we need to implement a state machine first. The state machine for this assignment will have the following states:</li>

</ul>

○ START

■ Consists of a blank PINK screen  (given macro in myLib.h)

■ The seed for the random number generator increases each frame spent in this state

■ Pressing SELECT takes you to the GAME state, seeds the random number generator, and calls initGame()​

○ GAME

■ Consists of a blank black background with a game running on top  of it (we will add in the game in later TODOs)

■ Calls updateGame()​ , ​ waitForVBlank()​ , and ​ drawGame()​

■ Pressing SELECT takes you to the PAUSE state

■ Pressing B takes you to the WIN state (for now)

■ Pressing A takes you to the LOSE state

○ PAUSE

■ Consists of a blank GOLD screen (given macro in myLib.h

■ Pressing SELECT takes you to the GAME state without reinitializing the game

■ Pressing START takes you back to the START state

○ WIN

■ Consists of a blank green screen

■ Pressing SELECT takes you back to the START state

○ LOSE

■ Consists of a blank red screen

■ Pressing SELECT takes you back to the START state




To help you visualize, the state machine looks like this:




<ul>

 <li>​<strong> TODO 1.0</strong>​: In the main while loop, create the switch-case for the state machine.</li>

 <li>​<strong>TODO 1.1</strong>​: Below the already-written initialize function, make the functions for all of your states with their respective goTo functions. Make sure that the states work like the ones described above, and that you don’t do things every frame that only need to be done once (like fillScreen)</li>

 <li>​<strong>TODO 1.2</strong>​: Now that you have made these functions, put the prototypes for them at the top of​c​.</li>

</ul>




​<strong>TODO 1.3</strong>​: Call your goToStart function in the initialize function so that when the game starts, the START state is first. If you haven’t already done so, call your state functions in the state machine switch-case.

<ul>

 <li>Compile and run. You should be able to travel through all the states by pressing the respective buttons. If not, fix this before going further.</li>

</ul>

<strong> </strong>

<h2>TODO 2 – Cannon</h2>

<ul>

 <li>Now that we have our state machine set up, we can begin adding in the game. We will do this in​c ​and​ game.h​, and call those functions in​ main.c ​(like we already are with ​initGame()​,​ updateGame()​, and ​drawGame()​). Let’s start by getting the cannon working.</li>

 <li>​<strong>TODO 2.0</strong>​: In​h​, create the struct for the cannon, typedef-ed ​PLAYER​. The cannon should have a row, col, oldRow, oldCol, cdel, height, width, color, and a bulletTimer (we will see the use for this later). All of the cannon members can be of type int except color, which should be an unsigned short.</li>

 <li>​<strong>UNCOMMENT 2.0</strong>​: Below this, uncomment the line that declares the cannon.</li>

 <li>​<strong>UNCOMMENT 2.1</strong>​: In​c​, uncomment the line that declares the cannon here.</li>

 <li>​<strong>UNCOMMENT 2.2</strong>​: Below the drawBar function, uncomment​ initCannon()​, updateCannon()​, and​ drawCannon()​.</li>

 <li>​<strong>UNCOMMENT 2.3</strong>​: Now that we have these cannon functions, uncomment the prototypes in ​h</li>

 <li>​<strong>UNCOMMENT 2.4</strong>​: Uncomment ​initCannon()​ in ​initGame()</li>

 <li>​<strong>UNCOMMENT 2.5</strong>​: Uncomment ​updateCannon()​ in ​updateGame()</li>

 <li>​<strong>UNCOMMENT 2.6</strong>​: Uncomment ​drawCannon()​ and ​drawBar()​ in ​drawGame()</li>

 <li>Compile and run. When you enter the game state, you should see the cannon under the red bar, and move the cannon left and right. If not, fix this before going further.</li>

</ul>

<h2>TODO 3 – Bullets</h2>

<ul>

 <li>Now that the cannon is moving, let’s give it a pool of bullets to shoot.</li>

 <li>​<strong>UNCOMMENT 3.0</strong>​: In​c​, uncomment the line that declares the pool of bullets here.</li>

 <li>​<strong>UNCOMMENT 3.1</strong>​: Below the drawCannon function, uncomment ​initBullet()​, fireBullet()​,​ updateBullet()​, and ​drawBullet()​.</li>

</ul>

​<strong>TODO 3.0</strong>​: Complete ​initBullets()​ by initializing all the bullets with the following values:

<ul>

 <li>height – 2</li>

</ul>

○ width – 1

○ row – negative the bullet’s height

○ col – 0

○ oldRow – the cannon’s row

○ oldCol – the cannon’s col

○ rdel – negative 2

○ color – white

○ active – 0

<ul>

 <li>​<strong>TODO 3.1</strong>​: Complete the ​updateBullets()​ This takes in a pointer to a bullet. If the bullet is inactive, the function does nothing. If it is active, it moves the bullet up the screen. If the bullet goes off the top of the screen, make it inactive.</li>

 <li>​<strong>UNCOMMENT 3.2</strong>​: Now that we have these bullet functions, uncomment the prototypes in​h</li>

 <li>​<strong>UNCOMMENT 3.3</strong>​: Uncomment ​initBullets()​ in ​initGame()</li>

 <li>​<strong>TODO 3.2</strong>​: In ​updateGame()​, call ​updateBullet()​ for each of your bullets.</li>

 <li>​<strong>TODO 3.3</strong>​: Complete ​fireBullet()​. This should iterate through the bullets to find the first inactive bullet in the pool and initialize it. When you are finished initializing, ​break out of the loop. Initialize the bullet like so:

  <ul>

   <li>row – the cannon’s row</li>

  </ul></li>

</ul>

○ col – cannon col + (cannon width / 2) + (bullet width / 2)

■ This is the center of the cannon’s top

○ active – 1

○ erased – 0

<ul>

 <li>​<strong>UNCOMMENT 3.4</strong>​: In ​updateCannon()​, uncomment ​fireBullet()​ so that they actually fire</li>

 <li>​<strong>TODO 3.4</strong>​: Since pressing B fires a bullet, it should not also win the game every time you press it. So, back in​c​, comment out the fact that pressing B wins the game.</li>

 <li>​<strong>TODO 3.5</strong>​: In ​drawGame()​, call ​drawBullet()​ for all of the bullets.</li>

 <li>Compile and run. When you enter the game state, you should be able to fire bullets by pressing B. You should be able to see three at once if you fire quickly enough. If not, fix this before going further</li>

</ul>

<h2>TODO 4 – Balls</h2>

<ul>

 <li>Now that the cannon is moving and shooting, let’s give it something to shoot at.</li>

 <li>​<strong>TODO 4.0</strong>​: Most of the code to make the balls work has already been written for you, so in ​updateGame()​, call ​updateBall()​ for each of your balls.</li>

 <li>​<strong>TODO 4.1</strong>​: In ​drawGame()​, call ​drawBall()​ for all of the balls.</li>

 <li>Compile and run. When you enter the game state, you should be able to see several balls bouncing around. When you pause and unpause, they shouldn’t have moved. If not, fix this before going further. ​<em>Every time you re-run the game, the starting positions of the balls should be different</em>​. The positions may change only slightly, or may look to be the same if you idle in the START state for the same duration of time each run. Ensure ​srand()​ is working correctly by entering the GAME state immediately upon starting your game (i.e. running your Project.gba file), and by entering the GAME state 30 seconds after starting your game. If the starting position of the balls differ, you’re fine. If not, you aren’t using srand()​</li>

</ul>

<strong> </strong>

<h2>TODO 5 – Collision</h2>

<ul>

 <li>Having all those balls bounce around isn’t very fun yet. Make it so that shooting all of them allows you to win the game.</li>

 <li>​<strong>TODO 5.0</strong>​: In ​updateBall()​, loop through all of the bullets. If an active bullet is colliding with this ball, make both the bullet and the ball inactive, then decrement ballsRemaining.</li>

 <li>​<strong> TODO 5.1</strong>​: In order for the cannon to be able to win the game, you need to go back into main.c,​ and, in the game state function, transition to the WIN state if ballsRemaining is 0.</li>

 <li>Compile and run. When you enter the game state, you should be able to shoot the balls. If a bullet hits a ball, they both disappear. If you shoot all the balls, the win state should begin. If not, fix this.</li>

</ul>

At this point, you should be able to travel to all of the states, play the game, and win the game. If so, then you are done.

<strong> </strong>

<h1>Tips</h1>

<ul>

 <li>Review lecture and recitation material for how to implement a state machine and</li>

</ul>




pooling

<ul>

 <li>Follow each TODO in order, and only move forward if everything is correct</li>

</ul>