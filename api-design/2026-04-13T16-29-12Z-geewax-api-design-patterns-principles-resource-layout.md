# API Design | Resource Layout
> Chapter 4 of API Design Patterns (Geewax)

Resource Layout: arrangement of "things" (resources) in an API. 
- focused on how resources relate to one another through:
    - fields that define the resources
    - relationships between resources

Resource Relationships

Type            | Description
--              | --
Reference       | one resource refers to or points at another resource
Many-to-Many    | each resource points to multiple instances of each other
Self Reference  | a resource points to another resource of the **exact same type**
Hierarchical    | (see section)

An example of Self-Reference relationships would be an `Employee` resource pointing
at other employee resources as managers as assistants.

```
{
    employeeId: 1,
    firstName: "Bob",
    lastName: "Smith",
    managerId: 90 // The self-reference is here, since manager is also employee
}
```

Self-referencing relationships are often used in hierarchical relationships
- network style APIs where data can be directed graphs
- data is a node in some tree


Hierarchical Relationships:
- reflects containment or ownership between resources (i.e. think directories on Linux)

"This might seem innocuous, but this special relationship implies some important
atttributes and behaviors. For example, when you delete a folder on your computer,
generally all the files (and other folders) contained insdie are likewise deleted.
Of, if you are given access to a specific folder, that often implies acces to the
files (and other folders) inside. These same behaviors have come to be expected from
resources that behave in this way."

In the Chatroom API example:
- having access to a `Chatroom` implies access to all `Messages` resources inside the chatroom
- delete a `Chatroom` resource implies cascade deleting all `Messages`

Challengs to Hiearchical Relationships:
- can resources change parents? (cna a `Message` move from one `Chatroom` to another?)

