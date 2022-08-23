---
title: Learning Domain Driven Design
author: Vlad Khononov
---

# Learning Domain Driven Design

## Integration of Bounded Contexts

When two or more bounded contexts need to be integrated, there are some patterns defined depending on the relationships of the team: **Cooperation, Customer-Supplier, Separate Ways**

### Cooperation
Both team success depends on one another. They have to define protocols to communicate between:
- Partnership model: both team adapt to each other's API.
- Shared Kernel: Some part of the context is shared. These model is better applied to core subdomains since those are the ones that change more often. ==Shared kernels should only be used when the cost of duplication is higher than the cost of sharing==

### Customer-Supplier
	The service supplier is called upstream and the client is called downstream
Both teams can succeed independently in this case. The patterns used are:
- Conformist: The downstream team has to conform to the upstream.
- Anticorruption Layer: Same as the prev but in this case the downstream implements an anticorruption layer to transform the other team's bounded context model into one more usable for them.
- Open-Host Service: This time the upstream is going to adapt to the clients. The supplier establishes a **published language** that is used by the other team. This language can be different from the organization official language. Different versions can be deployed.

### Separate Ways
In this case the two teams go on their different ways. These can mean communication issues or that the shared subdomains are very generic that is best just to replicate them.

### Context Map
This diagram shows how we can model the relationships between contexts on a business. For example in this case, the legacy system is sharing something with the billing. Also the marketing marketing conforms to the billing team.

![[Pasted image 20220815165201.png]]

# Implementing Simple Business Logic

## Transaction Script
On this approach we use direct comunication with the database via `SQL` and include the use of transactions. The approach should be ==all or nothing==.
A common mistake is using different transactions on the same funciton, leading to inconsistent results. Other thing can be that the transaction succeeds but the service in charge of sending a response fails, in that case the client might try again but that can duplicate the action. We can use this approach for very simple business logic.

## Active Record
An active record is an object that includes basic CRUD operations. It is the next level of abstraction after transactions. For example we can create a object called `User` like Sequelize and we need to implement methods to save it, remove it, find one, etc. We can use this approach for simple business logic with complex data structures.

	Neither of these two should be used for core sub domains.


# Implementing Complex Business Logic
To implement complex business logic there is a need of using a more strict structure. 
## Domain Model
The domain model is a collection of behaviour and data. The domain model is composed of
- aggregates
- value objects
- domain events
- domain services

### Value Objects
A value object can be identified by the composition of its values. It does not need an unique identifier to differentiate it from the others. For example colors: each color has a unique rgb combination.
Value objects help us to leave behind generic data types. 
	We can use the value objects to place the **valid**