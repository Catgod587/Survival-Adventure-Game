# Survival Adventure Game

<!DOCTYPE html>
<html>
<head>
<style>

.button1 {
   background-color: black;
   color: royalblue;
   border: 2px solid #555575;
}

.button2 {
   background-color: black;
   color: red;
   border: 2px solid #555575;
}

.button3 {
   background-color: black;
   color: darkolivegreen;
   border: 2px solid #555575;
}

.button4 {
   background-color: black;
   color: grey;
   border: 2px solid #555575;
}

.button5 {
   background-color: black;
   color: darkslateblue;
   border: 2px solid #555575;
}

body{
    background : url("http://images.dinamani.com/uploads/user/imagelibrary/2016/11/14/original/maxresdefault.jpg");
    background-position: right;
    background-size: cover;
    background-attachment: fixed;
    }
h1 {
   color: royalblue;
   text-align: center;
    text-shadow: 2px 2px 5px black;
}
h2 {    
    color: darkred;
    text-align: right;
    text-shadow: 2px 2px 5px black;
}
h3 {    
    color: darkgoldenrod;
    text-align: center;
    text-shadow: 2px 2px 5px black;
}
p { 
    color: royalblue;
    text-align: center;
}
h4 {    
    color: darkred;
    text-align: center;
    text-shadow: 2px 2px 5px black;
}
h5 {    
    color: royalblue;
    text-align: center;
    text-shadow: 2px 2px 5px black;
}
h6 {    
    text-align: center;
    text-shadow: 2px 2px 5px black;
}
h7 {    
    color: red;
    text-align: left;
    text-shadow: 2px 2px 5px black;
}

</style>
<body>

<h1>Do you think you can survive?</h1>

<h1 id = "name">Welcome</h1>


<h6>
    <button class="button button4" onclick = "StoryStart()">Wake Up</button>
    <button class="button button4" onclick = "Chapter1()">Chapter 1</button>
    <button class="button button4" onclick = "Chapter2()">Chapter 2</button>
    <button class="button button4" onclick = "Chapter3()">Chapter 3</button>
    <button class="button button4" onclick = "Chapter4()">Chapter 4</button>
    <button class="button button4" onclick = "Chapter5()">Chapter 5</button>
    </h6>
    
<h1>
    <button class="button button2" onclick = "Hp()">Use First-Aid Kit</button>
<button class="button button2" onclick = "Restart()">Restart</button>
<button class="button button2" onclick = "Cheats()">Use Cheats</button>
</h1>

<h1><button class="button button3" onclick="Credits()">Credits</button></h1>

<h3>Shop</h3>

<p> <button class="button button1" onclick="buyK()">Buy Key</button>
<button class="button button1" onclick="BuyFirstAid()">Buy First-Aid Kit</button>
<button class="button button1" onclick="BuyMap()">Buy Empty Map</button>
<button class="button button1" onclick="BuyFluid()">Buy Lighter Fluid</button>
<button class="button button1" onclick="BuyBottle()">Buy Weird Liquid in Bottle</button>
</p>
<p>
    <button class="button button1" onclick="BuyKnife()">Buy Knife</button>
    <button class="button button1" onclick="BuySword()">Buy Sword</button>
    <button class="button button1" onclick="BuyAxe()">Buy Axe</button>
    <button class="button button1" onclick="BuyMachete()">Buy Machete</button>
</p>
<p>
    <button class="button button1" onclick="Sell()">Sell your Useless Shit</button>
</p>

<h2>Inventory</h2>
<h2 id="Inventory" onmousedown="Value()" onmouseup="Inventory()">
Empty Lighter
</h2>

<p id = "feedback"></p>
<p id = "dollars"></p>
<p id = "value"></p>
<p id = "Restart"></p>
<p id = "name"></p>
<p id = "HP&Dollars"></p>
<p id = "Choices"></p>
<p id = "Health" Health()></p>
<p id = "achievementUnlocked"></p>
<p id = "$"></p>

<audio id="myAudio">
    <source src="Forest.mp3" type="audio/mpeg">
</audio>

<h7>Note: Audio will not work if you haven't downloaded it.</h7>

<h7><button class="button button5" onclick="playAudio()" type="button">Play Audio</button></h7>
<h7><button class="button button5" onclick="pauseAudio()" type="button">Pause Audio</button></h7>

