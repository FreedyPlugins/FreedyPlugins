FreedyMinigameMaker2 is a script-type minigame creation plugin.  
Executing a command is the basic principle.  

```
on move
    print "You moved!"
```
It works this way.  

```
on move {
    print ( "You moved!" )
}
```
All source code above and below works fine.  
This code sends a message when the player moves.  

Here `print` is called `command`.  
And `move` in `on move` is called `event`.  
Commands within curly braces, or commands under events, are called 'bundles'.  
And these are collectively called 'source code', 'code', and 'syntax'.  

`move` is an `event` that executes the code below when it is moved.  
`print` is a `command` to send the next message to the player.  
`{ }` `( )` The parentheses and curly braces mark the end of the sentence.  
`""` `''` Quotation marks are used to separate non-command message characters.  

Braces and parentheses must be preceded and followed by spaces.  
`print("hello")`(X) `print ( "hello" )`(O)    
`{print "hello"}`(X) `{ print "hello" }`(O)  

---

## Minigames and commands

I'll call the 'mini-game' a 'game'.    
There is a hub game, a game that automatically joins when you enter the server.    
You cannot exit this game other than by exiting the server.  
To join a non-hub game, you must not be in a non-hub game.  

`/fmg create <game name>` Creates a game. Game names must not contain illegal characters. Spaces are allowed.  

`/fmg delete <game name>` Deletes a game.  

`/fmg reload [gamename]` Reloads all games or specific game files.  

`/fmg join <game name>` Join the game.  

`/fmg quit <game name>` Leaves the game.  

Save the `/fmg save` variable.  

`/fmg game` List the existing games.  

`/fmg do <bundle name>` Run the bundle in the hub game.  

Run the `/fmg run <command>` command.  

---

## event

### Join
When a player enters the server  

### Left
When a player leaves the server  

### Pre-game join
Before the player enters the game  

### Game join
When a player enters the game  

### Pre game left
before a player leaves the game  

### Game left
When a player leaves the game  

### Pre game stop
Before the minigame is disabled because there are no players  

### Game stop
When the minigame is disabled because there are no players  

### Interact
when the player interacts  

| name | Category | Description |
|--------------|--------------|--------------|
| interactAction | data | Click Type |
| interactHand | data | hand type |
| interactBlockFace | data | block direction |
| interactBlock | block | Clicked Block |
| interactItem | item | Clicked Item |

### Move
when the player moves  

| name | Category | Description |
|--------------|--------------|--------------|
| moveFrom | Location | Previous location |
| moveTo | Location | Next location |

### Chat
when the player chats  

| name | Category | Description |
|--------------|--------------|--------------|
| chat | data | chat message |

### Command
When the player executes a command  

| name | Category | Description |
|--------------|--------------|--------------|
| command | data | command entered |

### Inventory click
When the player clicks on the inventory  

| name | Category | Description |
|--------------|--------------|--------------|
| inventoryClicked | inventory | Clicked Inventory |
| inventoryHotBar | data | Hot Bar 9 Slot |
| inventoryCursor | item | items in hand |
| inventoryCurrentItem | item | Items in Inventory |
| inventoryAction | data | Click Type |
| inventoryClick | data | Click Type 2 |
| inventoryRawSlot | data | slot location |
| inventorySlotType | data | Types of slots |
| inventorySlot | data | slot position 2 |

### Inventory close
When a player closes their inventory  

| name | Category | Description |
|--------------|--------------|--------------|
| inventoryClosed | inventory | Closed Inventory |

### Attack
When a player attacks an entity  

| name | Category | Description |
|--------------|--------------|--------------|
| damage | data | Damage figures |
| damageCause | data | Damage Cause |
| damageFinal | data | final calculated figure |
| entityUuid | data | Entity UUID |

### Damage
When a player takes damage from an entity  

| name | Category | Description |
|--------------|--------------|--------------|
| damage | data | Damage figures |
| damageCause | data | Damage Cause |
| damageFinal | data | final calculated figure |
| attackUuid | data | Player UUID |


### Player damage
When a player takes damage  

| name | Category | Description |
|--------------|--------------|--------------|
| damage | data | Damage figures |
| damageCause | data | Damage Cause |
| damageFinal | data | final calculated figure |

### Drop item
When a player drops an item  

| name | Category | Description |
|--------------|--------------|--------------|
| dropItem | item | Dropped Items |

