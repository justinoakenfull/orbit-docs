---
title: ERD - Design v1
description: Initial ERD Design for ChartDB
published: true
date: 2025-06-28T06:08:48.748Z
tags: 
editor: markdown
dateCreated: 2025-06-28T06:08:48.748Z
---

#ERD
```JSON
{
  "id": "0",
  "name": "Data Model Draft v1",
  "createdAt": "2025-06-28T06:01:18.820Z",
  "updatedAt": "2025-06-28T06:01:18.820Z",
  "databaseType": "generic",
  "tables": [
    {
      "id": "1",
      "name": "List",
      "x": 100,
      "y": 100,
      "fields": [
        {
          "id": "2",
          "name": "id",
          "type": {
            "id": "bigint",
            "name": "bigint"
          },
          "unique": true,
          "nullable": false,
          "primaryKey": true,
          "createdAt": 1751081627358
        },
        {
          "id": "3",
          "name": "Name",
          "type": {
            "id": "text",
            "name": "text"
          },
          "unique": false,
          "nullable": false,
          "primaryKey": false,
          "createdAt": 1751081644831
        },
        {
          "id": "4",
          "name": "Category",
          "type": {
            "id": "text",
            "name": "text"
          },
          "unique": false,
          "nullable": false,
          "primaryKey": false,
          "createdAt": 1751081658493
        },
        {
          "id": "5",
          "name": "Created By",
          "type": {
            "id": "bigint",
            "name": "bigint"
          },
          "unique": false,
          "nullable": false,
          "primaryKey": false,
          "createdAt": 1751081671559
        },
        {
          "id": "6",
          "name": "SharedWith",
          "type": {
            "id": "bigint",
            "name": "bigint"
          },
          "unique": false,
          "nullable": true,
          "primaryKey": false,
          "createdAt": 1751081721413
        },
        {
          "id": "7",
          "name": "IsArchived",
          "type": {
            "id": "boolean",
            "name": "boolean"
          },
          "unique": false,
          "nullable": true,
          "primaryKey": false,
          "createdAt": 1751081852930
        }
      ],
      "indexes": [],
      "color": "#9ef07a",
      "createdAt": 1751081627358,
      "isView": false,
      "order": 2,
      "diagramId": "4dvaswi0cm81"
    },
    {
      "id": "8",
      "name": "Profile Type",
      "x": 100.00000000000001,
      "y": 436.00000000000006,
      "fields": [
        {
          "id": "9",
          "name": "id",
          "type": {
            "id": "bigint",
            "name": "bigint"
          },
          "unique": true,
          "nullable": false,
          "primaryKey": true,
          "createdAt": 1751080221054
        },
        {
          "id": "10",
          "name": "Type",
          "type": {
            "id": "enum",
            "name": "enum"
          },
          "unique": false,
          "nullable": false,
          "primaryKey": false,
          "createdAt": 1751080230979
        },
        {
          "id": "11",
          "name": "Permissions",
          "type": {
            "id": "bigint",
            "name": "bigint"
          },
          "unique": false,
          "nullable": false,
          "primaryKey": false,
          "createdAt": 1751081355649
        }
      ],
      "indexes": [],
      "color": "#8eb7ff",
      "createdAt": 1751080221054,
      "isView": false,
      "order": 1,
      "diagramId": "4dvaswi0cm81"
    },
    {
      "id": "12",
      "name": "Profile",
      "x": -324,
      "y": 100.00000000000006,
      "fields": [
        {
          "id": "13",
          "name": "id",
          "type": {
            "id": "bigint",
            "name": "bigint"
          },
          "unique": true,
          "nullable": false,
          "primaryKey": true,
          "createdAt": 1751080007004
        },
        {
          "id": "14",
          "name": "Profile Type",
          "type": {
            "id": "bigint",
            "name": "bigint"
          },
          "unique": false,
          "nullable": false,
          "primaryKey": false,
          "createdAt": 1751080179160
        },
        {
          "id": "15",
          "name": "Display Name",
          "type": {
            "id": "text",
            "name": "text"
          },
          "unique": false,
          "nullable": false,
          "primaryKey": false,
          "createdAt": 1751080176883
        },
        {
          "id": "16",
          "name": "Colour Code",
          "type": {
            "id": "text",
            "name": "text"
          },
          "unique": false,
          "nullable": false,
          "primaryKey": false,
          "createdAt": 1751080180387
        },
        {
          "id": "17",
          "name": "Avatar",
          "type": {
            "id": "text",
            "name": "text"
          },
          "unique": false,
          "nullable": true,
          "primaryKey": false,
          "createdAt": 1751080180805
        },
        {
          "id": "18",
          "name": "DOB",
          "type": {
            "id": "date",
            "name": "date"
          },
          "unique": false,
          "nullable": false,
          "primaryKey": false,
          "createdAt": 1751080181310
        },
        {
          "id": "19",
          "name": "Stars Earned",
          "type": {
            "id": "bigint",
            "name": "bigint"
          },
          "unique": false,
          "nullable": false,
          "primaryKey": false,
          "createdAt": 1751080181748
        },
        {
          "id": "20",
          "name": "Created At",
          "type": {
            "id": "bigint",
            "name": "bigint"
          },
          "unique": false,
          "nullable": false,
          "primaryKey": false,
          "createdAt": 1751080726681
        },
        {
          "id": "21",
          "name": "Updated At",
          "type": {
            "id": "bigint",
            "name": "bigint"
          },
          "unique": false,
          "nullable": false,
          "primaryKey": false,
          "createdAt": 1751080731666
        },
        {
          "id": "22",
          "name": "Active Account",
          "type": {
            "id": "boolean",
            "name": "boolean"
          },
          "unique": false,
          "nullable": false,
          "primaryKey": false,
          "createdAt": 1751080737334
        }
      ],
      "indexes": [],
      "color": "#ff6363",
      "createdAt": 1751080007004,
      "isView": false,
      "order": 0,
      "diagramId": "4dvaswi0cm81"
    },
    {
      "id": "23",
      "name": "List Item",
      "x": 524,
      "y": 100,
      "fields": [
        {
          "id": "24",
          "name": "id",
          "type": {
            "id": "bigint",
            "name": "bigint"
          },
          "unique": true,
          "nullable": false,
          "primaryKey": true,
          "createdAt": 1751081891796
        },
        {
          "id": "25",
          "name": "Parent List",
          "type": {
            "id": "bigint",
            "name": "bigint"
          },
          "unique": false,
          "nullable": false,
          "primaryKey": false,
          "createdAt": 1751081913781
        },
        {
          "id": "26",
          "name": "Name",
          "type": {
            "id": "bigint",
            "name": "bigint"
          },
          "unique": false,
          "nullable": false,
          "primaryKey": false,
          "createdAt": 1751081946803
        },
        {
          "id": "27",
          "name": "Quantity",
          "type": {
            "id": "bigint",
            "name": "bigint"
          },
          "unique": false,
          "nullable": true,
          "primaryKey": false,
          "createdAt": 1751081954073
        }
      ],
      "indexes": [],
      "color": "#9ef07a",
      "createdAt": 1751081891796,
      "isView": false,
      "order": 3,
      "diagramId": "4dvaswi0cm81"
    }
  ],
  "relationships": [
    {
      "id": "28",
      "name": "List Item_Parent List_fk",
      "sourceTableId": "23",
      "targetTableId": "1",
      "sourceFieldId": "25",
      "targetFieldId": "2",
      "sourceCardinality": "many",
      "targetCardinality": "one",
      "createdAt": 1751081923310,
      "diagramId": "4dvaswi0cm81"
    },
    {
      "id": "29",
      "name": "Profile Type_id_fk",
      "sourceTableId": "8",
      "targetTableId": "12",
      "sourceFieldId": "9",
      "targetFieldId": "14",
      "sourceCardinality": "one",
      "targetCardinality": "one",
      "createdAt": 1751080253168,
      "diagramId": "4dvaswi0cm81"
    },
    {
      "id": "30",
      "name": "Profile_id_fk",
      "sourceTableId": "12",
      "targetTableId": "1",
      "sourceFieldId": "13",
      "targetFieldId": "6",
      "sourceCardinality": "many",
      "targetCardinality": "many",
      "createdAt": 1751081838228,
      "diagramId": "4dvaswi0cm81"
    },
    {
      "id": "31",
      "name": "Profile_id_fk",
      "sourceTableId": "12",
      "targetTableId": "1",
      "sourceFieldId": "13",
      "targetFieldId": "5",
      "sourceCardinality": "one",
      "targetCardinality": "many",
      "createdAt": 1751081686518,
      "diagramId": "4dvaswi0cm81"
    }
  ],
  "dependencies": [],
  "areas": [],
  "customTypes": []
}
```