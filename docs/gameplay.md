# Gameplay

## Mechanics

This category covers varius game mechanics such as player controller, building system, as well as some ideas for combat like i-frames, hitboxes and hurtboxes, etc. 

### NPC-Controller

to-do

### Player-Controller

**Speed and direction**

pressing WASD determins direction a player is taking. This will be stored in a Vector3 variable called **direction**
Determining the full Vector3 (direction and speed) we'll be done by taking the direction and multiplying it with **speed_multi**
**speed_multi** is a simple number gotten by multiplying speed (**walk_speed** or **run_speed** or **sprint_speed**) and **speed_buff** and **speed_debuff**

**Walk-Run-Sprint button logic.**

Now onto the fun part. Button logic. For some reason I was having real difficulties with this one. Its relatively simple. 
Pressing the **sprint button** will trigger a function **Sprint_btn()** which'll follow following logic:

```
Sprint_btn():
    if !sprint_btn_running: # make sure function is not already running
        sprint_btn_running != sprint_btn_running 
        if Input.is_action_just_pressed('move_sprint'): # if sprint is just pressed
            await get_tree().create_timer(0.2).timeout # wait 0.2 secs
            if Input.is_action_pressed('move_sprint'): # if sprint is still held do sprint speed
                speed_mutli = sprint_speed * speed_buff * speed_debuff
            elseif running: # otherwise if player was running set him to walk
                speed_multi = walk_speed * speed_buff * speed_debuff
            else: # else player should walk
                speed_multi = run_speed * speed_buff * speed_debuff
        sprint_btn_running != sprint_btn_running # set variable back to false so function can be rerun
        
```

to-do
#### Emotes

**Whistling** - emote for whisling. Have a stat check if a player can whistle or not. Whistling should slowly fade out in-game music and replace it with the players whistle. Visually there would be a couple of notes above players head, indicating he's whistling. If this is done at night it can trigger [whistle event](lore#whistling-at-night)

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

Should npc remember player actions and actions of other npcs in their surrouding/groups. It might be too complex, but it could also be used to let a characfter form an opinion on people in its proximity. 
Now the question is how do you make an npc react to this in organic and natural way. chatGPT is of course a great tool that would be amazing to be used here, but does it have to be used? Can it be done on its own without a third party software. 
Something along the line of following scenarion: 
A paladin joined a player who up until that moment only did things paladin agrees with. Defended poor, defeated unholy creatures, etc. 
But now the player finds itself in a situation where he can kill a young group of monks in training, but it'll prevent one of them becoming a prophetised tyrann that will ruin the world. 
Paladin belives in good and nothing else, so the act of murdering 10 people just for a chance that the one person might be evil is against his ideals. The player commits the deed, and paladin as a group member just stands there watching it happen. It would be hard detecting what a player would do in such a situation before it happens, so we'll act on it in following idea. 
Player swings the sword and hits the innocent. The paladin yells "STOP!". This is his first retaliation. Next time a player swings the sword and kills a couple of monks, the paladin will move in front of player, and say a generic line, "I won't stand for this." If player lowers the aggression, by sheeting the sword and not attacking the monks any further, the paladin will be displeased (some sort of moral debuf that will go down with time, but can never be removed.) So if player tries to kill another good monk in next year of their advanture together, the paladin will leave or retaliate in some other way. 

So I think I need to sumarize the notes that should be extended to be able to think clearly about this idea. 


## Stats

### Moral

Moral should be a simple equation (Expotential decay? Linearl decay) that determins whether an action should be done or not. Think attacking a stronger enemy, or staying and defending a castle although you've been starving, etc. 

### Renown

how well known a character is, for good or bad deeds

### Perception

## Behavious

NPCs have to be able to mimic players decisions and behaviour. I'll do my best to describe them here. 

**Stats**
Im going on a train of thought that each behavious should be determind by a single stat, but that  might be too limiting. However, maybe limiting it by 3 of them or doing some kind of nesting limitation might be pretty good. 
e.g: Determining if the npc will attack: First check npcs [moral](#Moral) (how afraid/brave he is), then check odds npc's [group](#Group-Stats) is facing. 

### Agression initiation 
**Determins when a character will start aggression**

**checks:**

1. Compare characters [renown](#Renown) vs enemy's [renown](#Renown) *don't forget the note written below this list*
2. Compare odds between two [groups](#Group-Stats) 
3. Check [moral](#Moral)

!!! note
    If characters renown is higher than enemies, but for some reason moral is lowered, they'll show aggression, without acting on it. If the enemy reacts to the aggression (e.g Player attacks although the character would not have acted on the aggression, it will be as if a player attacked an innocent aka a bad deed)


## Creatures

### Wolves

Wolves should hunt on stamina. Meaning they try to exhaust their targets. 
The way it would work against deers is that deers are faster, but wolves would try to stay on their sence, buz one thing they'll be able to catch are babies so you get alpha deers defending. And deers should get more aggressive if its mating season. Harry explianed it really good

## Groups

to-do

### Group-Stats

to-do (group numbers, faction, etc)





# Thinking-Over

## TO-Duty
I'm thinking if it should be a stat that a character tries to follow even if they don't all the requirements (aka.: [this](#agression-initiation))
But I feel like it should be simply covered differently when checking the aggression