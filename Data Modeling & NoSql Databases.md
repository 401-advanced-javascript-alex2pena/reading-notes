# Javascript Data Modeling

- Consistantly describe *"things"* both physically(properties) and behaviorially(actions)
- You can create logic, workflows, and applications that use/modify data
- JS has built in data types: *Objects, Arrays, Strings, Numbers, & Booleans*
- boolean values should always be used when there are only 2 states
- Numbers only when arithmatic is needed or applied
- Strings when representing natural language
- Arrays when bundling or grouping similar segments of data

## Modeling Behavior
*CRUD Basic Operations*
- `CREATE` - Add a record to a data store
- `READ` - Retrieve a record from a data store
- `UPDATE` - Update a record within a data store
- `DELETE` - Remove a record from a data store

# Databases

## SQL
- Postgress, SQL Server, Oracle... are relational with rows and columns and keys
- Highly structured & great for reporting or tabular data

## NoSQL
- Pulls information into one record tracked by an ID
- The ID acts like an object without structure
- it is pure json files that are flexible

### NoSQL Data Modeling
- Model documents with data that is needed rather than what is available
- Takes up more space with duplicate data but lookup speed is the advantage
