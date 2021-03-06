# Implementing noSQL designs in RDBMS

In this article we're designing **postgresql** DB in a **mongodb** way.

Please note: tables have no indexes, for simplicity's sake.

## Basics

Are described here https://www.mongodb.com/blog/post/6-rules-of-thumb-for-mongodb-schema-design-part-1

### One2Few

It is not only easy to implement

```sql
create table person (name varchar, addresses jsonb);
insert into person values ('Kate Monster', '[{ "street": "123 Sesame St", "city": "Anytown", "cc": "USA" }, { "street": "123 Avenue Q", "city": "New York", "cc": "USA" }]');
insert into person values ('Asha Terner', '[{ "street": "123 Avenue Q", "city": "New York", "cc": "USA" }]');
insert into person values ('Jon Gaucho', '[{ "street": "54 Asame St", "city": "Rome", "cc": "Italy" }]');
```

As an added bonus you'll have wide range of comparison operators, e.g. to check tenants

```sql
select name from person where addresses @> '[{ "street": "123 Avenue Q", "city": "New York", "cc": "USA" }]'::jsonb;
     name     
--------------
 Kate Monster
 Asha Terner
(2 rows)
```

### One2Many

Normally you don't want to do this, because this way you can't ensure consistency.

```sql
create table parts (partno uuid, name varchar, qty int, cost float, price float);
insert into parts values ('96b89add-4a03-4963-a145-2a079ab4cf83', '.4 grommet', 94, 0.94, 3.99);
insert into parts values ('d3a7cb2b-ddee-44d5-b439-8343ff9ac5a1', 'h-lever', 34, 1.40, 5.25);

create table products (name varchar, manufacturer varchar, catalog_number int, parts uuid[]);
insert into products values ('left-handed smoke shifter', 'Acme Corp', 1234, '{96b89add-4a03-4963-a145-2a079ab4cf83, d3a7cb2b-ddee-44d5-b439-8343ff9ac5a1}');
```

Getting data out will also became a bit trickier:

```sql
select parts.name from products, parts where partno = any(products.parts);
    name    
------------
 .4 grommet
 h-lever
(2 rows)
```

But it will save you app-level logic and one extra query, because RDBMS doing it for you.

### One2Squillions

This is almost identical to usual RDBMS one-2-many design. Except for foreign keys, of course.

```sql
create table hosts (name varchar, ipaddr inet);
insert into hosts values ('goofy.example.com', '127.66.66.66');

create table logmsg (time timestamp, message varchar, host inet);
insert into logmsg values ('2014-03-28T09:42:41.382Z', 'cpu is on fire!', '127.66.66.66');
```

Getting it back:

```sql
select message from logmsg, hosts where ipaddr = host;
     message     
-----------------
 cpu is on fire!
(1 row)
```

Think about it:
- if the design considered normal within RDBMS, in **mongodb** works only in case of HUGE collection, what does it says about both? (universality)
- if **mongodb** embedding made to get you all the requested data in one query, but RDBMS allows you to get in one query data collected from any number of tables? (usability)
- how it is helping that second design in **mongodb** is not only limited to 131072 references, but this references also shared space with document? (scalability)
