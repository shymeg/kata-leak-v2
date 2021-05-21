<!-- PROJECT LOGO -->
<br />
<p align="center">
</p>
  <h3 align="center">kata# leak v2 </h3>
  <p align="center">
    <br />
    <br />
</p>


## CREDITS 
Before starting i would like to thanks:

-nobody told me | https://www.twitch.tv/iowxd -> Gave me the exe & a license which i didn't even used 
<!-- TABLE OF CONTENTS -->
## Table of Contents

* [Why The leak](#why-the-leak)
* [Pasted](#pasted)
* [Crack](#Crack)
* [How to use](#usage)

<!-- ABOUT THE PROJECT -->
## Why the leak
Well, i wanted to buy the program, but the seller scammed me for 10$ (lmao) 

and then i contacted kata#, in first goal to pay his shit program, but also to help him protect his program, which i usually do. 

he's shown disrespectful to me, so i decided to leak. 


<!-- GETTING STARTED -->
## Pasted

Well, I'm not a c# expert but i can tell you that shit is fully pasted lmao, the code is trash as the protection


### Crack

So, How did i do ? 

I analyzed the authentication, just like the v1 leak, and saw most of string were obfuscated & unobfuscated at runtime (which is logic)

So i took a online api testing tool to test his api. 
Was returning a 404 error when using a bad token.

That could seem stupid to you, but a 404 on a rest api isn't common AT ALL.

With me knowing that, the last step was just to deobfuscate string, which i did with de4dot.
Now the file can be open in ida.
  <img src=https://cdn.discordapp.com/attachments/839067677712580638/845405155872735262/unknown.png></img>

hehe wrong string to have! 

lets just walk through the string to see how it work. So... 
  <img src=https://cdn.discordapp.com/attachments/839067677712580638/845405377436450826/unknown.png></img>

the "fail func" 

Just xref to the location to see why it call it.
  <img src=https://cdn.discordapp.com/attachments/839067677712580638/845406627104161842/unknown.png></img>

So, if it is bfalse mean it fail.

Lets see how we can change that.

So with a simple google search we can find this : 
https://en.wikipedia.org/wiki/List_of_CIL_instructions

Which is just all IL Instructions with their hex values; 

Now we use ida to make a "mini signature" of the function calling thing (IsSuccessStatusCode()) 

and we get on this 
  <img src=https://cdn.discordapp.com/attachments/839067677712580638/845407013093769216/unknown.png></img>

The last step is just to hex modify every signature found in the file by the new opcode 

so 6F C3 00 00 0A 2C -> 6F C3 00 00 0A 2D
<!-- USAGE EXAMPLES -->
## usage

just run the modified exe file


Completed in 20minutes.