### Teleport
when the player teleports  

| name | Category | Description |
|--------------|--------------|--------------|
| teleportFrom | Location | Previous location |
| teleportTo | Location | Next location |

### Swap hand
When the player switches right and left hands with the F key  

| name | Category | Description |
|--------------|--------------|--------------|
| mainHandItem | item | right hand item |
| offHandItem | item | left hand items |

### block break
When a player breaks a block  

| name | Category | Description |
|--------------|--------------|--------------|
| blockBreak | block | crushed blocks |

### Block place
When the player places blocks  

| name | Category | Description |
|--------------|--------------|--------------|
| blockPlace | block | installed blocks |


---

## Command

### data modifier

    // This is a modifier to express where data is stored.  
    //all is per file and stored permanently  
    //game is a game unit and is destroyed when the game is deactivated  
    //player is the player and game unit and is destroyed when the game is deactivated or the player leaves the game  
    //Most of them have this meaning, but the modifier all of the target has the meaning of checking all  


### Math Operations

    cos 5 //print the trigonometric cosine of the angle
    sin 5 //print the trigonometric sine of the angle
    tan 5 //print the trigonometric tangent of the angle
    ( 1 + 1 ) // Outputs the sum of two values
    ( 1 - 1 ) // Output the value obtained by subtracting two values
    ( 1 * 1 ) // Output the product of two values
    ( 1 / 1 ) // Output the value obtained by dividing two values
    ( 1 % 1 ) /prints the remainder of dividing two values
    //If you want to count more than 2, you have to do something like ( ( 1 + 1 ) + 1 )


### Data
`aliases: [ data, var ]`

    <game or all or player> data ( some ) // print some data
    <game or all or player> set data ( some | Hello ) //set some data

### List

    <game or all or player> add list ( play | Hello ) // Add a message to the list
    <game or all or player> set list ( play | 0 | Hello ) // set message 0 to a certain list
    <game or all or player> clear list ( play ) // clear the list
    <game or all or player> size list ( play ) // Print the number of messages in the list
    <game or all or player> contains list ( play | Hello ) // Print whether there are any messages in the list
    <game or all or player> remove list ( play | Hello ) // Remove the message from the list
    <game or all or player> shuffle list ( play ) // Shuffle the list

### Location

    <game or all or player> create location ( spawn | world | 0 | 0 | 0 ) //save x-coordinate 0, y-coordinate 0, z-coordinate 0 location in world world
    <game or all or player> create location ( spawn | world | 0 | 0 | 0 | 90 | 0 ) //save the x-coordinate 0, y-coordinate 0, z-coordinate 0, yaw 90, pitch 0 location in the world world
    <game or all or player> set posX location ( spawn | 10 ) // set the X coordinate of the location
    <game or all or player> set posY location ( spawn | 10 ) // Set the Y coordinate of the location
    <game or all or player> set posZ location ( spawn | 10 ) // Set the Z coordinate of the location
    <game or all or player> set posYaw location ( spawn | 10 )
    <game or all or player> set posPitch location ( spawn | 10 ) // set the pitch of the location
    <game or all or player> clone location ( player | spawn ) // clone location to another location
    <game or all or player> add location ( spawn | 0 | 10 | 0 ) //Add x-coordinate 0, y-coordinate 10, z-coordinate 0 to the location
    <game or all or player> remove location ( spawn ) // remove location
    <game or all or player> exists location ( spawn ) //prints whether location exists
    <game or all or player> equals location ( spawn | player ) //prints whether the two locations are equal to each other
    <game or all or player> contains location ( spawn | <game or all or player> pos_A | <game or all or player> pos_B ) // print if the location is inside the rectangle of both locations
    <game or all or player> get block ( spawn | <game or player> blockName ) // Save the block at location

