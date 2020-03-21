# build os

dosctl installed to your PATH, change to a (empty) working directory and build kernel+initrd
```
dosctl os <YML-FILE>
dosctl <YML-FILE>
```

# run os

Execute from the same working directory as above. YML-File or project name (YML file name without extension). Local installed qemu is needed.
```
dosctl run <YML-FILE>
```

# Build docker image

```
dosctl img dengleros/os-rustysd:latest -build -push
```

# services in container

All services run in crun container.
```
/ # crun list 
NAME   PID       STATUS   BUNDLE PATH                            
rngd   825       running  /containers/services/rngd              
udhcpc 826       running  /containers/services/udhcpc            
mdevd  827       running  /containers/services/mdevd             
sshd   824       running  /containers/services/sshd
```

# gpm package manager

Successfully booted DenglerOS try to install example package with gpm (git package manager)
```
gpm update
gpm install docker
/prepare.sh /containers/services/docker  # workaround to update unitfile... without trailing "/"!!!
rsdctl /var/run/rustysd/control.socket reload  # update / add new service to rustysd
rsdctl /var/run/rustysd/control.socket restart docker.service   # (re-)start service "docker"
crun exec -t docker docker run --rm -ti alpine sh   # :)
```
