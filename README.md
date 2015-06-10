# elasticbeanstalk-docker-ulimit-example
Example Elastic Beanstalk Docker project that updates the ulimit settings using the following ebextensions config:

```
files:
  "/etc/security/limits.conf":
    mode: "00644"
    owner: "root"
    group: "root"
    content: |
      *         hard    nofile      65536
      *         soft    nofile      65536

commands:
  01restart_docker:
    command: /sbin/service docker stop && ulimit -n 65536 && /sbin/service docker start

```
