## About playbook

This playbook installs NTP service on the host.

## Parameters

- <FULL_PATH_TO_PLAYBOOK> - The full path to the playbook on your host.
- <NTP_AREA> - The area to use the NTP servers from. Available values:
- <HOST_USER> - The non-root user of the host.

```
europe
asia
north-america
```

## How to run

In order to launch the playbook please run the following command:

```
docker run --rm -it --name adop-e_ansible -e ANSIBLE_HOST_KEY_CHECKING=False \
			-v /:/rootfs:rw dockerhub.accenture.com/adope/docker-ansible:1.0 \
			/bin/sh -c "ansible-playbook -c paramiko /rootfs/<FULL_PATH_TO_PLAYBOOK> -i $(curl -s http://169.254.169.254/latest/meta-data/local-ipv4), -e \"NTP_AREA=<NTP_AREA>\""
```