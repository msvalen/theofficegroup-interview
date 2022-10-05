# tog-fs-interview-task

## Tecnologies 
- node
- express
- MongoDB or another noSQL db. I would use a NoSQL like mongo or dynamo because of the preference of a embeded data model for the definitions of our Events.
- jsonwebtoken (Our security will be based on  tockens)
- bcrypt (To hash the password of the users)
- cypress 

## Endpoints

### Auth
| URL | Type | Description | Situatuion |
| --- | ----- | ------------- | ----- |
| /register | POST | create a new User | public route |
| /login | POST | sign in a User   | public route |
| /send-mail-verification/:id | POST | send verification email to user | public route |
| /email-verified/:id | PATCH | save email as confirmed |
| /forgot-password/:id | POST | send recovery email to User | public route |
| /new-password/:id | PATCH | save new password of User | public route |
| /delete/:id | DELETE | delete a User | private route |

### Events 

| URL | Type | Description | Situatuion |
| --- | ----- | ------------- | ----- |
| /events | POST | create a new Event | private route |
| /events | GET | show a list of Events | private route |
| /events/:id | GET | show a particular Event | private route |

## Database schema

#### Events
| Name | Type | Notes |
| ---- | ---- | ------ |
| id | serial | primary key |
| creation_date | timestamp | default = now |
| name | varchar(100) | not null |
| time.start | timestamp | not null |
| time.end | timestamp | null |
| description | varchar(500) | not null |
| venue.name | varchar(100) | not null |
| venue.address | varchar(100) | not null |
| image.src |  varchar(100) | null |
| image.alt | varchar(100) | null

* Please note. This event is based of what I remember of facebook events where, so there are certain fields that are mandatory and certain that arent. Mandatory: Name, Description, start time, venue.

#### Users
| Name | Type | Notes |
| ---- | ---- | ------ |
| id | serial | primary key |
| creation_date | timestamp | default = now |
| name | varchar(100) | not null |
| email | varchar(100) | not null | 
| password | varchar(100) | not null (hashed) |
| verified | BOOL | default = false |

## Design notes
- The show list event controller should add a link to the id so it add it redirect to the particullar event
- I would implement in Github action a pipeline who would do automatic testing and deployment when the conditions are meet
- The version control will be done by Github