<script>

var gameForm =  ' Your Input:<input type="text" id="answer"> <input type ="button" id ="enter" onclick="yourMove()" value = "enter">';
var randomNumber = Math.floor(Math.random()* 100 + 1);
var text = "";
var message = [];
var HP = 20;
var MaxHP = 20;
var firstaid = 0;
var key = 0;
var inventory = ["nothing"];
var dollars = 0;
var maxtries = Math.floor(Math.random() * 5+3);
var UserInput = 0;
var tries = 0;
var name;
var value;
var person;
var sell;
var sanity = 20;
var Maxsanity = 20;

var fluid = 0;
var bottle = 0;
var Knife = 0;
var Sword = 0;
var Axe = 0;
var Machete = 0;
var emptymap = 0;
var FullLighter = 0;
var emptylighter= 0;

var Lightsaber = 0; //cheat
var Pistol = 0; //cheat
var RayGun = 0; //cheat
var cheatmap = 0; //cheat
var Excalibur = 0;//cheat
var Sharur = 0; //cheat
var x = document.getElementById("myAudio");


function playAudio() {
   x.play();
}

function pauseAudio() {
   x.pause();
}

function Update(){
    document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;
}

function Inventory() {
var text=" "
for (i=0 ; i < inventory.length; i++) {
text += i + 1 + ": " + inventory[i] + "<br>" + "<br>" ;
document.getElementById("Inventory").innerHTML = text //displays inventory
}}

function value() {
var text=" "
for (i=0 ; i < inventory.length; i++) {
text += value[i] + " dollars<br>" + "<br>" ;
document.getElementById("Inventory").innerHTML = text //displays Value of Inventory item
}}

function BuyFirstAid(){//want to buy a First-Aid kits
        if (dollars > 9){//are you to broke
            if (confirm("This will allows you to heal 5 hit points\nWould you like to buy a First-Aid Kit for 10 dollars?\nDon't forget to click on the Inventory to update it!")==true){//are yo sure
                firstaid += 1;//gives you one
                dollars -= 10;//takes your money
                inventory.push(firstaid + "First-Aid")//gives you the Key
                alert ("You now have "+ firstaid + " First-Aid Kits");//you have this meny now
                document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;//]Updates Display
                }}
                else{
                alert ("You need a least 10 Dollars to buy this item")}}//to broke


function BuyAxe(){//want to buy a First-Aid kits
    if (Axe == 0);
        if (dollars > 29){//are you to broke
            if (confirm("You will now have an Axe\nWould you like to buy an Axe for 30 dollars?\nDon't forget to click on the Inventory to update it!")==true){//are yo sure
                Axe += 1;//gives you one
                dollars -= 30;//takes your money
                inventory.push("Axe")//gives you the Key
               value.push (15)//how much its worth
                alert ("You now have "+ Axe + " Axe.");//you have this meny now
                document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;//]Updates Display
                }}
                else{
                alert ("You need a least 30 Dollars to buy this item")}}//to broke

function BuySword(){//want to buy a First-Aid kits
    if (Sword == 0);
        if (dollars > 19){//are you to broke
            if (confirm("You will now have a Sword\nWould you like to buy a Sword for 20 dollars?\nDon't forget to click on the Inventory to update it!")==true){//are yo sure
                Sword += 1;//gives you one
                dollars -= 20;//takes your money
                inventory.push("Sword")//gives you the Key
               value.push (10)//how much its worth
                alert ("You now have "+ Sword + " Sword.");//you have this meny now
                document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;//]Updates Display
                }}
                else{
                alert ("You need a least 20 Dollars to buy this item")}}//to broke

function BuyKnife(){//want to buy a First-Aid kits
    if (Knife == 0);
       if (dollars > 9){//are you to broke
           if (confirm("You will now have a Knife\nWould you like to buy a Knife for 10 dollars?\nDon't forget to click on the Inventory to update it!")==true){//are yo sure
               Knife += 1;//gives you one
               dollars -= 10;//takes your money
            inventory.push("Knife")
            value.push (5)
               alert ("You now have "+ Knife + " Knife.");//you have this meny now
               document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;//]Updates Display
               }}
               else{
               alert ("You need a least 10 Dollars to buy this item")}}//to broke


