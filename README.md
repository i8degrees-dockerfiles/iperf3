
# iperf3

- [OpenProject Documentation][0]
- [Docker Compose bootstrap configuration][10]
- [Docker Hub: networkstatic/iperf3][20]

## usage

Once the server is setup and ready, you can begin running speed tests on the
client-side with something like:

``shell
# -c implies client
# -P implies the number of parallel threads
# -t implies the duration of the test
iperf3 -c example.com -P2 -t60
```

For additional options, consult the command line usage reference, or check out
the manual page for `iperf3`.

```shell
iperf3 --help
```

### deps

- `docker`
- `docker-compose`

### docker setup

This project needs no particular environment to be setup, other than a quick
check of the `ports` assignment in regards to your firewall layout and maybe
an adjustment to the `command` if the defaults do not suit you. This container
should be ran with no privileges unless you so happen to use one of the
following switches:

- `-B` root privs required
- `-s` root privs required
- `-D` root privs required
- `--get-server-output` (maybe)

Finally, we can bootstrap the project! Cross your fingers, say
your prayers or however your typical ritual for this goes:

```shell
docker compose up -d
docker compose down
docker compose up -d --force-recreate
docker compose up -d service-server --force-recreate
```

```shell
# Check status of each service
docker compose logs #--since=5m -f

```shell
# Start and stop an individual service
docker start service-db # service name
docker stop service-proxy # service name
```

```shell
docker exec -it iperf3-1 /bin/bash
docker exec -it iperf3-1 /usr/bin/iperf3 --help
```

## reference documents

[0]: https://www.openproject.org/docs/getting-started/
[10]: https://github.com/opf/openproject-docker-compose.git
[20]: https://hub.docker.com/r/networkstatic/iperf3

