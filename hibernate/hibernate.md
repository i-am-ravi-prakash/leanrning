# Hibernate

- Hibernate is a Java framework that simplifies the deveopment of Java applications to interact with database.
- Hibernate is ORM (Object Relational Mapping) tool.

SessionFactory is an interface factory for providing sessions. SessionFactory is thread safe. At a time, only one session will be created.

Commonly used Hibernate annotations:

- **@Entity**: Used to treat any class as Hibernate entity.
- **@Table**: Used to change table details.
- **@Id**: Used to treat any column as primary key.
- **@GeneratedValue**: Hibernate will automatically generate the value for that column using an internal sequence. Therefore, we don't need to set value manually.
- **@Column**: Used to specify column mapping. For example, to change the column name in the associated table in the database.
- **@Transient**: Used to inform hibernate not to save this field in the database.
- **@Temporal**: @Temporal over a date field is used to format a date in any required date format.
- **@Lob**: It's used to inform hibernate that it's a large object not a simple object.
- **@OneToOne**, **@OneToMany**, **@ManyToOne**, **@JoinColumn**, etc.

There are two ways to fetch data from database using Hibernate:
1. get()
2. load()

Differences between get() and load() methods of Hibernate:

| get() | load() |
| ----- | ------ |
| get() method of Hibernate session returns null if object doesn't exist in cache or in DB. | load() method throws ObjectNotFoundException if object is not found in cache or in DB. |
| Use get() when you are not sure if the required data exist in the DB. | Use load() when you are sure that the required data exist in the DB. |
| get() involves database hit if the object doesn't exist in session cache and returns a fully initialized object which may involve several database call. | load() returns proxy object and only initialize object or hit the database if any method other than getId() is called on persistant or entity object. This is called lazy initializing. |
