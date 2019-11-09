## Simple 01
```
kind: pipeline
type: docker
name: demo

steps:
- name: show README.md
  image: adoptopenjdk/openjdk8:jdk8u222-b10
  commands:
  - cat README.md


- name: compile Greet
  image: adoptopenjdk/openjdk8:jdk8u222-b10
  commands:
  - javac Greet.java
  - ls 
  when:
    branch:
    - feature/*

```
## Complex
```
kind: pipeline
name: demo

steps:
  - name: migrations
    image: flyway/flyway:6.0.6
    commands:
      - "/flyway/flyway migrate"

  - name: mvn clean package
    image: maven:3.6.2-jdk-8
    commands:
      - mvn clean package

  - name: delivery
    image: plugins/docker
    settings:
      repo: fagoner/blessings
      username:
        from_secret: docker_username
      password:
        from_secret: docker_password

services:
  - name: mysql
    image: mysql:5.7.26
    detach: true
    environment:
      MYSQL_ROOT_PASSWORD: r00t

```

