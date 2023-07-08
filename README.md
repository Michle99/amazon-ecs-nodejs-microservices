# Node.js Microservices Deployed on EC2 Container Service

This is a reference architecture that shows the evolution of a Node.js application from a monolithic
application that is deployed directly onto instances with no containerization or orchestration, to a
containerized microservices architecture orchestrated using Amazon EC2 Container Service.

- [Part One: The base Node.js application](1-no-container/)
- [Part Two: Moving the application to a container deployed using ECS](2-containerized/)
- [Part Three: Breaking the monolith apart into microservices on ECS](3-microservices/)

# Common Errors
Encountered the below errors when building the Node.js microservices.

![common session error](./images/common_session_token-error.png)

Solution to error:
```
aws configure set aws_session_token "<<your session token>>"
```

# Verify Deployment Results
1. [Get Post by userId](http://api-a-publi-1m6e6ggbr8tfe-440222643.us-east-2.elb.amazonaws.com/api/posts/by-user/4)

```
[{"thread":1,"text":"Has anyone checked on the lich recently?","user":4}]
```

2. [Get User by UserId](http://api-a-publi-1m6e6ggbr8tfe-440222643.us-east-2.elb.amazonaws.com/api/users/2)

```
{"id":2,"username":"finn","name":"Finn 'the Human' Mertens","bio":"Adventurer and hero, last human, defender of good"}

```

3. [Get threads by threadId](http://api-a-publi-1m6e6ggbr8tfe-440222643.us-east-2.elb.amazonaws.com/api/threads/2)

```
{"id":2,"title":"Party at the candy kingdom tomorrow","createdBy":3}
```

4. [Get posts by threadId](http://api-a-publi-1m6e6ggbr8tfe-440222643.us-east-2.elb.amazonaws.com/api/posts/in-thread/2)
```
[{"thread":2,"text":"Come party with the candy people tomorrow!","user":3},{"thread":2,"text":"Mathematical!","user":2},{"thread":2,"text":"I'll bring my guitar","user":1}]
```


# Clean Up Resources

```
copilot app delete --name api .
```

# Resources

[Break a Monolithic Application into Microservices with AWS Copilot, Amazon ECS, Docker, and AWS Fargate
TUTORIAL](https://aws.amazon.com/getting-started/hands-on/break-monolith-app-microservices-ecs-docker-ec2/)