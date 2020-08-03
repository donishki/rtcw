RTCW Match Server
=================

This Docker image will download the required RTCW maps as specified in the
`MAPS` environment variable (from `REDIRECTURL`) and then spawn an OSP server
with configuration as defined in the environment variables or their defaults
(refer below).

All logs are written to STDOUT so can be viewed from `docker logs` or run
without the `-d` Docker run switch.

A server with this image will run v1.41b.

Example
-------

```
docker run -d \
  -p "10.0.0.1:27960:27960/udp" \
  -e "MAPS=adlernest_b3:te_escape2:te_frostbite" \
  -e "PASSWORD=war" \
  -e "REFEREEPASSWORD=pass123" \
  msh100/rtcw
```

Configuration Options
---------------------

Environment Variable | Description                    | Defaults
-------------------- | ------------------------------ | ------------------------
MAPS                 | List of maps seperated by ':'. | Default 6 maps
PASSWORD             | Server password.               | No password.
RCONPASSWORD         | RCON password.                 | No password (disabled).
REFEREEPASSWORD      | Referee password.              | No password (disabled).
HOSTNAME             | Server hostname.               | RTCW OSP
STARTMAP             | Map server starts on.          | "mp_ice".
REDIRECTURL          | URL of HTTP downloads          | http://homie1337.bestmail.ws/rtcw/rtcw%20maps
MAP_PORT             | Container port (internal)      | 27960
NOQUERY              | Disable status queries         | Disabled, set to `true` to enable.
MAXCLIENTS           | Maximum number of players      | 32
CONF_MOTDA, CONF_MOTDB, CONF_MOTDC | MOTD lines on connect | Empty.