---
type: literature
status: to-view
topic: devops 
---

- Topic : #VeilleIT/devops 
- Tags : #dotnet #microservices #kubernetes


Source : [.NET Microservices – Full Course - YouTube](https://www.youtube.com/watch?v=DgVjEo3OGBI&t=992s)

# Ideas


## PART 1 - INTRODUCTION & Theory


### What are microservices?

#### 1 microservices :
- small (2weeks)
- do 1 thing well
- organization aligned
- part of (distributed) system
- self contained / Autonomous

#### Monolith:
- difficult to change
	- manual testing
	- month cycles
- difficult to scale
- Locked in
	- tech
	- vendor if outsourced


#### Exemple

> [!example] 
>  ![[Z. Assets/0810ee5953b16aaf50f915540212bd08_MD5.png]]


> [!important] 
> Microservices are always coupled but we want to reduce to the max the number of messages between them


### Overview of our microservices

#### Plateform Service

- Asset register
- Track all the platform/system in company
- Build by infra team 
- used by
	- infra 
	- support
	- accounting
	- R&D

#### Commands Service

- repo of CLI argument for given platform
- aid in automation of support process
- build by tech team
- used by
	- tech
	- infra 
	- R&D

### Solution Architecture

> [!summary] 
>  ![[Z. Assets/5c6d15103f39b331f5c0984a36d35a77_MD5.png]]


> [!hint] 
>  ![[Pasted image 20240116102020.png]]




### Application Architecture 

#### plateform 

![[Z. Assets/2e820f8d85fc3e9c2bffd58441c19ea0_MD5.png]]

#### Commands 

![[Z. Assets/8da05daf87fb8f4b5cc3dbcda6be6558_MD5.png]]

## PART 2 - BUILDING THE FIRST SERVICE

### Scaffolding the service
### Data Layer - Model
### Data Layer - DB Context
### Data Layer - Repository
### Data Layer - DB Preparation
### Data Layer - Data Transfer Objects
### Controller and Actions

## PART 3 - DOCKER & KUBERNETES

### Review of Docker
### Containerizing the Platform Service
### Pushing to Docker Hub
### Introduction to Kubernetes
### Kubernetes Architecture Overview
### Deploy the Platform service

## PART 4 - STARTING OUR 2ND SERVICE

### Scaffolding the service
### Add a Controller and Action
### Overview of Synchronous and Asynchronous Messaging
### Adding a HTTP Client
### Deploying service to Kubernetes
### Adding an API Gateway


## PART 5 - STARTING WITH SQL SERVER

### Adding a Persistent Volume Claim
### Adding a Kubernetes Secret
### Deploying SQL Server to Kubernetes
### Accessing SQL Server via Management Studio
### Updating our Platform Service to use SQL Server

## PART 6 - MULTI-RESOURCE API

### End Point Review for Commands Service
### Data Layer - Models
### Data Layer - DB Context
### Data Layer - Repository
### Data Layer - Dtos
### Data Layer - AutoMapper Profiles
### Controller & Actions

## PART 7 - MESSAGE BUS & RABBITMQ

### Solution Architecture Overview
### RabbitMQ Overview
### Deploy RabbitMQ to Kubernetes

## PART 8 - ASYNCHRONOUS MESSAGING

### Add a Message Bus Publisher to Platform Service
### Testing our Publisher
### Command Service ground work
### Event Processing
### Adding an Event Listener
### Testing Locally
### Deploying to Kubernetes

## PART 9 - GRPC

### Overview of gRPC
### Final Kubernetes networking configuration
### Adding gRPC Package references
### Working with Protocol Buffers
### Adding a gRPC Server to Platforms Service
### Adding a gRPC Client to Commands Service
### Adding a Database prep class to Commands Service
### Test Locally
### Deploy to Kubernetes
### Final thoughts & thanks
### Supporter Credits





Linked Sources :
- [[🌐.NET Microservices. Architecture for Containerized .NET Applications  Microsoft Learn]]