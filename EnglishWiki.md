## FreedyMinigameMaker
With this plugin, you can create your own minigame from scratch and customize it with your imagination.
So this plugin can be seen as a mini game development tool.
This plugin works by executing commands in certain parts of the gameplay.
It also provides the main mechanism for mini-games to work and has several features.
In addition, you will receive suggestions for plug-in features or error reports. Please contact us.

## Supported features
> Save custom GUi menus, custom kits, custom items, and custom locations

> Send message, title, sound

> Supports various syntax of mini-game commands

> Support timer function of mini game

> Supports mini game data, player data mini game variables

> Math operation support

> And many more features...

## Download
##### [>> Download Link <<](https://github.com/FreedyPlugins/FreedyMinigameMaker/releases/latest/download/FreedyMinigameMaker.jar)

## suggestions and bugs

##### [>> Report link <<](https://github.com/FreedyPlugins/FreedyPlugins/issues/new/choose)
  
## source code

##### [>> Source code link <<](https://github.com/FreedyPlugins/FreedyMinigameMaker/tree/master/FreedyMinigameMaker)
  
***

#### run command

Minigame utility commands have the functions necessary to run minigames.

To check the usage, try entering the fut command as player.


***


## conditional command

Conditional instructions check data and execute other instructions.



`/fut <player> if <value1> == <value2> <command to be executed>`
If value 1 and value 2 are the same, it is a command syntax that executes the command.



`/fut <player> if <value1> /= <value2> <command to be executed>`
If value 1 and value 2 are not the same, it is a command syntax that executes the command.



`/fut <player> if <value1> <<value2> <command to be executed>`
If the value 1 is less than the value 2, it is a command statement that executes the command.



`/fut <player> if <value1>> <value2> <command to be executed>`
If the value 1 is greater than the value 2, it is a command statement that executes the command.



`/fut <player> if <value1> <= <value2> <command to be executed>`
If the value 1 is less than or equal to the value 2, it is a command syntax that executes the command.




`/fut <player> if <value1> >= <value2> <command to be executed>`
If the value 1 is greater than or equal to the value 2, it is a command syntax that executes the command.


`/fut <player> if <value1> == <value2> fut <player> if <value3> == <value4> <command to be executed>`
If the value 1 and the value 2 are the same and the value 3 and the value 4 are the same, it is a command syntax that executes the command.
  


  

`/fut <player> if <value1> == <value2> {do(<command1> && <command2>)}`
If the value 1 and the value 2 are the same, it is a statement that executes command 1 and command 2
  

  
`/fut <player> if <value1> == <value2> {do(<command1> && <command2>)}{else(<command1> && <command2>)}`
If the value 1 and the value 2 are the same, command 1 and command 2 are executed, and if the value 1 and value 2 are not the same, command 3 and command 4 are executed.


> Notification! To execute multiple commands in {do()} or {else()} syntax, put '&&' (a string with'&&' between spaces and spaces) between the command and the command.
>> Attention! Don't put data functions like {add()} or {data()} in {do()} or {else()} statements! fut <player> do player, use data function via <player> run command


## Vanilla command execution

If a command in a minigame configuration, such as a minigame command bundle or event command or repeat command bundle, is a Minecraft default command such as /tp or /say,

Please don't run it right away.

`/fut <player> execute say hello`

You have to do this to work.

## Command block compatibility

When entering the fut command in the command block, commands like @p do not work well.

Of the @s, @p, and so on, only @p works, replacing the nearest player name in a 4 block radius of the command block.



## Start waiting for the mini game

Minigames require at least one player to play.

Minigames with no players are automatically disabled.

And you can set the maximum number of minigames

You can set the starting number of minigames

You can have it start after a few seconds when all the starters are gathered.

## Minigame event

Minigame events are literally triggered by a bundle of event commands when a situation or event occurs.

When the player moves in blocks, you can do the following:

For more details on the event, please refer to the page below.

