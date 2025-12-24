build with podman build -t hackspace-mgmt:latest .

run with podman run --name hs-mgmt --network host --rm localhost/hackspace-mgmt:latest

access on your web browser at localhost:5000

# Quadlet
https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/8/html/building_running_and_managing_containers/assembly_porting-containers-to-systemd-using-podman_building-running-and-managing-containers

Create the <CTRNAME>.container unit file in one of the following directories:

    For root users: /usr/share/containers/systemd/ or /etc/containers/systemd/
    For rootless users: $HOME/.config/containers/systemd/, $XDG_CONFIG_HOME/containers/systemd/, /etc/containers/systemd/users/$(UID), or /etc/containers/systemd/users/ 

The orchestration technology used in production is quadlet https://docs.podman.io/en/latest/markdown/podman-systemd.unit.5.html
The two important settings for allowing the container to use the peer authentication with postgress are:

```
[container]
Annotation="run.oci.keep_original_groups=1"
UserNS=keep-id
```
