# Hangout Video Chat Application Project

## Purpose

- The purpose of this project is to get a decent dive into the realm of Web Socket and Web RTC (Real-Time Chat) applications.

## Stack

- Frontend

  - React JS
  - Typescript
  - Web RTC (Simple-Peer)

- Backend
  - NodeJS
  - Redis Caching
- DevOps
  - Docker
  - Nginx Proxy
  - AWS EC2
  - Google Domains

## Key Decisions

- Data Structures
  - Main
    - Linked List
    - Arrays
  - Reasoning
    - There are two ways to go about keeping track of the important data, 1). The room and its specific settings, 2). The users in the room. The best way is by using a hashtable to keep track of the users that are suppose to be in the room. Instead of keeping a local copy of all the rooms, I decided to offload that onto a redis cache where we will update the cache when new rooms are created, and when users leave the room. I decided to use a Linked List as the secondary data structure for keeping track of users based on the operation of removing a user from the room (i.e. the list), will be O(1) operations and joining the room would result in an O(1) operation as well.
- WebRTC Architecture
  - Mesh
  - Reasoning
    - I decided to go with Mesh architecture because even though mesh architecture begins running into quality issues at around 5 users, it is the best option for small room sessions, which works best for the current rate of usage of the application.
