# amybot

## What is everything?

### Main components

[`amybot/samantha`](https://github.com/amybot/samantha) - Bot shards. Opens connections to the Discord websocket gateway and pushes events onto the queue.

[`amybot/samantha-connector`](https://github.com/amybot/samantha-connector) - Assigns shard IDs to `samantha` instances. Persists state in redis.

[`amybot/alice`](https://github.com/amybot/alice) - Main backend worker. Handles basically all commands, as well as queueing up events for other backend services.

[`amybot/hotspring`](https://github.com/amybot/hotspring) - [JDA-Audio](https://github.com/DV8FromTheWorld/JDA-Audio)-based audio server. Uses a REST API, and pushes events into the same queue that `alice` workers read from.

### Supporting code

[`amybot/emily`](https://github.com/amybot/emily) - A port of the [Nostrum](https://github.com/Kraigie/nostrum) Discord REST API handler, which (among other things) persists state in Redis to allow distributed REST usage. 

[`queer/lace`](https://github.com/queer/lace) - Redis-backed Erlang node clustering and autodiscovery.

## How do I self-host?

You don't. The code is explicitly designed to make a LOT of assumptions about how I run it, and as such is VERY unfriendly to self-hosting. This includes, but is not limited to, dependencies on closed-source components.
