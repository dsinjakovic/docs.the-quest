# Gameplay

## Mechanics

This category covers varius game mechanics such as player controller, building system, as well as some ideas for combat like i-frames, hitboxes and hurtboxes, etc. 

### NPC-Controller

to-do

### Player-Controller

to-do

## Items

All and everything about items and their use in game

### Item-Effects

To-do

### Maintanance-Items

To-do

### Item degradation and repairs

Item durability should have 2 stages of durability, **durability** and **maintanance**.

**Durability** will be the normal 0-100 value that will determin how the item will perform. The lower the durability is, higher the chance of item breaking down. The curvature of how likely the item is to break should be covered by exponential decay (or growth idk). Meaning the less durability the item has the higher chance for the item to grow.

**Maintanance** will be another new value that can add half extra durability on top of **durability**, so 0-50 and will be applied by using certain [items](#Maintanance-Items) like, sharpening stones, maintanance kits, etc. Apart from applying maintanance, they'll also apply certian [buffs](#Item-Effects). 

# Combat

To-do

# AI

AI seems like a really complicated topic, especially with the range I want it to have. 
[NPC-Controller](#NPC-Controller) and [Player-Controller](#Player-Controller) should both control the same entity. When executed correct it will allow player to take control of any entity. 

## Stats

### Moral

## Behavious

NPCs have to be able to mimic players decisions and behaviour. I'll do my best to describe them here. 

**Stats**
Im going on a train of thought that each behavious should be determind by a single stat, but that  might be too limiting. However, maybe limiting it by 3 of them or doing some kind of nesting limitation might be pretty good. 
e.g: Determining if the npc will attack: First check npcs [moral](#Moral) (how afraid/brave he is), then check odds npc is facing ([group-numbers](#Group-Stats))

### Aggression

Should aggression be its own stat? When thinking about it player aggression can be utilized in combat, 

## Groups

to-do

### Group-Stats

to-do (group numbers, faction, etc)