function BuyMachete(){//want to buy a First-Aid kits
    if (Machete == 0);
        if (dollars > 39){//are you to broke
            if (confirm("You will now have a Machete\nWould you like to buy a Machete for 40 dollars?\nDon't forget to click on the Inventory to update it!")==true){//are yo sure
                Machete += 1;//gives you one
                dollars -= 40;//takes your money
                inventory.push("Machete");
               value.push (20);
                alert ("You now have "+ Machete + " Machete.");//you have this meny now
                document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;//]Updates Display
                }}
                else{
                alert ("You need a least 40 Dollars to buy this item")}}//to broke

function BuyMap(){//want to buy a First-Aid kits
    if (emptymap == 0);
       if (dollars > 4){//are you to broke
           if (confirm("You will now have an Empty Map\nWould you like to buy an Empty Map for 5 dollars?\nDon't forget to click on the Inventory to update it!")==true){//are yo sure
               emptymap += 1;//gives you one
               dollars -= 5;//takes your money
               inventory.push("Empty Map");
               alert ("You now have "+ emptymap + " Empty Map.");//you have this meny now
               document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;//]Updates Display
               }}
               else{
               alert ("You need a least 5 Dollars to buy this item")}}//to broke


function BuyFluid(){//want to buy a First-Aid kits
    if (fluid == 0);
        if (dollars > 4){//are you to broke
            if (confirm("You will now have Lighter Fluid\nWould you like to buy Lighter Fluid for 5 dollars?\nDon't forget to click on the Inventory to update it!")==true){//are yo sure
                fluid += 1;//gives you one
                dollars -= 5;//takes your money
                inventory.push("Lighter Fluid")
                alert ("You now have "+ fluid + " Lighter Fluid.");//you have this meny now
                document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;//]Updates Display
                }}
                else{
                alert ("You need a least 5 Dollars to buy this item")}}//to broke

function BuyBottle(){//want to buy a bottle
        if (dollars > 99){//are you to broke
            if (confirm("You will now have a Weird Liquid in a Bottle\nWould you like to buy a Weird Liquid in a Bottle for 100 dollars?\nDon't forget to click on the Inventory to update it!")==true){//are yo sure
                bottle += 1;//gives you one
                dollars -= 100;//takes your money
                alert ("You now have "+ bottle + "a Weird Liquid in a Bottle.");//you have this meny now
                document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;//]Updates Display
                }}
                else{
                alert ("You need a least 100 Dollars to buy this item")}}//to broke

function buyK() {//Key
   if (key == 0){//only 1
    if (dollars > 59){//you need 60 dollars
        if (confirm("This well alow you to open any safe you find with out picking the lock\nwould you like to buy a Key for 60 dollars\nDon't forget to click on the Inventory to update it!")==true){
            key = 1//you have one now
            dollars -= 60//takes the dollars
            Inventory.push("key")//gives you the Key
            value.push (30)//how much its worth
            Inventory()//updates invatory
            document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;//]Updates Display
            }}
            else{
            alert ("you need a least 60 dollars to buy this item")}}}//ha ha your to broke


function Sell(){//sell your Junk
var UserInput = prompt("What are you looking to sell\nUse the item Id\nDon't forget to click on the Inventory to update it!"+ name, 1 )//what do you want to  sell
var Sub = UserInput -= 1//makes awnser able to be used for arrays
if (Sub >= 0 && UserInput <= inventory.length){
if (confirm("Would you like to sell your "+ inventory[Sub] +" for "+ value[Sub] +" dollars?")==true){//are you sure
       dollars += value[Sub]
    if(inventory[Sub] == "Weird Liquid in Bottle"){
       bottle = 0;}
    if(inventory[Sub] == "Key"){
       key= 0;}
    if(inventory[Sub] == "Knife"){
       Knife = 0;}
    if(inventory[Sub] == "Axe"){
       Axe = 0;}
    if(inventory[Sub] == "First Aid" || "First-Aid" || "FirstAid"){
       firstaid --}
    if(inventory[Sub] == "Machete"){
       Machete = 0;}
    if(inventory[Sub] == "Lighter Fluid"){
           fluid = 0;
        alert("Your loss, you could've filled the Empty Lighter!")}
    if(inventory[Sub] == "Empty Lighter"){
           emptylighter = 0;
        alert("Your loss, you might have needed that later!")}
    if(inventory[Sub] == "Sword"){
           Sword = 0;}
   inventory.splice(Sub, 1);//takes the item away
   value.splice(Sub, 1);//takes value
   Inventory();//updates your inventory
   document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;
}}}

