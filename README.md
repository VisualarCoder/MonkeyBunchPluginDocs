# MonkeyBunchPluginDocs
Welcome to the **Monkey Bunch Plugin Documentation!**, here you will be able to find everything you need to create your first Monkey Bunch Plugin!
Monkey Bunch's Plugin system uses the lua coding language, if you wonder why? its because its easy for beginners and because I am too lazy to make a C# one!!

## Get Started
Create a .lua file and open it in your IDE of choice, Make sure it is inside of a folder called "MonkeyBunchPlugins" in your documents folder, And get coding! all of the official functions for the Update, OnApplicationQuit, etc. Functions are shown below.

## Functions
**GameTick** - Similar to the unity **Update()** function, gets called every frame/game tick.

**OnAppQuit** - Similar to the unity **OnApplicationQuit()** function, gets called whenever the game quits.

## Scripts

### Debugging
**Log** - Logs a message to the console. (you can also use print)

**LogError** - Logs a error to the console.

**LogWarning** - Logs a warning to the console.

### Objects
**CreateMonkeyObject** - Similar to creating a gameObject in unity, Paramaters: (**(string : objectName)**), Out: (**(MonkeyObject : object)**)

**GetObject** - Similar to the GameObject.Find function in unity, Paramaters: (**(string : objectName)**), Out: (**(MonkeyObject : object)**)

**SetParent** - Similar to the GameObject.SetParent function in unity, Paramaters: (**(MonkeyObject : object), (MonkeyObject : newParent), (bool : worldPositionStays)**)

**SetActive** - Similar to the GameObject.SetActive function in unity, Paramaters: (**(MonkeyObject : object), (bool : state)**)

**GetName** - Similar to the GameObject.name variable in unity, Paramaters: (**(MonkeyObject : object)**), Out: (**(string : objectName)**)

## Debugging
To debug your plugin, you will need access to the Spectator Camera, if you do **not** have access to it, I dont know why your here. But, open the debugger window from the top bar in Spectator, and find all of the game's logs and your plugins logs in that window.

## Notice
Currently at this stage, only people with spectator camera access can create custom plugins, but with the **Monkey Bunch Custom Maps SDK** you are able to code in that, but more limited and **very very very limited debugging tools for the custom maps sdk.**.

## Example Script
```lua
Log("This is a normal log message!") -- Logs a message to the console
LogError("This is an error log message!") -- Logs an error to the console
LogWarning("This is a warning log message!") -- Logs a warning log message to the console

-- Create a MonkeyObject from an existing GameObject
local function CreateMonkeyObject(gameObject)
    return MonkeyAPI:CreateMonkeyObject(gameObject)
end

-- Set the parent of a MonkeyObject
local function SetParent(monkeyObject, newParent, worldPositionStays)
    MonkeyAPI:SetParent(monkeyObject, newParent, worldPositionStays)
end

-- Set the active state of a MonkeyObject
local function SetActive(monkeyObject, state)
    MonkeyAPI:SetActive(monkeyObject, state)
end

-- Get the name of the MonkeyObject
local function GetName(monkeyObject)
    return MonkeyAPI:GetName(monkeyObject)
end

-- Move the MonkeyObject to a new position
local function MovePosition(monkeyObject, position)
    MonkeyAPI:MovePosition(monkeyObject, position)
end

-- Gets called every frame
local function GameTick()
    Log("GameTick is running!")

    local forestGameObject = GetObject("Forest") -- Get the Forest GameObject
    local cove = GetObject("TheCove") -- Get the Cove GameObject
    if forestGameObject ~= nil then
        Log("Found forest GameObject!!")

        local pos = Vec3(0, 0, 0)
        local rot = Quat(0, 0, 0, 1)
        local scale = Vec3(1, 1, 1)

        MonkeyAPI:SetActive(forestGameObject, true)
        MonkeyAPI:SetPosition(forestGameObject, pos)
        MonkeyAPI:CreatePrimitiveObject("Cube", pos, rot, scale)
        MonkeyAPI:SetParent(forestGameObject, cove, true)
    else
        LogError("Couldn't find the Forest object!")
    end
end

-- Gets called when Monkey Bunch quits.
local function OnAppQuit()
    Log("OnAppQuit!")
end

-- Register functions
RegisterUpdateFunction(GameTick)
RegisterQuitFunction(OnAppQuit)
