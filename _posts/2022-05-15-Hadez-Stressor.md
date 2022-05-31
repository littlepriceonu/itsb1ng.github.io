---
layout: post
title: Nagasaki Nuker
subtitle: Python Script to Execute Processes via Discord Token
thumbnail-img: /assets/img/hadez.jpg
share-img: /assets/img/hadez_logo.png
cover-img: /assets/img/hadez_login.png
tags: [python]
---
* Stressor and DDOS Panel (Code is closed source)

> IP Geolocation

```python
url = requests.get(f"http://www.geoplugin.net/json.gp?ip={IP}").json()
print("\t┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓")
print(f"\t   {IP} Geolocation Information")
print(f"\t   Continent: {url['geoplugin_continentName']}")
print(f"\t   Country: {url['geoplugin_countryName']}")
print(f"\t   Timezone: {url['geoplugin_timezone']}")
print(f"\t   Region/State: {url['geoplugin_regionName']}")
print(f"\t   City: {url['geoplugin_city']}")
print("\t┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛")
```

> Menu

```python
def menu(package, id):
    menu="""
                ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓                                                        
                ┃         ____   ____       _____        _____        ______      _____                ┃ 
                ┃        |    | |    |  ___|\    \   ___|\    \   ___|\     \    /    /|___            ┃
                ┃        |    | |    | /    /\    \ |    |\    \ |     \     \  /    /|    |           ┃
                ┃        |    |_|    ||    |  |    ||    | |    ||     ,_____/||\____\|    |           ┃ 
                ┃        |    .-.    ||    |__|    ||    | |    ||     \--'\_|/| |   |/    |___        ┃  
                ┃        |    | |    ||    .--.    ||    | |    ||     /___/|   \|___/    /    |       ┃
                ┃        |    | |    ||    |  |    ||    | |    ||     \____|\     /     /|    |       ┃
                ┃        |____| |____||____|  |____||____|/____/||____ '     /|   |_____|/____/|       ┃
                ┃        |    | |    ||    |  |    ||    /    | ||    /_____/ |   |     |    | |       ┃
                ┃        |____| |____||____|  |____||____|____|/ |____|     | /   |_____|____|/        ┃
                ┃          \(     )/    \(      )/    \(    )/     \( |_____|/      \(    )/           ┃
                ┃           '     '      '      '      '    '       '    )/          '    '            ┃
                ┃                                                        '                             ┃
                ┃                    Developed by bing#0001 | Managed by Bandy#1000                    ┃
                ┃                           https://discord.gg/wupV9ZC7ET                              ┃
                ┣━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┫
                ┃                                                                                      ┃
                ┃           """ + Fore.RED + "[1]. " + Fore.LIGHTRED_EX + """UDP DOS Attack                    """ + Fore.RED + "[2]. " + Fore.LIGHTRED_EX + """Geolocate IP                   ┃     
                ┃                                                                                      ┃                                                               
                ┃                       """ + Fore.RED + "[3]. " + Fore.LIGHTRED_EX + """Ping User ('Ctrl + C' to quit)                            ┃
                ┃                                                                                      ┃
                ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛
    """
    print(Fore.LIGHTRED_EX + menu.center(width))
    print(r"                Choice: ", end="")
```

{: .box-warning}
**Warning:** Script is closed source and available for purchase. Join [Hadez Stresser Discord](https://discord.gg/wupV9ZC7ET) for more information