### Block

    <game or player> set block ( blockName | <game or all or player> spawnPoint ) // Save the block location
    <game or player> get location block ( blockName | <game or all or player> spawnPoint // Save block location
    <game or player> set block ( blockName | code 5 | 1 )
    <game or player> code block ( blockName ) /prints the block code

### Item

    set <game or all or player> item ( itemName | code 35:5 )
    lore add <game or all or player> item ( itemName | "item description" ) //add a lore to the item
    lore set <game or all or player> item ( itemName | 0 | "item description" ) //set the lore on the item
    name set <game or all or player> item ( itemName | "item name" ) // set the display name of the item
    exists <game or all or player> item ( itemName ) // Prints whether the item exists

### Inventory

    <game or all or player> create inventory ( menu_1 | 54 | "menu title" )
    <game or all or player> create inventory ( menu_1 | HOPPER | "menu title" ) //Create an inventory of type
    <game or all or player> set inventory ( menu_1 | 0 | <game or all or player> itemName )
    <game or all or player> add inventory ( menu_1 | <game or all or player> itemname ) // Add item to inventory
    <game or all or player> open inventory ( menu_1 ) // Open the inventory to the player
    <game or all or player> size inventory ( menu_1 ) // Print the number of inventory spaces
    <game or all or player> equals inventory ( menu_1 | player ) // Prints whether the two inventories are equal to each other
    <game or all or player> exists inventory ( menu_1 ) // Prints whether the inventory exists
    <game or all or player> clear inventory ( menu_1 ) //Delete all items in the inventory
    <game or all or player> clone inventory ( menu_1 | player ) // Clone the inventory to another inventory
    <game or all or player> remove inventory ( menu_1 ) //Delete inventory
    <game or all or player> close inventory // Close the player's inventory
    <game or all or player> get item inventory ( player | hotbar | <game or all or player> testItem ) // Store the slot of the item the player is holding in the item
    // Google InventoryType <server version> spigot to find all inventory types

### Target

    name target ( Notch ) set helath 20 //run the following command with the player with any name
    target ( player uuid ) set food 20 // Execute the following command as the player with UUID
    all target ( <game or all or player> play ) {
        add food -1
    } //find players by a list of player names or player UUIDs and run the following command once for all

### Send message
`aliases: [ send, sendmessage, message, msg, print, say, sendmsg ]`

    print Hello // send a message to the player
    game print Hello // Send a message to all players participating in the game
    all print Hello // Send a message to all players participating in the server

### Broadcast
`aliases: broadcast, broadcastmessage, announce`

    broadcast Hello // Send a message to all servers

### ActionBar
`aliases: sendactionbar, actionbar`

    actionbar Hello // send action bar message to player
    game actionbar Hello // Sends an action bar message to all players participating in the game
    all actionbar Hello // Sends an action bar message to all players participating in the server

### BossBar

    <game or player> create bossbar ( testBossBar | WHITE ) //Create a bossbar in any color
    <game or player> open bossbar ( testBossBar ) //Open bossbar to the player
    <game or player> close bossbar ( testBossBar ) //Closes the player's bossbar
    <game or player> remove bossbar ( testBossBar ) //Remove bossbar
    <game or player> set size bossbar ( testBossBar | 1 ) //Set the process bar of the boss bar to a number from 0 to 1
    <game or player> set type bossbar ( testBossBar | SOLID )
    <game or player> set color bossbar ( testBossBar | WHITE ) //Set the color of the bossbar
    <game or player> exists bossbar ( testBossBar ) // Prints whether the boss bar exists
    // Available colors: PINK, BLUE, RED, GREEN, YELLOW, PURPLE, WHITE
    // Possible styles: SOLID, 6, 10, 12, 20 or not

###

    food //print the player's hunger level
    set food 20 //set the player's hunger
    add food 1 //Increase or decrease the player's hunger

### Health

    health //print the player's health
    set health 20 //set the player's health
    add health 20 //Increase or decrease the player's health

### GameMode

    gamemode // output the player's game mode
    set gamemode /sets the player's gamemode

### Name

    player name // print the player's name
    set player name testName //Set the player's display name
    set name tesetName //set the player's tab list display name
    game name // print the name of the game

### Permission

    permission ( op ) // Print whether the player has op or not
    permission ( freedyminigamemaker.admin )
    /print whether the player has node privileges

### Title

    <game or all or player> title ( 0 | 50 | 0 | "title" | "subtitle" )
    //Send the title and subtitle to the player, fade in 0, duration 50, fade out 0

### Sound

    <game or all or player> sound ( "minecraft:block.note.snare" | 1 | 1 )
    //Play a sound to the player at volume 1 and pitch 1

    <game or all or player> sound ( "minecraft:block.note.snare" | -1 | 1 )
    // Tell the player to cancel the change of the sound according to the position and play the sound at pitch 1

### Particles

    particle ( player | FLAME | 10 | true ) // Summon 10 particle effects at the location in a stopped state
    particle ( player | FLAME | 10 ) // Summon 10 particle effects at the location
    // Google Particle <server version> spigot to find all particle effects


### Do

    add potion ( GLOWING | 55555 | 0 ) // Gives level 1 potion effect for the duration (Potion level 1 is 0)
    remove potion ( GLOWING ) // Remove the potion effect
    clear potion // Removes all potion effects
    // Type PottionEffectType <server version> spigot on Google to find all potions

### Sneaking
`aliases: [ sneaking, sneak ]`

    sneaking //prints whether the player is crouching

### Uuid

    player uuid //print the player's unique UUID
    get random uuid //print a random UUID

### Timings

    timings print Hello //Print the execution time of the next command in milliseconds

### MilliSec
`aliases: millisec, millisecond, milliseconds`

    millisec //prints the millisecond timer that started at midnight January 1, 1970

### Random

    random ( 0 | 100 ) // Print a random number with decimals from 0 to 100

### Log

    log hello // send a message to the console window

### Length

    length Hello //print the length of the message

### Int

    int 3.14 // Rounds down to remove the decimal point

### Split

    split ( "1,2,3" | "," | <game or all or player> listName )
    // Split the first message into the second message and store it in the list

### Join

    join testGame // join the player to the game

### Left

    left //Exit the player from the game the player is playing

###

    do start //start Executes the command bundle

### Return

    return false //pass the message to the bundle or event and abort the command
    // For example, if executed in the interact event, the interaction is canceled

### Refs

    refs ( testGame | bundleName )
    // Execute the game's command bundle as the running game

### Async

    async print hello // execute the command asynchronously
    //Async is executed outside the server's action flow, so if the command execution time is long, use async
    // However, asynchronous execution does not flow with other normal executions, so
    // It is recommended not to share data

### Delay

    delay ( 20 ) print hello // After a few ticks, execute the following statement and print the execution code (20 ticks is 1 second)

    async delay ( 20 ) print hello
    //After a few ticks, the following statement is executed asynchronously and the execution code is output.

### CancelTask

    cancel (execution code) //Cancel the statement that was waiting to be executed

### Execute

    player execute command // Let the player execute the command
    execute command // Execute a command in the console

## conditional

```
if ( "first value" = "second value" )
    print "true"
```
A conditional statement is a 'statement' in which 'code' is executed according to a condition.  
```
if ( value1 = value2 ) {
    // If true, it will be executed.
} else {
    // If false, it will be executed.
}
```

The `=` equal sign is called a logical operator'.
`== or =` True when both values are equal.  
`!= or /=` True if the two values are different.  
`<` True if the number on the left is less than the number on the right.  
`>` True if the left hand side is greater than the right hand side number.   
`<=` True if the number on the left is less than or equal to the number on the right.    
`>=` True if the number on the left is greater than or equal to the number on the right.  

```
if ( South Korea /= North Korea ) { print "true." } else { print "false." }
```
```
* Output message when the above code is executed
Oh yeah.
```
The `if` command executes the next command when the condition is true.  
The `else` command executes the next command when the condition is false.  
In the above syntax, `/=` is true when the two values ​​are different, so "true." is output.  
If the two values are equal, "false." will be output because the two values are not different.  

```
if ( "first value" = "second value" )
    if ( "third value" = "fourth value" )
        print The first and second values are the same, the third and fourth values are the same
```
```
if ( "first value" = "second value" & "third value" = "4th value" )
    print The first and second values are the same, the third and fourth values are the same
```
The meaning of the source code above and below is the same.  
Only true if the condition before or after `& or &&` is true.  
`| or ||` is true only if any of the conditions before and after are true.  

---

## loop

```
while ( conditional statement ) {
    // Code here will continue to run as long as the condition is true.
}
```

```
set data ( i | 0 )
while ( data ( i ) < 10 ) {
    print data ( i ) is running
    set data ( i | data ( i ) + 1 )
}
```

```
for (Initial Execution Statement | Conditional Statement | Incremental Statement) {
    //execution statement
}

//execution flow chart:
//0. initial execution statement
//1. If the conditional statement is true, 2 is executed; otherwise, 5 is executed.
//2. Execution statement
//3. increase/decrease syntax
//4. go to 1
//5. Terminate the command.
```

```
for ( set data ( i | 0 ) | data ( i ) < 10 | set data ( i | data ( i ) + 1 ) ) {
    print data ( i ) is running
}
```

---