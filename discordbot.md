---
layout: page
title: BingBot Discord-Bot
subtitle: Discord Bot hosted by Sparked Host
gh-repo: itsb1ng/BingBot-Discord-Bot
gh-badge: [star, fork, follow]
---
> # BingBot Discord-Bot
> Discord bot that conducts Hypixel API and Economy System

> [Invite BingBot](https://discord.com/api/oauth2/authorize?client_id=541682385151066112&permissions=8&scope=bot%20applications.commands){: .btn} | [BingBot Official Discord](https://discord.gg/d6TB9xUBgj){: .btn}


> # Accessibility to Slash Commands and Economy System

> - Bot is hosted via SparkedHost because and Economy system is loaded to json file on Apollo Server
> - bb!startmining to start the journey
> - /help for all available commands

```python
async def mine(ctx):
  ...
  if account is True:
    with open("storage/premium.json", "r") as premfile:
        premium = json.load(premfile)
    def return_key(val):
      key_list=list(premium[0].keys())
      val_list=list(premium[0].values())
      for i in range(len(premium[0])):
        if val_list[i]==val:
          return key_list[i]
          
    for p in premium[0]:
      for i in range(len(premium[0][p])):
        if ctx.author.user.id == premium[0][p][i]:
          rank_ = return_key(premium[0][p])
    crate = 0
    if data[user_num]['current_pick'] == "BingCoin Pickaxe":
      min = 1
      coin_num = 1
    elif data[user_num]['current_pick'] == "BingCoin Drill": 
      min = 1
      coin_num = 2
    elif data[user_num]['current_pick'] == "Miner x1000": 
      min = 2
      coin_num = 5
```

```python
if (heist_user_num == 0) or (heist_user_num-1 == heist_partner_num) or (heist_user_num+1 == heist_partner_num) or (heist_user_num == heist_partner_num):
      if heist_json[heist_user_num]['heist'] == "Burj Khalifa":
        income = random.randint(1500,2500)
      elif heist_json[heist_user_num]['heist'] == "The Louvre Museum":
        income = random.randint(8000,11000)
      elif heist_json[heist_user_num]['heist'] == "Emirates Palace":
        income = random.randint(17000,23000)
      elif heist_json[heist_user_num]['heist'] == "SoFi Stadium":
        income = random.randint(30000,35000)
      elif heist_json[heist_user_num]['heist'] == "The Great Mosque of Mecca":
        income = random.randint(50000,65000)
        
      if rank_ == "Script Kitty":
        income_float = income + (income*0.10)
      elif rank_ == "Bitcoin Screenshotter":
        income_float = income + (income*0.15)
      elif rank_ == "NFT Miner":
        income_float = income + (income*0.20)
      income = income_float //2

      
      if rank_ == "Default" and chance <= 20:
        failure = True
      elif rank_ == "Script Kitty" and chance <= 18:
        failure = True
      elif rank_ == "Bitcoin Screenshotter" and chance <= 16:
        failure = True
      elif rank_ == "NFT Miner" and chance <= 14:
        failure = True
      
      if failure is True:
        for x in range(len(data)):
          if data[x]["id"] == ctx.author.id:
            user_num = x
        new_bank = data[user_num]['bank'][0] - income
        outdata = {"id": ctx.author.id, "name": str(ctx.author), "coin": data[user_num]['coin'], "bank": [int(new_bank), data[user_num]['bank'][1]], "spent": data[user_num]['spent'], "current_pick": data[user_num]['current_pick']}
        data.pop(user_num)
        data.append(outdata)
        with open('economy.json', 'w') as out:
          out.write(json.dumps(data))
```


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
async def bin(ctx, *, item):
  try:
    auction_data = requests.get("http://maro.skyblockextras.com/api/auctions/all").json()
    for i in range(0,len(auction_data['data'])):
      if auction_data['data'][i]['name'] == item or item.lower() == auction_data['data'][i]['name'].lower():
        number = i

    item_id = auction_data['data'][number]['id']
    item_data = requests.get(f"http://maro.skyblockextras.com/api/auctions/quickStats/{item_id}").json()
    embed = discord.Embed(title=auction_data['data'][number]['name'], description=item_id, color=0xC98FFC)
    embed.add_field(name="Lowest BIN", value="{:,.0f} coins".format(auction_data['data'][number]['value']))
    embed.add_field(name="Average Price", value="{:,.2f} coins".format(item_data['data']['average']))
    embed.add_field(name="Highest Price", value="{:,.2f} coins".format(item_data['data']['max']))
```
