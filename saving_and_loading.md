An addendum to the original article:

To save a world that is currently running (default name "world"), given (for example) a container hash "ab12":

```
  > docker exec -it fbae zip -r world.zip world & docker cp fbae:/data/world.zip .
```

To then load that world save next time you start up the server (assuming you have extracted it to "./worlds/world")::

```
  > docker run --env-file=config.env -p=25565:25565 -v="%CD%/worlds/world":/data/world:rw dockercraft:latest
```

Note that this will include a "live" writable version of the world so the mounted file contents will change in real-time on the host.