function Cheats(){
    var UserInput=prompt("Enter a cheatcode here" , "Enter Code")//Enter the cheat
    if (UserInput == "~IWantMoneySanta"){
        dollars += 100//isn't santa so nice
        document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;}//]Updates Display
    if (UserInput == "~ItsOver9000!"){//DBZ Refance
    MaxHP += 9000//Upgrades you Hp
    document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;}//]Updates Display
    if(UserInput == "~INeedHP"){
    HP = MaxHP//restorces HP
    document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;}//]Updates Display
    if(UserInput == "~Slice&Dice"){
    inventory.push("Light Saber")
    value.push(0)//cheats aren't worth anything
    Lightsaber = 1;}
    if(UserInput == "~BlackOps2:Zombies"){
    inventory.push("Ray Gun")
    value.push(0)//cheats aren't worth anything
    RayGun = 1;}
    if(UserInput == "~IWannaShootYouAll"){
    inventory.push("Pistol")
    value.push(0)//cheats aren't worth anything
    Pistol = 1;}
    if(UserInput == "~ImTheMapImTheMap"){
    inventory.push("Cheat Map")
    value.push(0)//cheats aren't worth anything
    cheatmap = 1;}
        if(UserInput == "~TheRoyalPrat"){
    inventory.push("Excalibur")
    value.push(0)//cheats aren't worth anything
    Excalibur = 1;}
        if(UserInput == "~SmasherOfThousands"){
    inventory.push("Sharur")
    value.push(0)//cheats aren't worth anything
    Sharur = 1;}

        if(UserInput == "~Pizza"){
    inventory.push("Jayjohn (Distraction)")
    value.push(0)//cheats aren't worth anything
     = 1;}

        if(UserInput == "~"){
    inventory.push("")
    value.push(0)//cheats aren't worth anything
     = 1;}

        if(UserInput == "~"){
    inventory.push("")
    value.push(0)//cheats aren't worth anything
     = 1;}

        if(UserInput == "~"){
    inventory.push("")
    value.push(0)//cheats aren't worth anything
     = 1;}

        if(UserInput == "~"){
    inventory.push("")
    value.push(0)//cheats aren't worth anything
     = 1;}

        if(UserInput == "~"){
    inventory.push("")
    value.push(0)//cheats aren't worth anything
     = 1;}

        if(UserInput == "~"){
    inventory.push("")
    value.push(0)//cheats aren't worth anything
     = 1;
    

    Inv()}}//you cheater

function Restart() { //code to go back to when the player dies or the page is loaded
alert ("You find yourself stranded in a forest \nYou're not sure how you got there, but that doesn't really matter now.");//intro 1
alert ("You want to escape this unknown place. \nDo you have what it takes to survive?");//intro 2
name = prompt("What is your name?" , "Blair");//Lets the player set their name
value = [20];//sets value for 1st inventory item
key = 0;//tells the game to get rid of the Skeleton Key if you have it
HP = 20;//Resets Hit Points
MaxHP = 20; //resets Max HP
bottle = 0; //resets bottles
firstaid = 0;//the number of first-aid kits the player has
dollars = 5;//the amount of dollars the player has
Update();
inventory = ["Empty Lighter"]; //starter inventory
document.getElementById("name").innerHTML = "Welcome " + name ;
} //wecomes the player on the page

function Hp() {//use first aid kit Button
if (firstaid > 0 && HP < MaxHP){//if your ingered and you have first-ad kits
        if (confirm("Would you like to use a First-Aid kit \nYou have " + firstaid + " left") == true){//are you sure?
        alert("You gained 5 life.\nDon't forget to click on the Inventory to update it!")//the game asks the player if he wants to heal
        HP += 5//adds 5 life
        firstaid--//on less first-aid kit
        document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;//]Updates Display
        if (HP > MaxHP){
        HP=MaxHP //cant go over max life
        document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;}}}//]Updates Display

}

