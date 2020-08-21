# Scalable connection pooler Odyssey: purpose, setup, monitoring, architecture
## PG Day Israel 2020

Video can be found [here](https://yadi.sk/i/vunlsW1ip5m8FA)

Slides are available [here](https://yadi.sk/i/DmVlODzv23mBDA)

Odyssey GitHub repo https://github.com/yandex/odyssey

Feel free to [create an issue in this repo](https://github.com/x4m/odyssey_pgday.org.il/issues/new) to ask a structured question if you want a detailed answer.

Or just [ping me at telegram](https://t.me/x4mmm) for a chat :)

Some questions:
### Q: Do I need a connection pooler?
If you have more than ~100 client connections - probably you need a connection pooler.

If you do not use temporary tables, advisory locks, prepared statements and other stuff that survive transaction boundaries - you should use transaction connection pooling: Odyssey or PgBouncer.

PgBouncer is more established tool - it's been there for more than a decade.

But if you have more than 1000 of client connections, Odyssey is, probably, a better option.

### Q: Does the Odyssey work on Windows\MacOS?
Unfortunately, no. Dureing the development we cut the corners of portability and Odyssey operates over epoll(7). Probably, at some point we will support kqueues. We tried to build pooler over libevent, but faced costs of abstraction and abondoned the idea for now.
