# Database Fundamentals Course
## History of data persistence
Cloud storage has a great pro compared to other storage methods because it is accessible from anywhere in the world. It is also centralized and can be used by several people at the same time.
Databases come in when we transition to digital media.
Types of databases:
Relational: In the industry there are several companies dedicated to be relational database managers such as SQL Server, Oracle, MariaDB, among others.
Non-relational: They are still advancing and there are very different examples such as cassandra, elasticsearch, neo4j, MongoDB, among others.

## Services:
Self-managed: This is the database that you install yourself and take care of updates, maintenance, etc.
Managed: Services offered by modern clouds such as Azure and you don't have to worry about maintenance or updates.

## Database origin
Databases arise from the need to conserve information beyond what exists in RAM memory.
File-based databases were data stored in plain text, easy to store but very difficult to query, and relational databases were born out of the need to improve on this. Their inventor Edgar Codd left certain rules to ensure that the whole philosophy of databases was not lost, standardizing the process.

## Relational databases
### Entity
An entity is something similar to an object (object-oriented programming) and represents something in the real world, even something abstract. They have attributes which are the things that make them an entity and by convention are put in plural.


<br>
<img src="https://github.com/brendamrdz/week2-course6-batabase/blob/main/images/entity.jpg?raw=true" alt="alt text" width="30%" height="auto">
Key attributes are those that identify the entity and cannot be repeated. They exist:
Natural: they are inherent to the object such as the serial number.
Artificial key: is not inherent to the object and is assigned arbitrarily.
Strong entities: are entities that can survive on their own.
Weak entities: cannot exist without a strong entity and are represented by a square with a double line.
Weak identities by identity: they do not differ from each other except by the key of their strong identity.
Weak identities by existence: they are assigned a key of their own.

Translated with www.DeepL.com/Translator (free version)
