# security

keeping notes on security stuffs.


## Kali Linux

running using Kali Linux docker image

```
docker pull kalilinux/kali-rolling:latest
docker run -it kalilinux/kali-rolling:latest /bin/bash
```

updates 

```
apt update
apt upgrade
apt autoremove
apt clean
```

useful install
```
apt install kali-linux-top10
apt install man-db
apt install exploitdb
```

saving a copy of the update as new image

exit the running container, and list stopped container

list containers
```
docker ps -a
```

save a copy of the container
```
docker commit <CONTAINER ID> my-kali
```

run your image in the future
```
docker run -ti my-kali /bin/bash
```

Persistent

```
docker run -ti --rm --mount src=kali-root,dst=/root --mount src=kali-postgres,dst=/var/lib/postgresql my-kali
```

the above volume location can be obtained using the below command

```
docker volume inspect kali-root kali-postgres

[
    {
        "CreatedAt": "2019-12-19T02:44:27Z",
        "Driver": "local",
        "Labels": null,
        "Mountpoint": "/var/lib/docker/volumes/kali-root/_data",
        "Name": "kali-root",
        "Options": null,
        "Scope": "local"
    },
    {
        "CreatedAt": "2019-12-19T02:23:58Z",
        "Driver": "local",
        "Labels": null,
        "Mountpoint": "/var/lib/docker/volumes/kali-postgres/_data",
        "Name": "kali-postgres",
        "Options": null,
        "Scope": "local"
    }
]
```

- This will create two volumes named kali-root and kali-postgres — or use existing ones on subsequent runs — and map them to the created container.

- --rm switch makes Docker delete the container once it stops (i.e. once you exit the shell). This is perfectly fine (and preferred behaviour — you don’t want to waste storage on a bunch of stopped containers) as you have all the components — the image and the two volumes — to recreate it.

## Security

- [CIS Benchmark Docker](https://github.com/docker/docker-bench-security) - docker setup analysis
- [OpenSCAP](https://www.open-scap.org/) - system analysis 
- [SonarQube](https://www.sonarqube.org/) - code analysis
- [OWASP Zed Attack Proxy (ZAP)](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project) - Web application pen test
- [Aqua CIS Docker tool](https://github.com/aquasecurity/docker-bench)
- [Aqua CIS Kubenetes tool](https://github.com/aquasecurity/kube-bench)
- [Aqua kube-hunter](https://github.com/aquasecurity/kube-hunter)
- [Metasploit penetration testing framework](https://metasploit.com/)


# Resources
1. [Kali LinuxRevealed: Mastering the Penetration TestingDistribution](https://kali.training/downloads/Kali-Linux-Revealed-1st-edition.pdf)
2. [Kali Linux Revealed Online Course](https://kali.training/lessons/introduction/)
3. [Debian Jessie from Discovery to Mastery](https://debian-handbook.info/get/now/)
4. [Kali Linux In a Docker Container](https://medium.com/@airman604/kali-linux-in-a-docker-container-5a06311624eb)
5. [CIS Benchmark - Kubernetes](https://www.cisecurity.org/benchmark/kubernetes/)
6. [CIS Benchmark - Docker](https://www.cisecurity.org/benchmark/docker/)
7. Free course: [Metasploit](https://www.offensive-security.com/metasploit-unleashed/)
8. Free course: [Kali Linux Training](https://kali.training/)

