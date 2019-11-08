## Simple 01
```
kind: pipeline
type: docker
name: demo

steps:
- name: show README.md
  image: adoptopenjdk/openjdk8:jdk8u222-b10
  commands:
  - javac Greet.java
  - ls 
  when:
    branch:
    - feature/*
```