var choices4 = ["Run", "Hide", "Walk"];
var choices3 = ["Path", "Forest"];
var choices2 = ["Bathroom", "Kitchen", "Living Room"];
var choices1 = ["", "", ""];
var choices = ["", "", ""];

Hp()

function Story() {
   alert("You open you eyes to find yourself no longer in your home.\nYou attempt to recollect yourself, but you get distracted by the blood on you.");
   alert("You're unsure if it is your own blood or someone else's but you shake that thought out of your head.");
       if (confirm("Do you want to try to remember what happened before you woke up here?")==true) {
           alert("You tried to remember anything, but you only got a headache from trying.");
           alert("You took 1 Damage!");
               HP -= 1;
               alert("You have " + HP + "/" + MaxHP + " hit points left");
            
    } else {
   alert("You decided not to bother. If you don't even know where you are, how could you possibly remember what you did last?");
   }
}

function Story1(){
    if (confirm("You look around and see a note\nGrab the note?")==true) {
        alert("You pick up the note.");
       alert("The note reads:\n'Hello " + name + ", if you are reading this; it means It hasn't killed you.\nYou might not remember me or what you did.'");
       alert("'Of course, that only makes this more fun. Right now you are being watched.\nNever forget you are being watched for one second, you will lose.'");
       alert("'The only way out is for you to understand what these numbers mean:\n082715\nFind the meaning, and you will live.'");
    
    } else {
        alert("You decide it might not be for you and none of your concern.\n...\nYou got curious so you decide to read it anyway.");
        alert("You pick up the note.");
        alert("The note reads:\n'Hello " + name + ", if you are reading this; it means It hasn't killed you.\nYou might not remember me or what you did.'");
       alert("'Of course, that only makes this more fun. Right now you are being watched.\nNever forget you are being watched for one second, you will lose.'");
       alert("'The only way out is for you to understand what these numbers mean:\n082715\nFind the meaning, and you will live.'");
        }
}

