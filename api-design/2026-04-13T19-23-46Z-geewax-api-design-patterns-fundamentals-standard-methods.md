# API Design | Fundamentals - Standard Methods

Standard Actions

Name        | Example               | Description
--          | --                    | --
List        | ListChatRooms()       | Lists a collection of resources
Get         | GetChatRoom()         | Retrieves an existing resource
Create      | CreateMessage()       | Creates a new resource
Update      | UpdateUserProfile()   | Updates an existing resource
Delete      | DeleteChatRoom()      | Removes an existing resource
Replace     | ReplaceChatRoom()     | Replaces an entire resource


Cross-cutting aspects for all standard methods:
1. Is it hard requirement that all resources must support all standard actions?
    - if one of my resources is immutable, should is support the `Update` action?
    - if the resources is permanent, should it support the `Delete` action?

Not every standard method is required for each resource type. Should distinguish when
method is not supported (405 Method Not Allowed) and when a method is not permitted
on a specific instance (403 Forbidden)

What should never happen is omitting a specific route and returning `404 Not Found`
when someone attempts to use the method on a resource.

Implies **resource** doesn't exist, not true. What's true is that the **action** does
not exist for the given resource.

Guidelines:
- implement all methods (use 405 for methods that are not allowed)
- on immutable resources (update doesn't make sense) & permanent (no DELETE) use 403 Forbidden

Standard Actions:
- should not have any side effects or unexpected behavior

Idempotence:
- repeating same request (with same params) multiple times will have same effect as
single request.

Side Effect example:

In an email API, creating an email + storing it in the DB is not a side effect. 
If the standard create method also tries to connect via SMTP to a server and send
the email, that would be a side effect

Side Effects:
- connecting to 3rd party or external services
- triggering additionally work that has potential to make standard action fail
  or be partially executed
