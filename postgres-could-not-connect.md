Upon trying to run a rails app that connects to a postgres database:
```sh
PG::ConnectionBad: could not connect to server: No such file or directory
    Is the server running locally and accepting
    connections on Unix domain socket "/tmp/.s.PGSQL.5432"?
```

Upon trying to run `psql`:
```sh
psql: could not connect to server: No such file or directory
    Is the server running locally and accepting
    connections on Unix domain socket "/tmp/.s.PGSQL.5432"?
```

Further inspection showed that this file did not exist. This happened after my laptop shut down unexpectedly, so it seemed probable that it was related to a file corruption or similar.

After much googling, restarting services, uninstall/reinstalling, and upgrading/downgrading versions with no luck, the key to the solution was here:

https://philihp.com/2019/postgres-10-11-upgrade.html

The insanely simple solution:
1. run postgres manually
2. shut it down gracefully
3. ??? (I suppose the corrupted/missing files are being regenerated here)
4. problem solved

In my case:
```sh
/usr/local/opt/postgresql/bin/postgres
```
Then press ⌘+C