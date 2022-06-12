## Idempotence

Idempotence is **any function that can be executed several times without changing the final result beyond its first iteration**.



Idempotence is a technical word, used in mathematics and computer science, that classifies a function’s behavior. There are certain [identity functions](https://en.wikipedia.org/wiki/Identity_function), such as a = a, that can be called idempotent.

As a fucntion, it can be expressed as:

```
f(f(x)) = f(x)
```

That means that an operation can be performed on x to return y. Then, if that same function were performed on y, the result would still equal y.



Idempotence is a safe practice for [DevOps teams](https://www.bmc.com/blogs/devops-culture/) when developing applications. Idempotence ensures a safe, quality experience for both users and software teams. No one has to go in afterwards and clean up a mess.

​	For example, idempotence is the design standard for [Ansible](https://www.ansible.com/), a [DevOps](https://www.bmc.com/blogs/devops-basics-introduction/) tool for [system administrators](https://www.bmc.com/blogs/sysadmin-role-responsibilities-salary/) to manage their servers. Ansible can automate the server setup process, consistently create the same servers, and automatically deploy them. There is a lot of [orchestration](https://www.bmc.com/blogs/workflow-orchestration/) that occurs in automating this process—and it is idempotent behaviors that ensure only one directory gets created on a server, and only an exact number of servers get created.

Idempotent behavior is ever more crucial in [cloud computing](https://www.bmc.com/blogs/advantages-benefits-cloud-computing/) and [edge devices](https://www.bmc.com/blogs/edge-computing/). When multiple accounts can be logged in at once, accessed from different locations and different devices, updated from multiple user accounts, and data sent from one place to another, idempotent design helps manage the application’s state more efficiently and without error.



### Sample idempotent functions



**Idempotent HTTP functions**:

In the land of [HTTP methods](https://www.bmc.com/blogs/rest-vs-crud-whats-the-difference/), the GET, DELETE, and PUT functions are idempotent.

The GET method retrieves information from an HTTP endpoint. Whatever information GET asks for will be the same information again and again. This behavior is illustrated by hitting refresh on an internet browser. The browser pings an IP address and gets information. If GET weren’t idempotent, perhaps it would stack more and more pages on top of each other, adding each refreshed page in the browser’s cache. DELETE has similar behavior.

PUT is also an idempotent function—but POST is not. In HTTP, PUT will define a value, and continue to define the value as whatever is stated.

POST works differently. POST can send the same value repeatedly, but it adds an element to a collection. POST could repeatedly send the same Twitter status 10 times per hour, and all the followers will receive 10 status updates all saying the same thing. The PUT function just puts the status out there once.



**Example of idempotence in Front-end design**:

Payment button

If this were to be turned into an idempotent design, the function would pass through an object before being submitted to the credit card service. Instead of contacting the credit card service directly, the submit button might store the user information in a data model, in which one of the values says paymentSubmitted = True and one value says paymentVerified = False.

By creating a variable paymentSubmitted = True, and checking this value before submitting the card information, when the user presses the “Pay Now” button multiple times, it will only go through once when the Submitted variable equals false and all other presses will be null, as the function waits for its initial submission to return.