[Go to Event Bundle](https://freedyplugins.github.io/FreedyPlugins/FreedyMinigameMakerWiki#%EC%9D%B4%EB%B2%A4%ED%8A%B8-%EB%B2%88%EB%93 %A4)

```yaml
miniGames:
  Test mini game:
    maxPlayers: 20
    maxStartPlayers: 2
    waitForStartTime: 100
    moveCmd:
    -fut {player} sendActionBar private {toBlockX} {toBlockY} {toBlockZ}
```

## event cancellation

Used to stop a minigame event from proceeding.

Executing this command cancels the event.

`/fut <player> cancelEvent`

In the command bundle executed with fut <player> do ..., the repeat command bundle {do()}, {else()} is canceled immediately and until the next command, but
In the mini-game event, events such as movement events and block click events are canceled after all commands in the command bundle have been executed.

## repeat command

The repeat command is executed while waiting to start a mini-game or while playing a mini-game.

If you set the repeat command name to wait, it will run when the minigame is waiting to start or when a minigame is playing.

Repeat commands with a name other than wait will only be executed while the minigame is playing.


```yaml
repeats:
  timer:
    time: 20 #repeat command cycle
    cmd: #repeat command bundle
    -fut {player} ...
    -fut {player} ...
```

```yaml
miniGames:
  Test mini game:
    maxPlayers: 20
    maxStartPlayers: 1
    waitForStartTime: 100
    gameTime: 100
    repeatList:
    -wait
    -timer
    repeats:
      timer:
        time: 1
        cmd:
        -fut {player} if {isPlaying} == false fut {player} if {numeric({data(timer)})} == false fut {player} setData timer {constant(gameTime)}
        -fut {player} if {isPlaying} == false fut {player} if {numeric({data(timer)})} == true fut {player} do printBossBar
      wait:
        time: 20
        cmd:
        -fut {player} if {isPlaying} == false fut {player} if {numeric({data(wait)})} == false fut {player} setData wait 5
        -fut {player} if {isPlaying} == false fut {player} if {numeric({data(wait)})} == true fut {player} do printTime
    printTimeCmd:
    -fut {player} sendTitle game 10 50 10 {integer({data(wait)})}
    -fut {player} addData wait -1
    printBossBarCmd:
    -fut {player} sendBossBar game {game} {math(divide, {data(timer)}, {constant(gameTime)})} GREEN {game}
    -fut {player} addData timer -1
    -fut {player} if {data(timer)} <0 fut {player} do stop
    stopCmd:
    -fut {player} sendMsg game The game is over
    -fut {player} shutDown
    quitCmd:
    -fut {player} sendBossBar private {game} 0 GREEN none
```

I've taken this mini game setup as an example.

This is how to set it with a command.

/fmg set test minigame setCmd repeatList 999 wait

/fmg set test minigame msg repeats.time 20

/fmg set test minigame setCmd repeats.cmd 0 fut {player} ...

## Minigame execution command

`/fut <player> join`

`/fut <player> conLog <message>`
Print the message to the console.

`/fut none setFile data.hello yes_hello`
Save the file in data.yml.

`/fut none saveFile`
Save data.yml.

`/fut <player> shutDown`
Force all players out of the mini-game.

`/fut <player> setData <customdata> <data>`
Save minigame data

`/fut <player> addData <customdata> <amount>`
Add to the value of the minigame data.

`/fut <player> setPlayerData <customdata> <data>`
Save the player data of the mini game.

`/fut <player> addPlayerData <customdata> <amount>`
It is added to the value of the player data of the minigame.

`/fut <player> execute <command>`
Vanilla command execution


## Player and entity settings

`/fut <player> health private <health>`
This command sets the player's health.

`/fut <player> food private <hunger>`
This command sets the player's hunger.

`/fut <player> addPotion private SPEED 55555 1`
This command gives the player an infinite speed of 1.

`/fut <player> removePotion private`
This command removes all potions applied to the player.

`/fut <player> closeGui`
This command closes the inventory menu displayed to the player.

`/fut <player> knockBack <x> <y> <z>`
This command gives the player momentum.

`/fut <player> entityKnockBack <entityUuid> <x> <y> <z>`
These commands give momentum to an entity.

`/fut <player> addKnockBack <amount> <yaw> <pitch>`
This command gives the player momentum in some direction.

`/fut <player> entityAddKnockBack <entityUuid> <amount> <yaw> <pitch`
This is a command that gives the entity momentum in some direction.

`/fut <player> setHelmet <customItem>`
This command puts the stored item on the player's head.

`/fut <player> setChestplate <customItem>`
This command puts the stored item on the player's armor.

`/fut <player> setLeggings <customItem>`
This is a command to put the saved item on the player's pants.

`/fut <player> setBoots <customItem>`
This is a command to put the saved item on the player's shoe.

`/fut <player> cursor <cursor>`
This command sets the cursor on 9 spaces of the player's hot bar.

`/fut <player> kill <entityUuid>`
This is a command that deletes an entity without simply killing it.

`/fut <player> damage <entityUuid> <damage>`
This is a command that damages an entity.

`/fut <player> nearByEntities <x> <y> <z> <cmd>`
Execute commands in <cmd> with surrounding entities within the player's range.
`{nearByEntitiyType}`, `{nearByEntitiyName}`, `{nearByEntitiyUUID}`, `{nearByEntitiyDistance}`

`/fut <player> entityNearByEntities <entityUuid> <x> <y> <z> <cmd>`
Execute commands in <cmd> with surrounding entities within a certain range of an entity.
`{entityNearByEntitiyType}`, `{entityNearByEntitiyName}`, `{entityNearByEntitiyUUID}`, `{entityNearByEntitiyDistance}`

`/fut none ride <entityUuid> <passengerUuid>`
The entity rides the entity.

`/fut <player> removeRide`
Get off the boarding entity.

`/fut <player> repairItem`
Repairs the durability of items held by the player.





## kit

Kits are responsible for storing and retrieving inventory from config settings.

`/fmg set none kit create <kit name>`

Saves all items to config in the inventory of the player running this command

And since this kit is stored separately from the minigame, it can be loaded from any minigame.

This is a kit application instruction.

`/fut <player> kit <kit name>`

## save location

Since you need a location to teleport to, you can save the location.

Saved as a minigame constant.

`/fmg set <game name> loc <location name>`

Stores the location of the player executing this command as a constant in a minigame.

This is a teleport command.

`/fut <player> teleport <game name> <location name>`

If the location name is wait, start, or end, it will be automatically teleported when entering, starting, or exiting the mini-game!

## Block Regen

This is a function for reverting changed blocks during mini-games.

`/fut <player> addBlock <world> <x> <y> <z> [blocksName]`

The player executing this command saves the block at the coordinates written to the block storage of the participating minigame. If blocksName is written, it creates a block repository with that name in the minigame.

If the gameType is set to build, blocks are stored in the minigame block repository just before the player installs or destroys them.

This is a command to return a block.

`/fut none resetBlocks <game name> [blocksName]`

If blocksName is written, it reverts to the block in the block store of the minigame.

If blocksName does not exist, it reverts to the block in the minigame's block storage.

## repeat command

If the minigame command contains {allPlayer} or {onlinePlayer}, the command is executed repeatedly multiple times.

{allPlayer} continues to be replaced by the name of the player participating in the minigame, and runs as many times as the number of players participating in the minigame.

{onlinePlayer} runs as many times as the number of server players, continuing to substitute the name of the player participating in the server.

`/fut <player> while {data(index)} <= 5 {do(fut {player} sendMsg private hello!)}`

This command executes the commands inside {do()} until {data(index)} is less than or equal to 5 or less.

And this while command cannot be executed in general command bundles. Because replacing data functions such as {data(index)} is applied to the condition as a constant rather than a variable because it is already substituted before the command is executed, you should use the keeped instruction bundle that does not replace the data function in advance. Keeped bundles need only contain keeped in front of the command bundle. **keeped**!

```yaml
joinCmd:
-fut {player} setData index 0
-fut {player} do keepedWhile
keepedWhileCmd:
-fut {player} while {data(index)} <= 5 {do(fut {player} do final && fut {player} addData index 1)}
finalCmd:
-fut {player} sendMsg public {data(index)}th message
```

Be careful, this command will execute without stopping until the condition is really wrong. If this command runs too long, the server will crash.

## item

Save the item to config and load it.

Save the item to config by item name

`/fmg set none item <item name>`

Load an item in the config by item name

`/fut <player> give <item name> [number of items]`

Gives an item to the player. If your inventory is full, nothing will happen.

`/fut <player> giveHand <item name> [number of items]`

The player holds the item in his hand and puts the item in place.

`/fut <player> giveCursor <item name> <inventory digit> [number of items]`

Overwrites the numbered item in the player's inventory.


## GUI menu

Bring up the GUI inventory menu to the player.

If you modify the inventory item, it will not take effect until you bring up the inventory again.

`/fmg set none inv create inventory name <9|18|27|36|45|54> inventory title`

Create inventory.

`/fmg set none inv addItem <inventory name> <inventory number>`

The items you are holding in a certain inventory are stored in the inventory number.

`/fut <player> gui <inventory name>`

Open the inventory menu.

`/fut <player> setGui <invName> <index> <customItemName>`

The saved item is displayed on the player's GUI menu.

`/fut <player> setGuiItem name <invName> <index> <itemName>`

Edit the item name in the GUI menu.

`/fut <player> setGuiItem name <invName> <index> <line> <loreName>`

Modify the item lower in the GUI menu.

***

#### data functions


## What is a syntax?
This plugin has a lot of syntax.
Wait here!
What is the phrase here?
The syntax is that if you write `{playerName}`, the `player name` is displayed.

If you do `{gameName}`, the name of the mini game appears,
If you do `{playerAmount}`, you will get the number of players, right?

Now let's look at an example.

`/tp {player} 0 0 0`
Suppose you ran this command.
This will replace `{player}` with `the name of the player who executed this command'.
Of course the `/tp` command doesn't really do that.
But! This syntax works for Freedimini Gamemaker plugin.
But! The `/tp` command is a bit more complicated. Shall we take a look?

`/fut {player} teleport private testGame start`

It looks like this...

Let me interpret it.

`/fut {player} teleport private testGame start`
Player tipping personally to the start position stored in the testGame minigame


> To test the syntax, test it with the command below! {allPlayer} {onlinePlayer} only works in the minigame config
 
`/fut <player> execute fut {player} sendMsg private {x}`
  

## syntax list

### `{allPlayer}`
Substitute the names of all players participating in the minigame.
Commands with this syntax are executed for the number of players participating in the minigame.

### `{onlinePlayer}`
Substitute the names of all players participating in the server.
Commands with this syntax are executed for the number of players participating in the server.

### `{playerName}` or `{player}` (both are the same)
It will be replaced with the name of the player who caused this command to be triggered.

### `{playerIndex}`
Replace this command with the participating player listing number of the player who caused this command to be triggered.

### `{maxPlayers}`
It replaces the maximum number of people entering the mini game.

### `{randomPlayer}`
Replaces the name of the player who randomly selected one of the players participating in the mini-game.

### `{playerAmount}`
At the beginning of the minigame, it replaces the number of players participating.

### `{playerSize}`
Replaces the number of players participating in the minigame.

### `{isPlaying}`
Replaces whether the minigame is playing or not. True if true, false if false

### `{isWaiting}`
Replaces whether the minigame is waiting for play or not. True if true, false if false

### `{game}` or `{gameName}` (both are the same)
Replaces the minigame name saved in the config file.

### `{gameType}`
Replaces the type of minigame.

### `{randomNumer}`
Generates a random number that is a rational number between 0 and 1. This is Math.random().

### `{playerIsOp}`
True if the player has an oppie, false otherwise

### `{playerUuid}`
Replace the player's UUID.

### `{x}`
Replaces the player's X coordinate.

### `{y}`
Replaces the player's Y coordinate.

### `{z}`
Replaces the player's Z coordinate.

### `{eyeX}`
Replaces the X coordinate of the player's point of view.

### `{eyeY}`
Replaces the Y coordinate of the player's point of view.

### `{eyeZ}`
Substitute the Z coordinate for the player's point of view.

### `{yaw}`
Replaces the player's cost.

### `{pitch}`
Replaces the player's pitch value.

### `{world}`
Replaces the world name the player is in.

### `{playerName}`
Substitute the player's name. Same as {player}.

### `{playerCursor}`
Replaces the location of the space where the player's hand is.

### `{playerIndex}`
Replaces the number of players the player is in the mini-game. It starts with 0, not 1.

### `{playerHealth}`
Replaces the player's health.

### `{playerFood}`
Replaces the player’s hunger

### `{math(add, 1, 2)}`
Substitute the value of 1 plus 2. Besides add, there are remainder, multiply, and divide.

### `{playerData(testData)}`
Replaced with player data that was saved separately.

### `{data(testData)}`
It is replaced with the minigame data that was saved separately.

### `{miniGamedata(test, isPlaying)}`

Prints whether the test minigame has started. Instead of isPlaying, you can use playerList to display all players participating in the mini-game. Other than that, it is replaced with the minigame data that was saved separately.

### `{color(&aHello)}`
Replace it with green text

### `{numeric(1004)}`
The number 1004 replaces whether it is a number or not

### `{entityLoc(ce5e7f96-6c5d-43c1-a948-1c8c2388e47a)}`
Replace the position of the Uuid entity

### `{topLoc(world, 10, 5, -1)}`
Replace the block coordinate at the highest position among the y coordinates of the block in the above coordinates.

### `{contain(ㅁ, ㄱ, ㄴ, ㄷ, ㄹ, ㅁ)}`
Substitutes for ㅁ among ㄱ, ㄴ, ㄷ, ㄹ, ㅁ

### `{sub(1, 3, hello)}`
Hello, cut from 1 to 3 of the string to replace Hello

### `{blockName(world, 10, 5, -1)}`
Replace the code of the block at the coordinates above

### `{playerList(default)}`
Prints all player names in the minigame. If all is not the default, all online player names are replaced.

###'{add(four, one, two, three)}`
Prints a list of four, two, and three.

### `{remove(one, one, two, three)}`
Prints a list of days, two, and three with days removed.

### `{file(playerPoint-ce5e7f96-6c5d-43c1-a948-1c8c2388e47a)}`
The value with playerPoint in front of the UUID above is retrieved from data.yml. If there is no value, none is displayed. If you attach a dot (.) between a character and a character, the character after the character is saved in the character that precedes it. If only the UUID is put in front of the dot, an error will occur, so any character must be put in front of the UUID.

### `{date(<date format>)}`
https://nowonbun.tistory.com/502

### `{length(abcde)}`
Prints abcde's character length (5).

### `{indexOf(0, 10, 20, 30)}`
Replaces the 0th data out of 10, 20, 30.

### `{valueOf(20, 10, 20, 30)}`
Out of 10, 20, 30, 2 is replaced by replacing the index of 20 data.

### `{sizeOf(one, two, three, four)}`
Replaces the number of lists of days, two, three, four.

### `{shuffle(1, 2, 3)}`
1, 2, 3 are mixed and replaced.

### `{highList(1, 2, 3)}`
Substitutes 3, 2, 1 listed in highest order.

### `{flip(3, 1, 2)}`
Reverse the order and replace 2, 1, 3.

### `{lowestNumber(1, 2, 3)}`
Replace the smallest number.

### `{highestNumber(1, 2, 3)}`
Replaces the largest number.

### `{randomNumber(0, 9)}`
Choose one of the numbers from 0 to 9 and replace it.

### `{random(apple, bread, cheese)}`
Select one of apple, bread, and cheese and replace.

### `{constant(testMessage)}`
Replace with minigame constants saved in the config file.

### `{playerTargetBlock(100)}`
Replaces the position of the block that the player is looking at within 100 blocks.

### `{itemAmount(1)}`
Prints the number of items in the 1st slot in the player's inventory.

### `{itemType(1)}`
Prints the first slot item type in the player's inventory.

### `{replace(hello, hello, goodbye, goodbye, goodbye, goodbye, friends)}`
Replaces the list of all of your friends who changed hello to hello, goodbye, goodbye, goodbye, goodbye.

### `{integer(3.1415926535897932384626)}`
Substitute 3 with the decimal point removed.

### `{abs(-7)}`
If -7 has a minus sign, it replaces the removed value of 7.

### `{cos(3)}`
Substitute the cosine of 3.

### `{sin(3)}`
Substitute the sine value of 3.

### `{tan(3)}`
Substitute the tangent value of 3.

### `{round(3.5)}`
Replaces 4, which is the rounded value of 3.5.

### `{roundUp(3.5)}`
Replaces 4, which is the rounded value of 3.5.

### `roundDown(3.5)}`
Replaces 3, which is the rounded value of 3.5.



***


#### event bundle


**Event bundles execute commands in certain situations**


```yaml
blockBreakCmd:
-fut {player} sendMsg private no!
-fut {player} cancelEvent
```

`preJoinCmd`
Fired just before the player joins the minigame.

`joinCmd`
Fired when the player joins a minigame.

`preQuitCmd`
Fired just before the player leaves the minigame.

`quitCmd`
Fired when the player exits the minigame.

`conStartCmd`
Runs when the minigame is started.

`preConEndCmd`
Runs just before the minigame ends.

`conEndCmd`
The mini-game ends and runs.

`interactCmd` `{actionName} {action} {itemName} {itemDurability} {itemType}`
Fired when a player participating in a minigame clicks or interacts with something other than an entity.

`interactEntityCmd` `{entityName} {entityType} {itemName} {itemDurability} {itemType}`
Fired when a player participating in a minigame clicks an entity.

`moveCmd:` `{fromBlockType} {fromBlockX} {fromBlockY} {fromBlockZ} {fromBlockFace} {fromBlockWorld} {toBlockType} {toBlockX} {toBlockY} {toBlockZ} {toBlockFace} {toBlockWorld}`
Executed when the player participating in the mini-game moves one space by block.

`blockBreakCmd` `{blockType} {blockX} {blockY} {blockZ} {blockFace}`
Fired when a player participating in a mini game breaks a block.

`blockPlaceCmd` `{blockType} {blockX} {blockY} {blockZ} {blockFace}`
Runs when a player participating in a minigame installs a block.

`blockDamageCmd` `{blockType} {blockX} {blockY} {blockZ} {blockFace}`
Fired when a player participating in a mini game hits a block.

`preDeathCmd` `{killerType} {killerName}`
Fires just before the player in the minigame dies.

`deathCmd` `{killer}`
The player participating in the minigame dies and runs.

`damagedCmd` `{entityName} {entityType} {itemName} {itemDurability} {itemType}`
Fires when a player participating in a minigame deals damage to an entity.

`damageCmd` `{cause}`
Executed when a player participating in a mini-game takes damage.

`projectileCmd` `{cause}` `{damage}` `{projectileType}` `{projectileName}` `{projectileUuid}` `{entityName} {entityType}`
Executed when a player participating in a mini game takes damage from a projectile.

`dropCmd` `{itemName} {itemDurability} {itemType}`
Fired when a player participating in a mini-game drops an item.

`pickupCmd` `{itemName} {itemDurability} {itemType}`
Fired when a player participating in a mini-game picks up an item.

`chatCmd` `{format} {chat}`
Fired when a player participating in a minigame hits a chat.

`commandCmd` `{command} {args}`
Executed when a player participating in a minigame hits a command.

`worldChangeCmd` `{fromWorld}` `{toWorld}`
Fired when a player participating in a mini-game moves around the world.

`vehicleDamageCmd` `{vehicleName}` `{vehicleType}`
Fired when a player participating in a minigame deals damage to a boat or cart.

`vehicleExitCmd` `{vehicleName}` `{vehicleType}`
Fired when a player participating in a mini-game is riding and disembarking a boat or cart.

`vehicleCollisionCmd` `{vehicleName}` `{vehicleType}`
Fires when a boat or cart in a player participating in a minigame collides with an entity.

`Command bundle name Cmd` `{custom function}`
`/fut <minigame player> do command bundle custom function 1, value 1, custom function 2, value 2 ...`
It is executed through the do run command.

`keeped command bundle name Cmd` `{custom function}`
`/fut <minigame player> do keeped Command bundle name Custom function 1, value 1, custom function 2, value 2 ...`
It is executed through the do execution command. Keeped bundles are not replaced by data functions. So you have to replace the data function with the meaningless /fut <player> if true == true statement in front of it.
The advantage of these keeped bundles is that data functions can be newly loaded every week in the while statement, and data can be newly loaded in the iteration statement of the allPlayer data function.

`Menu name ClickCmd` `{slot}`
When a GUI menu with a menu name is clicked, the command bundle is executed to the clicked location {slot}.



> This place is not finished yet! Please come back next time...



## Developer API

## Dependency
```xml
        <dependency>
            <groupId>Freedy</groupId>
            <artifactId>FreedyMinigameMaker</artifactId>
            <version>version</version>
            <scope>system</scope>
        </dependency>
```


## example
```java
package freedy.learnspigot.events;

import freedy.freedyminigamemaker.FreedyMinigameMaker;
import freedy.freedyminigamemaker.MiniGame;
import freedy.freedyminigamemaker.MiniGames;
import freedy.learnspigot.LearnSpigot;
import org.bukkit.command.Command;
import org.bukkit.command.CommandExecutor;
import org.bukkit.command.CommandSender;
import org.bukkit.entity.Player;

public class ChatEvent implements CommandExecutor {

    LearnSpigot plugin;

    public ChatEvent(LearnSpigot plugin) {
        this.plugin = plugin;
    }


    public boolean onCommand(CommandSender sender, Command command, String label, String[] args) {
        if (args.length == 1) {
            if (sender instanceof Player) {
                Player player = (Player) sender;
                MiniGames miniGames = FreedyMinigameMaker.miniGames;
                if (miniGames.isJoined(player)) {
                    MiniGame miniGame = miniGames.getJoined(player);
                    for (Player p: miniGame.playerList) {
                        p.sendMessage("<" + p.getName() + "> "+ args[0]);
                    }
                }
            }
        }

        return true;
    }
}
```
