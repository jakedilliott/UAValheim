# UA Valheim
Go beyond Plus Ultra with these quality of life and fun Valheim mods! The purpose of this modpack is to provide an easy way for my friends and I to use a common set of both server and client side mods. 

***Disclaimer:*** Your mileage may vary! Valheim modding is still in it's infancy and is not officially supported by the developers of Valheim. These settings and configurations work for me with my server setup, and I do not guarantee that this modpack will work properly.

# Installation instructions

## Client Side (players)
For client side (users playing on the desktop) use one of the mod managers available on the [Thunderstore](https://thunderstore.io). I prefer [rd2modman](https://valheim.thunderstore.io/package/ebkr/r2modman/) but the [Thunderstore Mod Manager](https://www.overwolf.com/app/Thunderstore-Thunderstore_Mod_Manager) should also work just fine. 

## Server Side
### Requirements:
 - Some basic knowledge of linux and the command line.
 - A server that has docker installed, and a non-root user with permissions to run docker. I use [vultr](https://vultr.com)

Example docker-compose.yml using [mbround/valheim-docker](https://github.com/mbround18/valheim-docker) that is based on their [getting started with mods](https://github.com/mbround18/valheim-docker/blob/main/docs/getting_started_with_mods.md) documentation.

```yaml
version: "3"
services:
    valheim:
        image: mbround:/valheim:latest
        ports:
            - 2456:2456/udp
            - 2457:2457/udp
            - 2458:2458/udp
        environment:
            - PORT=2456
            - NAME="Cool Server Name"
            - WORLD="UA High"
            - PASSWORD="AllMight"
            - PUBLIC=1
            - AUTO_UPDATE=0
            - TYPE=BepInEx
            - "MODS=
              https://cdn.thunderstore.io/live/repository/packages/jakedilliott-UAValheim-1.0.0.zip
              "
        volumes:
            - ./valheim/saves:/home/steam/.config/unity3d/IronGate/Valheim
            - ./valheim/server:/home/steam/valheim

``` 
