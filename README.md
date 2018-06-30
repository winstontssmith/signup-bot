# signup-bot
Signup bot is used to manage our clan's raid lists and is currently under early development. 

Currently the commands that can be issued with this bot are:
```
In #signup-list
+raid $Title | $Date | $Description (| $Class)
+time $Raid_id|$Time

In #signup-here
+join $Raid_id(|$Class|$Reserve|$User)
+drop $Raid_id(|$User)
+class $Raid_id(|$Class|$User)

```
Arguments in parentheses are optional and do not need to be included. The arguments are ordered, however, so if you want to join your friend Dave to the main roster as a titan, you'd say something like `+raid 5|Titan||Dave`. If Dave wanted to fill any class needed you could say `+raid 5|||Dave`. More detailed documentation is available on the [github site for the bot](https://github.com/cliffhanger407/signup-bot). Keep in mind the number will change, depending on which raid ID it is. I'm not a mind-reader.

If you can't find it, the | key is just above your Enter key on a standard keyboard.

All the examples below are going to assume you're trying to modify raid 6. Obviouisly, if the raid isn't raid 6, change the number to match.

## Things you can do in #signup-list
1. Create Raids
2. Change the time of a raid

### To Create a Raid:
Use the `+raid` command with the syntax:
```
+raid $Title | $Date | $Description (| $Class)
```
You must specify a title, date, and description. All of these are free text and are not error checked in any way. I'll give a detailed walkthrough of how to create a raid, but the others will be less in-depth.

1) Type +raid
2) Type your raid's title. Usually this will be something like "Leviathan" or "Lev>EoW>SOS" or... something descriptive. Now type the | character. It's above the enter key.
3) Type your raid's time. This can be formatted however you want, we're just storing this for display purposes. Now type | again.
4) Type your raid's description. Maybe you want this to be a @SpacePup raid, or maybe you want it to be super sweaty. Your call. Type it here.
5) If you want to specify your class, type a | and then the class name. If you don't do this step, the system will put you in as a fill.

So for example, you would type:
```
+raid Leviathan|6/29 5PM PST|Let's set up a sherpa run, join in @spacepup!
```
and that would produce the below output:


**Leviathan**  
**Time:** 6/29 5PM PST  
**Posted by:** cliffhanger407  
Let's set up a sherpa run, join in @spacepup!

To join this raid, reply in #signup-here with the command `+join 5(|Class|Reserve|Name) `
For example: `+join 5|Hunter` would join me to the main roster, and `+join 5|Fill|reserve` would have me be a reserve fill. Lastly, `+join 5|Titan||signup-bot-evil-twin` would add my evil twin to the raid.

```====ROSTER====
1. cliffhanger407 - Fill
2. OPEN 
3. OPEN 
4. OPEN 
5. OPEN 
6. OPEN 
====RESERVES==== 
1. OPEN 
2. OPEN 
```

or
```
+raid Leviathan|6/30 5PM PST|I need a clear for my Titan|Titan
```

would produce the output:


**Leviathan**  
**Time:** 6/30 5PM PST  
**Posted by:** cliffhanger407  
I need a clear for my Titan

To join this raid, reply in #signup-here with the command `+join 5(|Class|Reserve|Name) `
For example: `+join 5|Hunter` would join me to the main roster, and `+join 5|Fill|reserve` would have me be a reserve fill. Lastly, `+join 5|Titan||signup-bot-evil-twin` would add my evil twin to the raid.

```
====ROSTER====
1. cliffhanger407 - Titan
2. OPEN 
3. OPEN 
4. OPEN 
5. OPEN 
6. OPEN 
====RESERVES==== 
1. OPEN 
2. OPEN 
```

The bot takes care of all the formatting and signups for you!

### To change the time of an already existing raid (creator only)
Use the `+time` command with syntax:
```
+time $Raid_id|$Time
```

You must specify a time (duh) that you want to update to. The time can be freeform, and is not errorchecked.

For example, you can type: `+time 6|7/1 5PM PST - Sorry, I forgot I had something going on tonight.`
and the raid time will update to match. Additionally, a DM will be sent to everyone signed up for the raid. The message I just got from signup-bot says:
>### **signup-bot** - Today at 2:59 PM  
>cliffhanger407's raid Leviathan has moved from 6/30 5PM PST to 7/1 5PM PST - Sorry, I forgot I had something going on tonight..

## Things you can do in #signup-here:

### To join an already existing raid:
Use the `+join` command with the syntax:
```
+join Raid_ID(|Class|Reserve|User)
```

As above. If all you want to do is join the raid as yourself, filling in as any class, you could type: `+join 6`, which would join you as a Fill into raid #6.  

Alternatively, if you need to do a run on your titan, you could type `+join 6|Titan` and it would join you as a titan. If you want to join the reserve list as a fill, you can type `+join 6||yes`. (Note, anything you put in the spot for reserve will make you reserve, even if you type 'no'). If your buddy is away from Discord but wants you to sign them up for the raid, you can type `+join 6|||signup-bot's buddy`, and that would put that person in as a fill. If you put data in between the other pipes, you could sign a friend up as a Warlock, reserve like this: `+join 6|Pocketsand|yes|signup-bot's buddy`.

If you try to sign-up for a raid that is already filled up, don't worry, I'll add you directly to the reserves. And, if someone `+drop`s, you'll get a DM letting you know that there's an open spot.

### To leave a raid you are in:
Use the `+drop` command with syntax:
```
+drop $Raid_id(|$User)
```
If you signed yourself up with a clever name (or signed up a friend), you must put that exact name in. Note, that you cannot drop someone from a raid unless 1) you are that person, 2) you signed that person up, or 3) you are the raid creator. Don't get any ideas.

`+drop 6` will drop me from the raid. If I want to un-sign-up @signup-bot's buddy, I will need to issue `+drop 6|signup-bot's buddy`. For now, capitalization and exact spelling are required. If there's a need, we may improve this functionality in the future.

### To change your class for a raid you're in:

Use the `+class` command with syntax:
```
+class $Raid_id(|$Class|$User)
```

If you previously specified a class and want to swap to Fill, all you need to do is type `+class 6`. If you want to change your class to punchbro, just type `+class 6|punchbro`. If you signed up your buddy for a raid as fill, and they let you know that they need to run on Warlock, you can just say `+class 6|warlock|signup-bot's buddy`.

That's about it for now. We will continue collecting requirements and do development over the coming months, letting you know what's available.
