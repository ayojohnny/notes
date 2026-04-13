# API Design Patterns | API Design Principles - Choosing Relationships

Before deciding on which relationships to choose, it is important that all resources
("things") are chosen upfront. Having a good idea over the domain of resources can
help lead to better modeling of relationships between resources.

Reference relationships should be purposeful and fundamental to desired API behavior.
- aim to accomplish primary goal
- not accidental or "nice-to-have" or "we need it later"

In-line data:
- store a duplicate copy inside a resources

Rely on reference:
- keep pointer to official data (via fields like `userId`)

Choosing between "in-lining" data vs referencing it depends on:
- questions being asked  
- actions being perfromed

```ts
// 1 call => bigger payload to due to in-line'd User info on Chatroom object.
function getAdminUserNameInline(chatroomId: string): string {
    let chatroomInline = GetChatroomInline(chatroomId);
    return chatroomInline.adminUser.Name;
}

// 2 calls => more processing time for simple information.
function getAdminUserNameInline(chatroomId: string): string {
    let chatroomReference = GetChatroomReference(chatroomId);
    let adminUser = GetAdminUser(chatroomReference.adminUserId);
    return adminUser.Name;
}
```

Pros of In-line:
- can reduce network API calls

Cons of In-line:
- can lead to oversending data that is not needed by calling client
- can lead to more CPU overhead due to JOINS from SQL queries to fetch the extra
  inline data.

Rule of thumb = optimize for common case w/o compromising feasibility of advanced case

Factors help considering in-line vs reference data:
- how often is this data accessed?
- how large is the request before in-lining extra data
- how large, estimated, will the in-line'd resoruce grow? Will User also have references to other Users inlined? (i.e. more bytes)
- how important is the data to be in-line'd in context of the resource in question? Do chatrooms need to know who the admin user is initially?

Hierarchical Relationships:
- imply cascading deletes & inheritance of behaviors and properties from parent to child (file permissions, deleting files w/in folder, etc.)

Signs to not use Hierarchy:
- avoid when using one-to-many relationships


Anti-Pattern: Creating Resources For Everything
// TODO: Fill out

Anti-Pattern: Deep Hierarchies
// TODO: Fill out

Anti-Pattern: In-Line Everything
// TODO: Fill out

Keypoints:
- only store relationships if they provide important functionality to the API
- sometimes a separate resource can simply be a data-type instead as in-line data
- avoid overly deep hierarhical relationships (hard to comprehend and manage)
