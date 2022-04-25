---
layout: page
title: BingBot Discord-Bot
subtitle: Discord Bot hosted by Sparked Host
---
> # BingBot Discord-Bot
> Discord bot that conducts Hypixel API and Economy System

> [Invite BingBot](https://discord.com/api/oauth2/authorize?client_id=541682385151066112&permissions=8&scope=bot%20applications.commands) [BingBot Official Discord](https://discord.gg/d6TB9xUBgj)


> # Accessibility to Slash Commands and Economy System

> - Bot is hosted via Replit because I am broke and Economy system is loaded to json file
> - bb!startmining to start the journey
> - /help for all available commands

> # Hypixel API 

> - Uses Hypixel's API, Senither API, and SlothPixel API
> - Mostly uses senither because all other APIs are inferior 
> - /help hypixel or bb!help skyblock


```python
@dpy.command()
async def weight(ctx, name):
    try:
        user_name = requests.get(f"https://api.mojang.com/users/profiles/minecraft/{name}").json()
        uuid = user_name["id"]
        profile_link = f"https://api.hypixel.net/skyblock/profiles?key={KEY}&uuid={uuid}"
        sb_data = getInfo(profile_link)
        link = f"https://api.hypixel.net/player?key={KEY}&uuid={uuid}"
        data = getInfo(link)
        senither = f"https://hypixel-api.senither.com/v1/profiles/{uuid}?key={KEY}"
        senither_data = getInfo(senither)
        save = 9999999999999999999
        for x in range(0, len(sb_data['profiles'])):
            for y in sb_data['profiles'][x]['members']:
                if uuid == y:
                    difference = time.time() - sb_data['profiles'][x]['members'][y]['last_save']
                    if difference < save:
                        save = sb_data['profiles'][x]['members'][y]['last_save']
                        profile_id = sb_data['profiles'][x]['profile_id']

        for z in range(0,len(senither_data['data'])):
            if senither_data['data'][z]['id'] == profile_id:
                profile_num = z

        profile_name = data['player']['stats']['SkyBlock']['profiles'][profile_id]["cute_name"]
```

```python

```
