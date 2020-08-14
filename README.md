## Description

Node REST API used as Proffy backend. The user can either list or create a new class, or list or create a new connection.

## Setup

To start the server just run:

```
  yarn install
  yarn start
```

## Routes

### List Classes

List all available classes and teachers according to subject, day of week and schedule filters.

```
URL: /classes
Method: GET
Params: { 
          week_day: 1, 
          subject: "Matemática", 
          time: "9:00"
        }
Body: {}

Status: 200
Response: [
            {
              "id": 1,
              "subject": "Matemática",
              "cost": 80,
              "user_id": 1,
              "name": "André Corrêa",
              "avatar": "https://avatars3.githubusercontent.com/u/27099418?s=460&u=9e9d60aaaa0442fe7490f625c9dbbe97ed1d3480&v=4",
              "whatsapp": "11999999999",
              "bio": "Entusiasta de tecnologia e data science, com grande sonho de ser um empreendedor de sucesso!"
            }
          ]

```

### Create Class

Create new class based on teacher, subject and available schedule.

```
URL: /classes
Method: POST
Params: {}
Body: {
        "name": "André Corrêa",
        "avatar": "https://avatars3.githubusercontent.com/u/27099418?s=460&u=9e9d60aaaa0442fe7490f625c9dbbe97ed1d3480&v=4",
        "whatsapp": "11999999999",
        "bio": "Entusiasta de tecnologia e data science, com grande sonho de ser um empreendedor de sucesso!",
        "subject": "Matemática",
        "cost": 80,
        "schedule": [
          {"week_day": 1,"from": "8:00","to": "12:00"},
          {"week_day": 3,"from": "10:00","to": "18:00"},
          {"week_day": 4,"from": "8:00","to": "12:00"}
        ]
      }

Status: 201
Response: {}

```

### List Connections

Get total amount of connections between teachers and students.

```
URL: /connections
Method: GET
Params: {}
Body: {}

Status: 200
Response: {
            "total": 4
          }

```

### Create Connection

Create new connection and add to total connections.

```
URL: /connections
Method: POST
Params: {}
Body: {
        "user_id": 1
      }

Status: 201
Response: {}

```