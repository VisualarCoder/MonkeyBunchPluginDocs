# MonkeyBunchPluginDocs
Welcome to the **Monkey Bunch Plugin Documentation!**, here you will be able to find everything you need to create your first Monkey Bunch Plugin!
Monkey Bunch's Plugin system uses the lua coding language, if you wonder why? its because its easy for beginners and because I am too lazy to make a C# one!!

## Get Started
Create a .lua file and open it in your IDE of choice, Make sure it is inside of a folder called "MonkeyBunchPlugins" in your documents folder, And get coding! all of the official functions for the Update, OnApplicationQuit, etc. Functions are shown below.

## Functions
**GameTick** - Similar to the unity **Update()** function, gets called every frame/game tick.

**OnAppQuit** - Similar to the unity **OnApplicationQuit()** function, gets called whenever the game quits.

## Scripts
**Log** - Logs a message to the console. (you can also use print)

**LogError** - Logs a error to the console.

**LogWarning** - Logs a warning to the console.

## Debugging
To debug your plugin, you will need access to the Spectator Camera, if you do **not** have access to it, I dont know why your here. But, open the debugger window from the top bar in Spectator, and find all of the game's logs and your plugins logs in that window.

## Notice
Currently at this stage, only people with spectator camera access can create custom plugins, but with the **Monkey Bunch Custom Maps SDK** you are able to code in that, but more limited and **very very very limited debugging tools for the custom maps sdk.**.
