---
layout: page
title: BingBot Self-Bot
subtitle: Self-Bot for Discord (see Discord TOS)
gh-repo: itsb1ng/BingBot-Self-Bot
gh-badge: [star, fork, follow]
---
> # BingBot Self-Bot
> Simple Discord Self-Bot that contains Hypixel API capabilities
> BingBot is a Self-Bot designed and coded by bing#0001. It offers some configuration and lists the available commands via commands.json


| [BingBot Official Discord](https://discord.gg/d6TB9xUBgj){: .btn}{: .mx-auto.d-block :}

> # How to Install
> 1. Run install.bat to reveal files and download proper python modules
> 2. Update config.json (See below)
> 3. Open BingBot.py in preferred IDE and launch (Developed and Tested in Visual Studio Code)

> # Features
> * Audio and Visual Cue for successful connection
> * Discord Nitro Gift notification for any viewable channel or direct message
> * Custom "The Hub" logo
> * Log 1000+ discord messages in aa channel or direct message
```python
global width
width = os.get_terminal_size().columns
def startup(setting):
    print()
    print()
    if setting.lower() == "standard" or setting == "":
        print("██████╗ ██╗███╗   ██╗ ██████╗ ██████╗  ██████╗ ████████╗".center(width))
        print("██╔══██╗██║████╗  ██║██╔════╝ ██╔══██╗██╔═══██╗╚══██╔══╝".center(width))
        print("██████╔╝██║██╔██╗ ██║██║  ███╗██████╔╝██║   ██║   ██║   ".center(width))
        print("██╔══██╗██║██║╚██╗██║██║   ██║██╔══██╗██║   ██║   ██║   ".center(width))
        print("██████╔╝██║██║ ╚████║╚██████╔╝██████╔╝╚██████╔╝   ██║   ".center(width))
        print("╚═════╝ ╚═╝╚═╝  ╚═══╝ ╚═════╝ ╚═════╝  ╚═════╝    ╚═╝   ".center(width))
...
def song(song):
    if song == "start":
        playsound(r"sounds\startup.mp3")
    elif song == "dm":
        playsound(r"sounds\dmsound.mp3")
    elif song == "failedlogin":
        playsound(r"sounds\failedlogin.mp3")
    elif song == ("nitro"):
        playsound(r"sounds\nitronotification.mp3")
```
```python
if (message.author.id != bing.user.id) and ("https://discord.gift/" in message.content):
    if (config[1]['nitro'] == "on"):
        try:
            content = message.content.split(" ")
            for item in content:
                if "https://discord.gift/" in item:
                    GIFT_LINK = item
            song("nitro")
            print(f"\nNitro Sniped: {message.author}\n")
            if NITRO_WEBHOOK != "":
                try:
                    webhook = Webhook.from_url(NITRO_WEBHOOK, adapter=RequestsWebhookAdapter())
```
```python
@bing.command()
async def pornhub(ctx, firstword, secondword):
    image = requests.get(f"https://logohub.appspot.com/{firstword}-{secondword}-120.webp?scheme=white&transparent=true&padding=0", stream=True)
    if image.status_code == 200:
        image.raw.decode_content = True
        with open("image.png",'wb') as f:
            shutil.copyfileobj(image.raw, f)
    file = discord.File("image.png", filename="image.png")
    await ctx.send(file=file)
    os.remove("image.png")
```
```python
@bing.command()
async def msghistory(ctx, number, channelid=None):
    try:
        if channelid == None:
            user_messages = await ctx.channel.history(limit=int(number)).flatten()
            file = open("messages.txt", "w")
            user_messages.reverse()
            for item in user_messages:
                try:
                    file.write(f"[{item.created_at.strftime('%m/%d/%Y, %H:%M:%S')}] {item.author.name}#{item.author.discriminator}: {item.content}\n")
                except:
                    pass
            file.close()
            await ctx.send("Messages Loaded:", file=discord.File("messages.txt"))
            os.remove("messages.txt")
        ...        
    except:
        await ctx.send("`Could not get messages`")
```

> # Config
> * discord_token = Refers to your Discord Token and the program will not be able to run without it
> * embed_mode = Whether or not to send your output as an embed
> * prefix = The prefix that is required for every command to invoke properly
> * dm_webhook = The webhook where you would like to display when you receive a Direct Message from someone
> * nitro_webhook = Webhook to receive nitro notifications
> * api_key = Hypixel api key to execute Hypixel related commands
> * discord_status = What you wish your status to be (Default is online). Available options: online (Online), dnd (Do Not Disturb), idle (Idle)
> * startup = The style of font you wish the starting header text to be. Available options: standard, 3D, pointed, money, blocks, graffiti, slant

> * nitro = The ability to receive console and audio notifications when someone posts a Nitro Gift link
```json
[{
    "discord_token": "",
    "embed_mode": "on",
    "prefix": "b!",
    "dm_webhook": "",
    "nitro_webhook": "",
    "api_key": "",
    "discord_status": "online",
    "startup": "standard"
},
{
    "nitro": "on"
}]
```