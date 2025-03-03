**We switched to storing our database in the local storage as it would be less complex.* [Link to the new ADR](https://github.com/cse110-sp24-group23/cse110-sp24-group23/blob/main/specs/adrs/051224-Database-LocalStorage.md).

# Using SQLite to make and maintain the database

## Context and Problem Statement

How should we store the data that the user saves?
How much data is expected to be saved by users?

## Considered Formats to Store Data

* JSON
* SQLite

## Decision Outcome

Chosen option: "SQLite" because allows the whole database to be stored as a single file on a host computer. Moreover, JSON is just a format to store the database. So, we would still need SQLite to manage the database. Storing the database through SQLite ensures that the data creation and updates occur within the same resulting in easier management of the data. 
