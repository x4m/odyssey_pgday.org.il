# Scalable connection pooler Odyssey:
## purpose, setup, monitoring, architecture
## PG Day Israel 2020

Video can be found [here](https://yadi.sk/i/vunlsW1ip5m8FA)
Slides are available [here](https://yadi.sk/i/DmVlODzv23mBDA)

Some questions:
### Q: Do I need a connection pooler?
If you have more than ~100 client connections - probably you need a connection pooler.
If you do not use temporary tables, advisory locks, prepared statements and other stuff that survive transaction boundaries - you should use transaction connection pooling: Odyssey or PgBouncer.
PgBouncer is more established tool - it's been there for more than a decade.
But if you have more than 1000 of client connections, Odyssey is, probably, a better option.
