# Microsoft Dataverse

## What is Dataverse?

Microsoft Dataverse is the **default data platform** for Microsoft Power Platform.

Although we usually call it a database, it is actually more than a traditional database.

It is closer to a **Data Platform** than a normal database.

---

## Why?

In a traditional database, my responsibility is usually to create:

- Tables
- Columns
- Relationships
- Records

Then, if I need Security, Business Logic, Validation, or Permissions, I usually implement them separately in the application itself.

---

## Why is Dataverse different?

Dataverse doesn't only store data.

While creating my tables, I can also implement:

- Tables
- Columns
- Relationships
- Business Rules
- Security Roles
- Auditing
- Business Process Flow
- Workflows
- Calculated Columns
- Choice Columns
- APIs

So Dataverse is not only responsible for storing data.

It also provides many business capabilities that help me implement customer requirements without building everything from scratch.

---

## Key Idea

Traditional Database

- Mainly stores data.

Dataverse

- Stores data.
- Manages relationships.
- Supports security.
- Supports business logic.
- Supports automation.
- Supports integrations.

That's why Dataverse is considered a **Data Platform**, not just a database.

---
# On-Premises Data

## What is On-Premises Data?

On-Premises Data is data stored inside the company's **Private Network** or **Local Network**.

Examples:

- SQL Server
- Oracle Database
- File Server
- Any database hosted inside the company.

Unlike Microsoft Dataverse, this data is not stored in Microsoft's Cloud.

---

## The Problem

The company's Private Network is protected by:

- Firewall
- Security Policies
- Network Rules

Because of these security restrictions, external cloud services (such as Power Apps or Power Automate) cannot access the company's database directly.

In other words,

there is **No Direct Access** between the Cloud and the Private Network.

---

## The Solution

To establish a secure connection between the Cloud and the company's Private Network, we need:

- On-Premises Data Gateway

The Gateway acts as a **Secure Bridge** between both environments.

```
Power Apps / Power Automate
            │
            ▼
On-Premises Data Gateway
            │
            ▼
Company Private Network
            │
            ▼
SQL Server
```

The Gateway allows Microsoft services to communicate securely with the company's local data without exposing the database directly to the internet.

---

## Connectors

The Gateway itself does not know how to communicate with every data source.

That's why we also use **Connectors**.

A Connector knows:

- How to connect to a specific system.
- How to send requests.
- How to retrieve data.

Examples:

- SQL Server Connector
- Oracle Connector
- SharePoint Connector

---

## My Understanding

At first, I thought the Gateway stores the data or translates it.

After studying it, I understood that:

- The Gateway only creates a secure communication channel.
- The Connector knows how to communicate with the target system.
- The data always remains inside the company's Private Network unless a request is made through the Gateway.

---
# Types of Dataverse Tables

## Standard Table

Standard Tables are tables already provided by Microsoft when the environment is created.

I can customize these tables, but with some restrictions.

For example, I can:

- Add new columns.
- Create new forms.
- Extend existing forms.
- Create new views.

However, I cannot modify or break Microsoft's built-in business logic.

For example, I can't change how the User table works internally because it's part of the platform.

---

## Custom Table

A Custom Table is a table that I create myself.

Since I own it, I have full customization.

I can:

- Add columns.
- Delete columns.
- Create relationships.
- Modify forms.
- Modify views.

Basically, I have full control over the table.

---

## Virtual Table

I use a Virtual Table when my data already exists in an external data source, such as:

- SQL Server
- External Database
- Other supported systems

Instead of importing all the data into Dataverse, I can use a Virtual Table as a logical representation of that external data.

This helps me:

- Avoid duplicating data.
- Reduce storage inside Dataverse.
- Improve performance when I don't need to store the data locally.

Virtual Tables don't actually store the data inside Dataverse.

They only reference the external data.

---

## Activity Table

Activity Tables are used when I need to track interactions or communication.

Examples include:

- Email
- Phone Call
- Task
- Appointment

Microsoft groups these activities under one Activity model because they all share similar behavior.

---

## My Understanding

At first, I thought every table inside Dataverse was the same.

After studying them, I understood that each table type has a different purpose.

- Standard Tables already exist and can only be extended.
- Custom Tables give me full control.
- Virtual Tables let me work with external data without importing it.
- Activity Tables are specialized for communication and interactions.

---

# Dataverse Schema

## Primary Key

Every Dataverse table has a Primary Key.

The Primary Key is automatically generated by Dataverse.

It is a GUID (Globally Unique Identifier).

Its main purpose is to uniquely identify every row inside the table.

Although it is perfect for identifying records internally, it is not business-friendly.

That's why we usually don't use it during integrations with external systems.

---

## Alternate Key

An Alternate Key is a business-friendly identifier.

Unlike the Primary Key, I define it myself.

It is commonly used during integrations because external systems usually identify records using business information instead of GUIDs.

An Alternate Key can also be Composite.

For example:

- Employee Number
- Department

Together they uniquely identify a record.

---

## Primary Name Column

Primary Name is the human-readable identifier.

It improves the user experience because users see meaningful names instead of GUIDs.

It is mainly used inside Lookups.

---

## Primary Image

A table can contain multiple Image Columns.

However, only one can be configured as the Primary Image.

The Primary Image improves the user experience by making records easier to recognize.

---

## Relationships

Dataverse supports:

- One-to-Many
- Many-to-One
- Many-to-Many
- Self Relationship

For One-to-Many relationships, I can configure different Delete Behaviors.

### Cascade Delete

Deleting the parent automatically deletes all child records.

### Restrict

The parent cannot be deleted while child records still exist.

### Remove Link

The relationship is removed, but the child records remain.

---

## Calculated Column

Calculated Columns evaluate formulas based on other columns.

They are used when the value depends on business calculations.

Example:

Total Price = Quantity × Unit Price

---

## Rollup Column

Rollup Columns perform aggregation across related child records.

Examples:

- Sum
- Average
- Count
- Minimum
- Maximum

Rollup calculations are executed asynchronously through background jobs to reduce performance impact.

When the business requires immediate updates, Power Automate may be a better choice.


