# Building Blocks

## Entity

An entity is a part of the system with a distinct identity. It is usually mutable and performs business logic.

This identity may be shared between different Subsystems. For example a customer may be defined in the accounting database and the crm database with different attributes, but it is still the same customer.

There has to be a key to identify an entity:
- Best: A single unique domain property like a social security number. It will automatically be unique for all systems
- A combination of properties like Name + Phone Number. Warning: Might not be unique and might change.
- An artificial property like a database generated ID. Warning: Might need to propagate this into other systems.

The entity should be focused on the absolutely necessary parts:
- Drop properties not relevant for the domain
- Extract groupable information into other entities or value objects. E.g. Extract address from customer into value object.


## Value Object

A value object is a part of the system which does not have a distinct identity. Therefore it does not need to have a unique identifier and can be freely shared, copied and exchanged between entities.

It is best to keep value objects immutable especially in shared contexts.

## Service

A service handles logic involving multiple entities where no entity is clearly responsible for the logic, e.g. transfering money between two bank accounts. Services should be stateless so that they can be used by different parts of the system independently.

They can be part of any layer depending on the scope they act on. Transfering Money would be a Domain Service while generating a report of an account as a csv file might be part of the application layer.

## Module

A module groups domain objects based on the principle: High cohesion inside the module, low coupling outside the module. Defining parts of an entity in multiple modules (e.g. based on architecture layers) is very likely a code smell.
