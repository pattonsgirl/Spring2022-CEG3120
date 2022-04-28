# CEG 3120 - Spring 2022 - Final Exam Key

1. Identify 2 load balancing allocation strategies and describe how they distribute traffic among a pool of servers.

- round robin
- least connections

2. What is the purpose of GitHub secrets (or any secret manager)? Describe in terms of protection and usage of the stored information.

- Keep information like credentials safe / vaulted (and stored encrypted). Such secrets can then be "called", usually by a variable name, when needed in the workflow

3. Explain the security groups rules given the following definition from a CloudFormation template and determine if the rules apply to inbound or outbound traffic:

```
ExamSecurityGroup:
    Type: 'AWS::EC2::SecurityGroup'
    Properties:
      VpcId: !Ref VPC
      SecurityGroupIngress:
        - IpProtocol: tcp
          FromPort: '1'
          ToPort: '500'
          CidrIp: 10.0.0.0/24
        - IpProtocol: tcp
          FromPort: '22'
          ToPort: '22'
          CidrIp: 158.25.90.34/32
        - IpProtocol: tcp
          FromPort: '80'
          ToPort: '80'
          CidrIp: 0.0.0.0/0
```

- rules apply to inbound traffic - `SecurityGroupIngress`
- 10.0.0.0/24 (likely VPC or subnet in VPC) are open on ports 1-500
- 158.25.90.34/32 (likely a trusted IP) has port 22 (SSH access)
- 0.0.0.0/0 (any IP) has port 80 open (HTTP access)

4. How does an instance communicate with the world via a NAT Gateway?

- Technical explanation: instances are on a private subnet. The internet gateway and NAT gateway are attached to a public subnet. The route table on the private subnet is configured to send external traffic (destination in 0.0.0.0/0) to the NAT gateway. The NAT gateway has a private IP on the subnet (so devices can send traffic to it) and public (or elastic) IP address associated with it. The NAT gateway then acts like a border router. Traffic sent through it will be labeled with the public IP, and returned to the device within the private subnet via its private IP.

5. What benefit do continuous integration pipelines, like GitHub Actions, provide an organization?

- They allow for workflows and pipelines for an organizations code base. Using Project 5 as an example - when developers with access to the code repo they can trigger code tests, new builds, and new deployments of the project. This also keeps manual errors in workflow to a minimum.

6. I have files in a local repository that I don't want accidentally push to GitHub. What should I do?

- List files in a .gitignore file. Make sure the paths are relative to within your repo folder so that the ignores will apply if you clone to another machine / location

The next three questions:  
For the following GitHub Action yml definition...

```
name: exam-workflow
on:
  push:
    branches:
      - 'prod'
jobs:
  execute:
    runs-on: ubuntu-18.04
    steps:
      - uses: actions/checkout@v2
      - run: apt install python3 python3-pip
      - run: pip3 install black
      - run: black my-code.py
```

7. What runner is used?

- `ubuntu-18.04`

8. What event triggers the workflow?

- push to branch prod

9. What does actions/checkout@v2 do?

- checks out repository to runner

10. Repositories hosted on services, like GitHub and Dockerhub, can be configured to deliver payloads to webhooks when events happen.

- True

11. In a folder, I have a Dockerfile and a folder named proj with code inside.  
    Write a command that will build a container image named bubbles and a tag of 2.3

- `docker build -t bubbles:2.3 .`

12. I have an image, bubbles:2.3 The image will run an application that listens on port 42.  
    Write a command that will run the container as a detached process and bind it to port 8080 on my host.

- `docker run -d -p 8080:42 bubbles:2.3`

13. Once an image exists in a public image repository (like we configured on DockerHub), to run a container from that image three things need to be set up:

- 1. The system needs a OCI compliant software that can run containers from images (like Docker)
- 2. The image needs to be pulled from the image repository (like DockerHub)
- 3. A container can be started from the image.
- True

14. The cloud and services that run on it never have downtime.

- False

15. I have chosen to use the nginx image from the official build for NGINX as a base image. In my Dockerfile is as follows:

```
FROM nginx
COPY html/ /var/www/html/
```

However, when I build the container image and run a container using the image, I don't see my site content...  
What's wrong?  
https://hub.docker.com/_/nginx

- `COPY` needs to be from `html/` TO `/usr/share/nginx/html`

16. A container will exit if it does not have an active foreground process running in it.

- True

17. How can I get the status of a service on my system (think apache, nginx, or haproxy)

- `sudo systemctl status <service>`

18. Two services can listen on the same port on the same machine. For example, haproxy and apache2 can listen on port 80 on the same machine and both can work.

- False

19. Let's assume I have successfully installed a webhook receiver on a server with IP 129.32.45.190

Also assume it is the same webhook we have been discussing in class (adnanh/webhook).  
I create a hook definition file as follows:

```
[
    {
          "id": "bubbles",
          "execute-command": "/home/ubuntu/pull-restart.sh"
      }
]
```

What URL can I deliver payloads to?

- `http://129.32.45.190:9000/hooks/bubbles`

20. I have a DockerHub token with read access. I can push new images new the repository using the token.

- False. Would need write access
