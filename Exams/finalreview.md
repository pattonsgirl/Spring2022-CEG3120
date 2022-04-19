# Final Review for CEG 3120

## Spring 2022

## Da Rules

Midterm: Monday, 2/25

- Available 8:00 AM to 11:59 PM
- 1 attempt, 2 hours once started
- Open note, open terminal
- I will be in Russ 355 from 12:30 to 2:30 PM if you want to take the exam in the room

## Week 1 & 2

- create aws stack
- terminal command reminder
- users
- permissions
- ssh keys
  - private vs public
  - .ssh/config
  - .ssh/authorized_keys
  - .ssh/known_hosts
- git & GitHub
  - clone
  - init
  - add
  - rm (and rm --cached)
  - commit
  - push
  - pull
  - branch
  - fetch / merge
  - checkout
  - merge conficts
  - Pull Requests
  - .gitignore
  - markdown essentials

### Project

- git guide

## Week 3

- crash course python notes
- package version dependencies and usage
- APIs
  - REST APIs
    - querying
    - version dependent (how queries are requested can change)
  - syncronous vs asyncronous APIs
  - Requesting and using OAuth keys
- authentication vs authorization
  - OAuth - allow third party to do x y z
  - JSON Web Tokens & session cookies
    - keeping you logged in and maintaining session details
- process exploration
  - bot runs as long as starting terminal is open
  - screen / background jobs (2350) - detaching processes
  - cloud solutions?
  - containers?

### Project

- Discord Bot using Discord API w/ discord.py
- managing secrets for a project
- using branches for changes

## Week 4

- linters and unit tests
  - using hooks to trigger
- networking review
  - IPv4 addresses
  - Subnets & CIDR notation
  - routes
  - gateways
  - NAT
  - Firewalls
    - network wide (AWS Security Groups)
    - per machine (iptables)

## Week 5

- the cloud
  - types of cloud services
  - regions
  - access management of cloud resources
    - token based can create(?) access(?) delete(?) view billing(?)
- intro to navigating AWS
  - EC2 instance types
  - images / AMI
  - networking (VPC, subnet, gateways, routes, security group)

### Project

- Manually creating the resources
  - VPC
  - instance type & AMI
  - EIP to instance

## Week 6

- intro to contents of CloudFormation Template
  - using YAML/JSON formatted files
- system logs & service control
- installing and configuring a webserver
  - apache vs nginx
  - status / control of services (systemctl)
  - service logs (apache & ssh)
  - security groups
  - iptables? system level firewalls
  - nmap -p 1-5000 server

### Project

- Create CloudFormation template
  - should mimic what was manually created

## Week 7

- proxies (forward & reverse)
- load balancing terminology
  - hosts
  - pools
  - config file settings
    - global / defaults/ frontend / backend
  - layer 4 (tcp) load balancing
  - layer 7 (http) load balancing
  - Allocation strategies
    - Round robin
    - Weight round robin
    - Least connections
    - Least response time

## Week 8

- NAT Gateways
  - one EIP, external communication allowed
- messing with a webserver
  - HTTPS vs HTTP and notes on certificates
- load balancing and fault tolerance
  - HAproxy configurations
  - keeping backend servers private - when are public IPs needed?
  - fault tolerance of non-responsive backends
- monitoring
  - Networked systems (Grafana?)
  - cloud costs and usage

### Project

- CF Template
  - create three instances
  - create one NAT gateway? Connect two instances to that?
- Configure load balancer
- Configure hosts to hold unique content

## Week 9 & 10

- containers using Docker
  - purpose & constraints
  - images & image selection
    - `docker pull ___`
    - `docker images`
    - `docker image rm ___`
  - Running containers
    - `docker run` + options (`--name`, `--rm`, `-v`, `-p`, `-d`, `-it`)
    - `docker ps` + `-a`
    - `docker kill ___` (or) `docker stop ___`
    - `docker rm ___` (and why...)
  - Dockerfiles (recipes)
    - `docker build` + `-t`
    - `FROM`, `WORKDIR`, `RUN`, `COPY`, `CMD`
  - using container registry (DockerHub)
    - `docker push ___`
    - tagging considerations

## Week 11

- Continuous integration using GitHub Actions

## Week 12

## Week 13

## Week 14

- secret sharing and containers
  - Have secret on individual host, share with container on run using a bind mount (-v HOST:CONTAINER)
