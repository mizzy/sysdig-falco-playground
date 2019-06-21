# Sysdig Falco Playground

## References

- [Falco | Sysdig](https://sysdig.com/opensource/falco/)
- [Falco - Container Native Runtime Security](https://falco.org/)
- [Falco - Container Native Runtime Security](https://falco.org/docs/)

## Installing Falco

```sh
$ vagrant ssh
$ sudo apt-get -y install linux-headers-$(uname -r)
$ sudo docker pull falcosecurity/falco
```

## Running Falco

```sh
$ sudo docker run -i -t \
    --name falco \
    --privileged \
    -v /var/run/docker.sock:/host/var/run/docker.sock \
    -v /dev:/host/dev \
    -v /proc:/host/proc:ro \
    -v /boot:/host/boot:ro \
    -v /lib/modules:/host/lib/modules:ro \
    -v /usr:/host/usr:ro \
    falcosecurity/falco
```

## Checking Falco running

Install event generator.

```sh
$ vagrant ssh
$ sudo docker pull sysdig/falco-event-generator
```


```sh
$ sudo docker run -it --name falco-event-generator \
  sysdig/falco-event-generator
```

By running falco-event-generator, falco daemon will output logs.