function Story2() {
  
   choices4 = prompt("The moment you get done with readng the note, you hear shuffling in the bushes.\nWhat is it? Will it kill you? What will you do?\nRun\nHide\nWalk", "Choose your outcome...");
   if (choices4 == null || choices4 == "" || choices4 == "Choose your outcome...") {
       alert("You just stood there waiting for whatever it was in the bushes to come out.\nYou wait to see what comes out.");
        alert("The bush slowly but surely comes to a hault\nSlowly a little rabbit comes out.");
        alert("You adore the small rabbit as it looks up at you with big blue eyes.");
        alert("You approach the rabbit, trying not to scare it. You slowly outstretch your hand to pet it.");
        alert("The rabbit suddenly gets up onto its hind legs to smell your hand.");
        alert("All of a sudden the rabbit turns into a blood thirsty fat rabbit with larger claws then an eagle.");
        alert("Alarmed, you bring in your arm away from the rabbit.");
        alert("Before you could even think, you ran throughout the forest\nafraid of what it could do to you.");
        alert("You lost some Sanity!")
        sanity --;
        alert("You now have " + sanity + "/" + Maxsanity + " Sanity left");
        alert("You're out of breath, but you're glad anyhow that whatever it was didn't follow you.");
        alert("You find one of those Time Capsule boxes, but it looks like a metal Lunch Box.");
        alert("You opened the Time Capsule.")
        alert("You found 10 dollars, a doll, and a random button.\nYou find the only thing useful was the money, so you took that.")
        dollars += 10;
        document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;//]Updates Display

    } else if (choices4 == "Run" || choices4 == "run"){
        alert("You ran throughout the forest, afraid of what could have been in the bushes.");
        alert("You're out of breath, but somehow you feel better.");
        alert("You're out of breath, but you're glad anyhow that whatever it was didn't follow you.");
        alert("You find one of those Time Capsule boxes, but it looks like a metal Lunch Box.");
        alert("You opened the Time Capsule.")
        alert("You found 10 dollars, a doll, and a random button.\nYou find the only thing useful was the money, so you took that.")
        dollars += 10;
        document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;//]Updates Display

   } else if (choices4 == "Hide" || choices4 == "hide") {
        alert("You hid behind a random tree to be as far away from the shaking bush.");
        alert("The bush slowly but surely comes to a hault\nSlowly a little rabbit comes out.");
        alert("You adore the small rabbit as it looks up at you with big blue eyes.");
        alert("You approach the rabbit, trying not to scare it. You slowly outstretch your hand to pet it.");
        alert("The rabbit suddenly gets up onto its hind legs to smell your hand.");
        alert("All of a sudden the rabbit turns into a blood thirsty fat rabbit with larger claws then an eagle.");
        alert("Alarmed, you bring in your arm away from the rabbit.");
        alert("Before you could even think, you ran throughout the forest\nafraid of what it could do to you.");
        alert("You lost some Sanity!")
        sanity --;
        alert("You now have " + sanity + "/" + Maxsanity + " Sanity left");
        alert("You're out of breath, but you're glad anyhow that whatever it was didn't follow you.");
        alert("You find one of those Time Capsule boxes, but it looks like a metal Lunch Box.");
        alert("You opened the Time Capsule.")
        alert("You found 10 dollars, a doll, and a random button.\nYou find the only thing useful was the money, so you took that.")
        dollars += 10;
        document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;//]Updates Display

    } else if (choices4 == "Walk" || choices4 == "walk"){
        alert("You slowly walked away, paying no mind to the heavily shaking bush.");
        alert("The bush slowly but surely comes to a hault, which catches your attention.\nSlowly a little rabbit comes out.");
        alert("You adore the small rabbit as it looks up at you with big blue eyes.");
        alert("You approach the rabbit, trying not to scare it. You slowly outstretch your hand to pet it.");
        alert("The rabbit suddenly gets up onto its hind legs to smell your hand.");
        alert("All of a sudden the rabbit turns into a blood thirsty fat rabbit with larger claws then an eagle.");
        alert("Alarmed, you bring in your arm away from the rabbit.");
        alert("Before you could even think, you ran throughout the forest\nafraid of what it could do to you.");
        alert("You lost some Sanity!")
        sanity --;
        alert("You now have " + sanity + "/" + Maxsanity + " Sanity left");
        alert("You're out of breath, but you're glad anyhow that whatever it was didn't follow you.");
        alert("You find one of those Time Capsule boxes, but it looks like a metal Lunch Box.");
        alert("You opened the Time Capsule.")
        alert("You found 10 dollars, a doll, and a random button.\nYou find the only thing useful was the money, so you took that.")
        dollars += 10;
        document.getElementById("HP&Dollars").innerHTML = "Hp: "+HP +"/"+ MaxHP +" || Dollars: " + dollars + " || Sanity: " + sanity + "/" + Maxsanity;//]Updates Display
    }

   document.getElementById("Choices").innerHTML = text;
}

