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