# Postman

## Build
Via GitHub repository
```bash
$ docker build --tag alireaza/postman:$(date -u +%Y%m%d) --tag alireaza/postman:latest https://github.com/alireaza/postman.git
```

## Run
```bash
$ docker run \
--interactive \
--tty \
--rm \
--mount="type=bind,source=/tmp/.X11-unix,target=/tmp/.X11-unix" \
--env="DISPLAY=$DISPLAY" \
--device="/dev/dri:/dev/dri" \
--env="PULSE_SERVER=unix:${XDG_RUNTIME_DIR}/pulse/native" \
--mount="type=bind,source=${XDG_RUNTIME_DIR}/pulse/native,target=${XDG_RUNTIME_DIR}/pulse/native" \
--env="TZ=$(cat /etc/timezone)" \
--mount="type=bind,source=/var/run/dbus/system_bus_socket,target=/var/run/dbus/system_bus_socket" \
--mount="type=bind,source=$(pwd)/udocker,target=/home/udocker" \
--name="postman" \
alireaza/postman
```