function Story3(){
    alert("You throw the Time Capsule behind you and go on your way.");
    choices3 = prompt("You look forward, you see a very narrow, destroyed path.\nDo you want to go down the path go off into the forest?",  "Choose your outcome...");
    if (choices3 == null || choices3 == "" || choices3 == "Choose your outcome...") {
        alert("You aren't sure which one to go with, so you decided to settle with the path.");
        alert("As you walk down the path, you get that irritating feeling like someone is watching you.\nYou remember what the note said: 'Never forget you are being watched for one second, you will lose.'");
        alert("Simply remembering that gruesome letter sendss chills up and down your spine.\nA sudden fog appeared around you. You didn't realize it before because you were lost in thought.");
        alert("You get an uneasy feeling.")
        alert("Out of the corner of your eye, you see a faint figure.\nYou look at the area you saw it, but only fog and faint silhouettes of trees.");
        alert("You shake your head and look forward.")
        alert("All of the sudden, there was a face in the fog.\nLike a curious dog, the face slowly turned its head 45 degrees to the left.")
        alert("Shaking, you start to run\nYou come across a house a little off the path. You look behind you, the face still visible.")
        alert("You run to the house, and open the door.\nYou slam the door shut, locking it, afraid the face could come inside.")
        alert("Achievement Unlocked:\nEnter the Goldfarb House");
}
    else if(choices3 == "Path" || choices3 == "path" ){
        alert("You decided to head down the Path. The Forest might not be your best bet of getting out of here.");
        alert("As you walk down the path, you get that irritating feeling like someone is watching you.\nYou remember what the note said: 'Never forget you are being watched for one second, you will lose.'");
        alert("Simply remembering that gruesome letter sends chills up and down your spine.\nA sudden fog appeared around you. You didn't realize it before because you were lost in thought.");
        alert("You get an uneasy feeling.")
        alert("Out of the corner of your eye, you see a faint figure.\nYou look at the area you saw it, but only fog and faint silhouettes of trees.");
        alert("You shake your head and look forward.")
        alert("All of the sudden, there was a face in the fog.\nLike a curious dog, the face slowly turned its head 45 degrees to the left.")
        alert("Shaking, you start to run\nYou come across a house a little off the path. You look behind you, the face still visible.")
        alert("You run to the house, and open the door.\nYou slam the door shut, locking it, afraid the face could come inside.")
        alert("Achievement Unlocked:\nEnter the Goldfarb House");
}
    else if(choices3 == "Forest" || choices3 == "Forest" ){
        alert("You look at the path and decide it's a bit unsafe how it leads to almost nowhere\nYou take off walking into the forest.")
        alert("As you walk into the Forest, you get that irritating feeling like someone is watching you.\nYou remember what the note said: 'Never forget you are being watched for one second, you will lose.'");
        alert("Simply remembering that gruesome letter sends chills up and down your spine.\nA sudden fog appeared around you. You didn't realize it before because you were lost in thought.");
        alert("You get an uneasy feeling.\nYou notice you're on the path, which confuses you. How did you get on the path if you never went on it to begin with?")
        alert("You decide not to bother; why should you? Obviously something wanted you to be on the path")
        alert("Out of the corner of your eye, you see a faint figure.\nYou look at the area you saw it, but only fog and faint silhouettes of trees.");
        alert("You shake your head and look forward.")
        alert("All of the sudden, there was a face in the fog.\nLike a curious dog, the face slowly turned its head 45 degrees to the left.")
        alert("Shaking, you start to run\nYou come across a house a little off the path. You look behind you, the face still visible.")
        alert("You run to the house, and open the door.\nYou slam the door shut, locking it, afraid the face could come inside.")
        alert("Achievement Unlocked:\nEnter the Goldfarb House");
}

}

function Story4(){
    alert("If you have never been in a creepy house that gave you the most horrid sight, well this house changed that.")
    alert("You look outside the window and the very thick fog. You can no longer see the silhouettes of trees anymore.")
    choices2 = prompt("Well, you're not planning on going out soon, so you prepare to look around the house.\nWhere will you start?\nBathroom, Kitchen, or the Living Room?", "Choose Wisely..")
    if (choices2 == null || choices2 == "" || choices2 == "Choose Wisely.."){
        alert("You couldn't choose, so you decided to go up the stairs.")
        choices = prompt("There was three options:\mthe children's bedroom labled 'Ava' in a bright pink and orange color;\nanother bedroom that had two skulls under the name 'Logan' who is most likely a teen,\nand the last room was a master bedroom which was pobably owned by the parents.", "Ava's Room, Logan's Room, or Parent's Room")
        if (choices == null || choices == "" || choices == "Choose Wisely.."){

        } else if(choices == "Ava's Room" || choices == "Avas Room" || choices == "ava's room" || choices == "avas room"){
            alert("Testing");
        }
        } else if(choices == "" || choices == "" || choices == "" || choices == ""){
            
        } else (choices == "" || choices == "" || choices == "" || choices == "");{
            
        
    } if (choices2 == "Bathroom" || choices2 == "bathroom"){
        alert("You walk into the ")
    }
}



function Story5(){
alert("This part of the story isn't done yet. Please try again at another time!")
}

function StoryStart(){
   Story();
   Story1();
    Health();
    Story2();
}

function Chapter1(){
    Story3();
    Story4();
}

function Chapter2(){
    Story5();
}

function Chapter3(){
    Story5();
}

function Chapter4(){
    Story5();
}

function Chapter5(){
    Story5();
}

function Health(){
if (Hp == 0) {
    alert("Game Over")//sorry play again
        Restart()//restarts the game
}
}

function Credits(){//Who made it
alert("Forest Survival: Choose Your Adventure Made By\nJazmine Farr, Jayjohn Clark, and Nancy Nusbaum");
}

Restart();//starts the game
Inventory();//sets inventory display
Health();

</script>
</head>
</body>
</html>


