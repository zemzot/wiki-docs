While a good wiki is one where anyone can contribute new content, it's always a good idea to restrict certain sections and specific actions to a list of selected users.

Wiki.js has a powerful permission system with fine grained control over what your users can see and do.

# Overview

The permission system of Wiki.js is based on 4 concepts:

- **Groups**
- **Users**
- **Permissions**
- **Page Rules**
{.grid-list}

A group contains multiple users, a set of permissions and a list of page rules.

![diag-permissions.jpg](/assets/diagrams/diag-permissions.jpg =1000x){.decor-shadow .radius-4}

A **user** can be part of **one or more** groups.

A **group** defines what users can see and what they can do. This is achieved by using 2 concepts: **Global Permissions** and **Page Rules**.

A **global permission** gives the right to a user to perform a very specific action. For example, the global permission `read:pages` allows the user to view pages, while the global permission `write:assets` allows the user to upload images and files. These global permissions act as a master switch to **allow or deny** a specific action on the wiki.

While global permissions are great a limiting the user to perform only a specific set of actions, it lacks control on **where** these permissions are applied. For example, you might want a user to be able to view pages under `/cities` but not pages under `/secret`. This is where **Page Rules** come into play.

A **page rule** specifies exactly where permissions are applicable.

---

**Let's use the following example:**
*We want users of group XYZ to be able to view pages and view assets where the path is exactly `/cities/montreal`.*

The page rule would be defined as:

- Allow or Deny: `Allow`
- Permissions: `read:pages, read:assets`
- Rule Pattern: `Path matches exactly...`
- Rule Value: `/cities/montreal`
{.grid-list}

![ss-pagerule-ex1.png](/assets/examples/ss-pagerule-ex1.png =1000x)

If we combine all the concepts together, the group would:

- Have one or more users
- Have the global permissions `read:pages` and `read:assets` enabled
- Have a page rule of `Allow` permissions `read:pages, read:assets` where `Path matches exactly`... `/cities/montreal`

---
