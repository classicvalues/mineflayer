# API

## Classes

### mineflayer.Vec3

See [superjoe30/node-vec3](https://github.com/superjoe30/node-vec3)

All points in mineflayer are supplied as instances of this class.

 * x - south
 * y - up
 * z - west

## Bot

### Properties

#### bot.username

Use this to find out your own name.

#### bot.game.spawnPoint

Coordinates to the main spawn point, where all compasses point to.

#### bot.game.levelType

#### bot.game.dimension

#### bot.game.difficulty

#### bot.game.gameMode

#### bot.game.hardcore

#### bot.game.worldHeight

#### bot.game.maxPlayers

#### bot.isRaining

#### bot.settings.chat

Choices:

 * `enabled` (default)
 * `commandsOnly`
 * `disabled`

#### bot.settings.colorsEnabled

Default true, whether or not you receive color codes in chats from the server.

#### bot.settings.viewDistance

Choices:
 * `far` (default)
 * `far`
 * `normal`
 * `short`
 * `tiny`

#### bot.settings.difficulty

Same as from server.properties.

#### bot.settings.showCape

If you have a cape you can turn it off by setting this to false.

#### bot.experience.level

#### bot.experience.points

Total experience points.

#### bot.experience.progress

Between 0 and 1 - amount to get to the next level.

#### bot.health

Number in the range [0, 20] representing the number of half-hearts.

#### bot.food

Number, in the range [0, 20] representing the number of half-turkey-legs.

#### bot.foodSaturation

Food saturation acts as a food "overcharge". Food values will not decrease
while the saturation is over zero. Players logging in automatically get a
saturation of 5.0. Eating food increases the saturation as well as the food bar.

### Events

#### "chat" (username, message, rawMessage)

 * `username` - who said the message
 * `message` - stripped of any control characters
 * `rawMessage` - unmodified message from the server

#### "nonSpokenChat" (message, rawMessage)

 * `message` - stripped of all control characters
 * `rawMessage` - unmodified message from the server

#### "login"

#### "spawn"

Emitted once after you log in and spawn for the first time
and then emitted when you respawn after death.

#### "game"

Emitted when the server changes any of the game properties.

#### "rain"

Emitted when it starts or stops raining. If you join a
server where it is already raining, this event will fire.

#### "kicked" (reason)

Emitted when the bot is kicked from the server. `reason`
is a string explaining why you were kicked.

#### "spawnReset"

Fires when you cannot spawn in your bed and your spawn point gets reset.

#### "death"

Fires when you die.

#### "health"

Fires when your hp or food change.

### Methods

#### chat(message)

Sends a publicly broadcast chat message. Breaks up big messages into multiple chat messages as necessary. If message begins with "/tell <username> ", then all split messages will be whispered as well.

#### spawn()

Spawn is called automatically upon login and death. If you wish to
disable this behavior and do it manually, pass `autoSpawn` `false`
to the `options` argument of `createBot`.

#### setSettings(options)

See the bot.settings property above.

#### sleep(bedPosition)

Sleep in a bed. `bedPosition` should be a point which contains a bed.

#### wake()

Get out of bed.