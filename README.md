```
             ▄█      ▄▀▀▀▀▄       ▄▀▀▄ ▄▄       ▄▀▀█▄       ▄▀▀▄ ▀▄
       ▄▀▀▀█▀ ▐     █      █     █  █   ▄▀     ▐ ▄▀ ▀▄     █  █ █ █
      █    █        █      █     ▐  █▄▄▄█        █▄▄▄█     ▐  █  ▀█   alpha design doc
      ▐    █        ▀▄    ▄▀        █   █       ▄▀   █       █   █
        ▄   ▀▄        ▀▀▀▀         ▄▀  ▄▀      █   ▄▀      ▄▀   █     sept 2017
         ▀▀▀▀                     █   █        ▐   ▐       █    ▐
                                  ▐   ▐                    ▐
```

## <a name="toc"></a>sections

1. [Overview](#section-overview)
    1. [Players vs Characters](#section-overview--pvsc)
2. [World](#section-world)
    1. [Rooms](#section-world--rooms)
        1. [State](#section-world--rooms-state)
        2. [Type](#section-world--rooms-types)
        3. [Properties](#section-world--rooms-properties)
    2. [Interaction](#section-world--interaction)
    3. [Setting](#section-world--setting)
3. [Players](#section-players)
4. [Characters](#section-characters)

## <a name="section-overview"></a> Overview [\^](#toc)

    elevator pitch

    mechanics philosophy, reference points

    players vs. characters

    single vs. multiplayer

    turn system

    combat system (brief)

    style/flavor/aesthetics
    

### <a name="section-overview--pvsc"></a> Players vs. Characters




## <a name="section-world"></a> World [\^](#toc)

The structure of the game world is an homage to old-school BBS "door games," MUD/MOOs, and to some extent tabletop RPGs. What this means practically is that the "map" is essentially a network of inter-connected user-interfaces. These UIs are called "rooms," but in this sense, a room can be anything from a basecamp at the foot of a mountain to a literal room in a tavern.

### <a name="section-world--rooms"></a> Network of Rooms 

The Game World is a Network of Rooms. Every unique location in the game* is represented by a single room object. Rooms have connections to each other, composing the network that defines the game world. 

Places like a dungeon or forest may be comprised of multiple connected rooms, but somewhere there would be a connection back to the main road (a series of rooms), which ultimately would lead back to the main city (that's right, a room).

> *&nbsp;eg: the main city, a tavern, a shop, an empty clearing in the middle of a forest, the boss room of a dungeon, etc, etc, etc..

Navigating the world is a matter of moving the party from one room to the next, be that from shop to shop in a market or from the basecamp to summit of a mountain.
*Every character action is done via a room interface.* 

#### <a name="section-world--rooms-state"></a> Rooms have State

Every room has a type (more below), which group them into classes, but every room also has a unique state, making them objects.

#### <a name="section-world--rooms-types"></a> Room Types

Every room is of a type. Every room type has its own interface (eg. a template), preprogrammed and custom made for whatever the function of the room is. The interface for a tavern, for example, could contain a chatroom with your fellow patrons. The interface for encounters will be central to the game.

Rooms of the same type share the same interface, but whats going on in the room at the time is a matter of the room's state.

##### <a name="section-world--rooms-types-table"></a> Room Types ((WIP)):

|name|description|
|---|---|
|Basic      |mainly for screens having only travel options, but also used for unique quests
|Encounter  |fighting stuff|
|Shop       |faire du shopping|
|Tavern     |sleep in town; chat with others|
|Camp       |on the road|
|Schools and Temples|learn stuff|

#### <a name="section-world--rooms-properties"></a> Room Properties

Every room has a universal set of properties. In addition, the room type also may define a set of its own properties.

##### <a name="section-world--rooms-properties-universal"></a> Universal Room Properties:

|name|type|
|---|---|
|Type                   |Constant|
|Connected rooms        |Set<Rooms>|
|Floor items            |Set<Items>|
|Description Template   |Template String|
|Effects                |Set<Room Effects>|

### <a name="section-world--interaction"></a> Interacting with the Game World:

The player's party always occupies one room in the game world (the "current room"). The player is always looking at a representation of the current room (menus and modals aside).
The biggest risk to this project is a takedown notice from Nintendo, however, this can be avoided. With proper funding, I can consult appropriate parties to ensure this project is never at risk.


There is a universal interface element allowing the player to move their party to rooms connected to the current room. Aside from this, the interface is specific to the room type.

**The view** uses the template for the current room type, rendering the room's state.

> eg: A shop room displays the shop inventory, allows to buy and sell, etc. An enounter room forces the party to fight a mob of npcs.

The simplest room is something like an empty room in a forest or dungeon. It only allows moving to adjacent rooms. It would be nice if it had cool art, but in alpha these will have a very bare-bones interface. The encounter room, on the other hand, contains a large chunk of the core functionality of the game.

### <a name="section-world--setting"></a> Setting

**((WIP))

## <a name="section-players"></a> Players [\^](#toc)

    turns
    currency
    item bank
    characters
    holdings

## <a name="section-characters"></a> Characters [\^](#toc)

    attributes
    skill points
    skills
    items
        equipables

