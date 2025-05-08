OpenSkype

--

> OpenSkype works because Microsoft made Skype use Teams' APIs to function during the migration period from Skype to Teams, meaning that there isn't anything stopping newer Skype clients from being able to communicate just fine with other Skype users, or Teams users, except for client-sided measures, so as long as Teams' APIs continue to function in the same way that these newer Skype clients expect, Skype will continue to work just fine. In summary, it's literally just a ticking time bomb.

--

However, our good buddies over at Microsoft left us the courtesy of allowing Skype users to still be able to fully communicate with Teams users during this mini-migration period by getting Skype to use Teams' APIs for the core infraustructure of Skype, like sending messages or making calls, etc.

In a gist, this means that MS did all the heavy-lifting for us, by only preventing Skype from running via an client-sided update to force the retirement splash screen, dropped on the 5th.

Interestingly however, the APIs that Skype uses does actually differ slightly from the direct APIs that Teams uses for its core infraustructure.

Teams uses endpoints from `https://teams.live.com/api/` for it to function, while Skype uses `https://msgapi.teams.live.com/v1/` for it to function. Having a quick Google of `msgapi.teams.live.com`, yields a post on the Teams Developer Forum from Microsoft, where in May 2023, [a user under the name of JGlowacki, wanted to use the Teams API to access their chats without using the Teams client itself](https://techcommunity.microsoft.com/discussions/teamsdeveloper/how-to-use-microsoft-teams-free-chat-api/3835352), and ended up having to manually find the approprate APIs themselves, which shows that `https://msgapi.teams.live.com/v1/` had been previously used to send messages to other Teams users. Whereas nowadays, Teams currently uses `https://teams.live.com/api/chatsvc/consumer/v1/users/ME/conversations/<the-liveID-of-your-recipient>/messages` to send messages.

Now, the fact that Skype is using part of Teams's APIs is great n all, but it still does require communication or assets from other APIs or CDNs, such as:  
    - [`skypeassets.com`](skypeassets.com)  
    - [`pnv.skype.com`](pnv.skype.com)  
    - [`prod.registrar.skype.com`](prod.registrar.skype.com)  
    - [`api.asm.skype.com`](api.asm.skype.com)  
    - [`presence.skype.com`](presence.skype.com)  
    - [`api.aps.skype.com`](api.aps.skype.com)  
    - [`avatar.skype.com`](avatar.skype.com)  
    - [`static-asm.secure.skypeassets.com`](static-asm.secure.skypeassets.com)  
    - [`channels.skype.com`](channels.skype,com)  
    - [`options.skype.com`](options.skype.com)  

..among God knows where else MS has scattered their FQDNs across Skype; this is all the seperate domains needed just to get Skype running in the first place!