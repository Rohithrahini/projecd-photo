---
title: 'Chapter 1 Introduction'
weight: 5
---

  

# Introduction

A **database-management system (DBMS)** is a collection of interrelated data and a set of programs to access those data. The collection of data, usually referred to as the **database**, contains information relevant to an enterprise. The primary goal of a DBMS is to provide a way to store and retrieve database information that is both _convenient_ and _efficient._

Database systems are designed to manage large bodies of information. Man- agement of data involves both defining structures for storage of information and providing mechanisms for the manipulation of information. In addition, the database system must ensure the safety of the information stored, despite system crashes or attempts at unauthorized access. If data are to be shared among several users, the system must avoid possible anomalous results.

Because information is so important in most organizations, computer scien- tists have developed a large body of concepts and techniques for managing data. These concepts and techniques form the focus of this book. This chapter briefly introduces the principles of database systems.

# 1.1 Database-System Applications

Databases are widely used. Here are some representative applications:

•Enterprise Information_

◦ _Sales_: For customer, product, and purchase information.

◦ _Accounting_: For payments, receipts, account balances, assets and other accounting information.

◦ _Human resources_: For information about employees, salaries, payroll taxes, and benefits, and for generation of paychecks.

◦ _Manufacturing_: For management of the supply chain and for tracking pro- duction of items in factories, inventories of items in warehouses and stores, and orders for items.

  2   **Chapter 1**  Introduction

◦ _Online retailers_: For sales data noted above plus online order tracking, generation of recommendation lists, and maintenance of online product evaluations.

• _Banking and Finance_

◦ _Banking_: For customer information, accounts, loans, and banking transac- tions.

◦ _Credit card transactions_: For purchases on credit cards and generation of monthly statements.

◦ _Finance_: For storing information about holdings, sales, and purchases of financial instruments such as stocks and bonds; also for storing real-time market data to enable online trading by customers and automated trading by the firm.

• _Universities_: For student information, course registrations, and grades (in addition to standard enterprise information such as human resources and accounting).

• _Airlines_: For reservations and schedule information. Airlines were among the first to use databases in a geographically distributed manner.

• _Telecommunication_: For keeping records of calls made, generating monthly bills, maintaining balances on prepaid calling cards, and storing information about the communication networks.

As the list illustrates, databases form an essential part of every enterprise today, storing not only types of information that are common to most enterprises, but also information that is specific to the category of the enterprise.

Over the course of the last four decades of the twentieth century, use of databases grew in all enterprises. In the early days, very few people interacted di- rectly with database systems, although without realizing it, they interacted with databases indirectly—through printed reports such as credit card statements, or through agents such as bank tellers and airline reservation agents. Then auto- mated teller machines came along and let users interact directly with databases. Phone interfaces to computers (interactive voice-response systems) also allowed users to deal directly with databases—a caller could dial a number, and press phone keys to enter information or to select alternative options, to find flight  arrival/departure times, for example, or to register for courses in a university.

The Internet revolution of the late 1990s sharply increased direct user access to databases. Organizations converted many of their phone interfaces to databases into Web interfaces, and made a variety of services and information available online. For instance, when you access an online bookstore and browse a book or music collection, you are accessing data stored in a database. When you enter an order online, your order is stored in a database. When you access a bank Web site and retrieve your bank balance and transaction information, the information is retrieved from the bank’s database system. When you access a Web site, informa-  

**1.2 Purpose of Database Systems**

tion about you may be retrieved from a database to select which advertisements you should see. Furthermore, data about your Web accesses may be stored in a database.

Thus, although user interfaces hide details of access to a database, and most people are not even aware they are dealing with a database, accessing databases forms an essential part of almost everyone’s life today.

The importance of database systems can be judged in another way—today, database system vendors like Oracle are among the largest software companies in the world, and database systems form an important part of the product line of Microsoft and IBM.

**1.2 Purpose of Database Systems**

Database systems arose in response to early methods of computerized manage- ment of commercial data. As an example of such methods, typical of the 1960s, consider part of a university organization that, among other data, keeps infor- mation about all instructors, students, departments, and course offerings. One way to keep the information on a computer is to store it in operating system files. To allow users to manipulate the information, the system has a number of application programs that manipulate the files, including programs to:

• Add new students, instructors, and courses

• Register students for courses and generate class rosters

• Assign grades to students, compute grade point averages (GPA), and generate transcripts

System programmers wrote these application programs to meet the needs of the university.

New application programs are added to the system as the need arises. For example, suppose that a university decides to create a new major (say, computer science). As a result, the university creates a new department and creates new per- manent files (or adds information to existing files) to record information about all the instructors in the department, students in that major, course offerings, degree requirements, etc. The university may have to write new application programs to deal with rules specific to the new major. New application programs may also have to be written to handle new rules in the university. Thus, as time goes by, the system acquires more files and more application programs.

This typical **file-processing system** is supported by a conventional operat- ing system. The system stores permanent records in various files, and it needs different application programs to extract records from, and add records to, the ap- propriate files. Before database management systems (DBMSs) were introduced, organizations usually stored information in such systems.

Keeping organizational information in a file-processing system has a number of major disadvantages:  

**4 Chapter 1 Introduction**

• **Data redundancy and inconsistency**. Since different programmers create the files and application programs over a long period, the various files are likely to have different structures and the programs may be written in several programming languages. Moreover, the same information may be duplicated in several places (files). For example, if a student has a double major (say, music and mathematics) the address and telephone number of that student may appear in a file that consists of student records of students in the Music department and in a file that consists of student records of students in the Mathematics department. This redundancy leads to higher storage and access cost. In addition, it may lead to **data inconsistency**; that is, the various copies of the same data may no longer agree. For example, a changed student address may be reflected in the Music department records but not elsewhere in the system.

• **Difficulty in accessing data**. Suppose that one of the university clerks needs to find out the names of all students who live within a particular postal-code area. The clerk asks the data-processing department to generate such a list. Because the designers of the original system did not anticipate this request, there is no application program on hand to meet it. There is, however, an application program to generate the list of _all_ students. The university clerk has now two choices: either obtain the list of all students and extract the needed information manually or ask a programmer to write the necessary application program. Both alternatives are obviously unsatisfactory. Suppose that such a program is written, and that, several days later, the same clerk needs to trim that list to include only those students who have taken at least 60 credit hours. As expected, a program to generate such a list does not exist. Again, the clerk has the preceding two options, neither of which is satisfactory.

The point here is that conventional file-processing environments do not allow needed data to be retrieved in a convenient and efficient manner. More responsive data-retrieval systems are required for general use.

• **Data isolation**. Because data are scattered in various files, and files may be in different formats, writing new application programs to retrieve the appropriate data is difficult.

• **Integrity problems**. The data values stored in the database must satisfy cer- tain types of **consistency constraints**. Suppose the university maintains an account for each department, and records the balance amount in each ac- count. Suppose also that the university requires that the account balance of a department may never fall below zero. Developers enforce these constraints in the system by adding appropriate code in the various application pro- grams. However, when new constraints are added, it is difficult to change the programs to enforce them. The problem is compounded when constraints involve several data items from different files.

• **Atomicity problems**. A computer system, like any other device, is subject to failure. In many applications, it is crucial that, if a failure occurs, the data  

**1.2 Purpose of Database Systems 5**

be restored to the consistent state that existed prior to the failure. Consider a program to transfer $500 from the account balance of department _A_ to the account balance of department _B_. If a system failure occurs during the execution of the program, it is possible that the $500 was removed from the balance of department _A_ but was not credited to the balance of department _B_, resulting in an inconsistent database state. Clearly, it is essential to database consistency that either both the credit and debit occur, or that neither occur. That is, the funds transfer must be _atomic_—it must happen in its entirety or not at all. It is difficult to ensure atomicity in a conventional file-processing system.

• **Concurrent-access anomalies**. For the sake of overall performance of the sys- tem and faster response, many systems allow multiple users to update the data simultaneously. Indeed, today, the largest Internet retailers may have millions of accesses per day to their data by shoppers. In such an environ- ment, interaction of concurrent updates is possible and may result in incon- sistent data. Consider department _A_, with an account balance of $10,000. If two department clerks debit the account balance (by say $500 and $100, re- spectively) of department _A_ at almost exactly the same time, the result of the concurrent executions may leave the budget in an incorrect (or inconsistent) state. Suppose that the programs executing on behalf of each withdrawal read the old balance, reduce that value by the amount being withdrawn, and write the result back. If the two programs run concurrently, they may both read the value $10,000, and write back $9500 and $9900, respectively. Depending on which one writes the value last, the account balance of department _A_ may contain either $9500 or $9900, rather than the correct value of $9400. To guard against this possibility, the system must maintain some form of supervision. But supervision is difficult to provide because data may be accessed by many different application programs that have not been coordinated previously.

As another example, suppose a registration program maintains a count of students registered for a course, in order to enforce limits on the number of students registered. When a student registers, the program reads the current count for the courses, verifies that the count is not already at the limit, adds one to the count, and stores the count back in the database. Suppose two students register concurrently, with the count at (say) 39. The two program executions may both read the value 39, and both would then write back 40, leading to an incorrect increase of only 1, even though two students suc- cessfully registered for the course and the count should be 41. Furthermore, suppose the course registration limit was 40; in the above case both students would be able to register, leading to a violation of the limit of 40 students.

• **Security problems**. Not every user of the database system should be able to access all the data. For example, in a university, payroll personnel need to see only that part of the database that has financial information. They do not need access to information about academic records. But, since applica- tion programs are added to the file-processing system in an ad hoc manner, enforcing such security constraints is difficult.  

**6 Chapter 1 Introduction**

These difficulties, among others, prompted the development of database sys- tems. In what follows, we shall see the concepts and algorithms that enable database systems to solve the problems with file-processing systems. In most of this book, we use a university organization as a running example of a typical data-processing application.

# 1.3 View of Data

A database system is a collection of interrelated data and a set of programs that allow users to access and modify these data. A major purpose of a database system is to provide users with an _abstract_ view of the data. That is, the system hides certain details of how the data are stored and maintained.

## 1.3.1 Data Abstraction

For the system to be usable, it must retrieve data efficiently. The need for efficiency has led designers to use complex data structures to represent data in the database. Since many database-system users are not computer trained, developers hide the complexity from users through several levels of abstraction, to simplify users’ interactions with the system:

• **Physical level**. The lowest level of abstraction describes _how_ the data are ac- tually stored. The physical level describes complex low-level data structures in detail.

• **Logical level**. The next-higher level of abstraction describes _what_ data are stored in the database, and what relationships exist among those data. The logical level thus describes the entire database in terms of a small number of relatively simple structures. Although implementation of the simple struc- tures at the logical level may involve complex physical-level structures, the user of the logical level does not need to be aware of this complexity. This is referred to as **physical data independence**. Database administrators, who must decide what information to keep in the database, use the logical level of abstraction.

• **View level**. The highest level of abstraction describes only part of the entire database. Even though the logical level uses simpler structures, complexity remains because of the variety of information stored in a large database. Many users of the database system do not need all this information; instead, they need to access only a part of the database. The view level of abstraction exists to simplify their interaction with the system. The system may provide many views for the same database.

Figure 1.1 shows the relationship among the three levels of abstraction. An analogy to the concept of data types in programming languages may

clarify the distinction among levels of abstraction. Many high-level programming  

**1.3 View of Data 7**

view 1 view 2

logical level

physical level

view _n_…

view level

![Alt  The three levels of data abstraction.](three.png)

**Figure 1.1** The three levels of data abstraction.

languages support the notion of a structured type. For example, we may describe a record as follows:1

**type** _instructor_ \= **record** _ID_ : **char** (5); _name_ : **char** (20); _dept name_ : **char** (20); _salary_ : **numeric** (8,2);

**end**;

This code defines a new record type called _instructor_ with four fields. Each field has a name and a type associated with it. A university organization may have several such record types, including

• _department_, with fields _dept name_, _building_, and _budget_

• _course_, with fields _course id_, _title_, _dept name_, and _credits_

• _student_, with fields _ID_, _name_, _dept name_, and _tot cred_

At the physical level, an _instructor_, _department_, or _student_ record can be de- scribed as a block of consecutive storage locations. The compiler hides this level of detail from programmers. Similarly, the database system hides many of the lowest-level storage details from database programmers. Database administra- tors, on the other hand, may be aware of certain details of the physical organiza- tion of the data.

1The actual type declaration depends on the language being used. C and C++ use **struct** declarations. Java does not have such a declaration, but a simple class can be defined to the same effect.  

**8 Chapter 1 Introduction**

At the logical level, each such record is described by a type definition, as in the previous code segment, and the interrelationship of these record types is defined as well. Programmers using a programming language work at this level of abstraction. Similarly, database administrators usually work at this level of abstraction.

Finally, at the view level, computer users see a set of application programs that hide details of the data types. At the view level, several views of the database are defined, and a database user sees some or all of these views. In addition to hiding details of the logical level of the database, the views also provide a security mechanism to prevent users from accessing certain parts of the database. For example, clerks in the university registrar office can see only that part of the database that has information about students; they cannot access information about salaries of instructors.

## 1.3.2 Instances and Schemas**

Databases change over time as information is inserted and deleted. The collection of information stored in the database at a particular moment is called an **instance** of the database. The overall design of the database is called the database **schema**. Schemas are changed infrequently, if at all.

The concept of database schemas and instances can be understood by analogy to a program written in a programming language. A database schema corresponds to the variable declarations (along with associated type definitions) in a program. Each variable has a particular value at a given instant. The values of the variables in a program at a point in time correspond to an _instance_ of a database schema.

Database systems have several schemas, partitioned according to the levels of abstraction. The **physical schema** describes the database design at the physical level, while the **logical schema** describes the database design at the logical level. A database may also have several schemas at the view level, sometimes called **subschemas**, that describe different views of the database.

Of these, the logical schema is by far the most important, in terms of its effect on application programs, since programmers construct applications by using the logical schema. The physical schema is hidden beneath the logical schema, and can usually be changed easily without affecting application programs. Application programs are said to exhibit **physical data independence** if they do not depend on the physical schema, and thus need not be rewritten if the physical schema changes.

We study languages for describing schemas after introducing the notion of data models in the next section.

**1.3.3 Data Models**

Underlying the structure of a database is the **data model**: a collection of conceptual tools for describing data, data relationships, data semantics, and consistency constraints. A data model provides a way to describe the design of a database at the physical, logical, and view levels.  

**1.4 Database Languages 9**

There are a number of different data models that we shall cover in the text. The data models can be classified into four different categories:

• **Relational Model**. The relational model uses a collection of tables to repre- sent both data and the relationships among those data. Each table has mul- tiple columns, and each column has a unique name. Tables are also known as **relations**. The relational model is an example of a record-based model. Record-based models are so named because the database is structured in fixed-format records of several types. Each table contains records of a par- ticular type. Each record type defines a fixed number of fields, or attributes. The columns of the table correspond to the attributes of the record type. The relational data model is the most widely used data model, and a vast major- ity of current database systems are based on the relational model. Chapters 2 through 8 cover the relational model in detail.

• **Entity-Relationship Model**. The entity-relationship (E-R) data model uses a collection of basic objects, called _entities_, and _relationships_ among these objects. An entity is a “thing” or “object” in the real world that is distinguishable from other objects. The entity-relationship model is widely used in database design, and Chapter 7 explores it in detail.

• **Object-Based Data Model**. Object-oriented programming (especially in Java, C++, or C#) has become the dominant software-development methodology. This led to the development of an object-oriented data model that can be seen as extending the E-R model with notions of encapsulation, methods (functions), and object identity. The object-relational data model combines features of the object-oriented data model and relational data model. Chap- ter 22 examines the object-relational data model.

• **Semistructured Data Model**. The semistructured data model permits the specification of data where individual data items of the same type may have different sets of attributes. This is in contrast to the data models mentioned earlier, where every data item of a particular type must have the same set of attributes. The **Extensible Markup Language (XML)** is widely used to represent semistructured data. Chapter 23 covers it.

Historically, the **network data model** and the **hierarchical data model** pre- ceded the relational data model. These models were tied closely to the underlying implementation, and complicated the task of modeling data. As a result they are used little now, except in old database code that is still in service in some places. They are outlined online in Appendices D and E for interested readers.

**1.4 Database Languages**

A database system provides a **data-definition language** to specify the database schema and a **data-manipulation language** to express database queries and up-  

**10 Chapter 1 Introduction**

dates. In practice, the data-definition and data-manipulation languages are not two separate languages; instead they simply form parts of a single database lan- guage, such as the widely used SQL language.

**1.4.1 Data-Manipulation Language**

A **data-manipulation language (DML)** is a language that enables users to access or manipulate data as organized by the appropriate data model. The types of access are:

• Retrieval of information stored in the database

• Insertion of new information into the database

• Deletion of information from the database

• Modification of information stored in the database

There are basically two types:

• **Procedural DMLs** require a user to specify _what_ data are needed and _how_ to get those data.

• **Declarative DMLs** (also referred to as **nonprocedural DMLs**) require a user to specify _what_ data are needed _without_ specifying how to get those data.

Declarative DMLs are usually easier to learn and use than are procedural DMLs. However, since a user does not have to specify how to get the data, the database system has to figure out an efficient means of accessing data.

A **query** is a statement requesting the retrieval of information. The portion of a DML that involves information retrieval is called a **query language**. Although technically incorrect, it is common practice to use the terms _query language_ and _data-manipulation language_ synonymously.

There are a number of database query languages in use, either commercially or experimentally. We study the most widely used query language, SQL, in Chap- ters 3, 4, and 5. We also study some other query languages in Chapter 6.

The levels of abstraction that we discussed in Section 1.3 apply not only to defining or structuring data, but also to manipulating data. At the physical level, we must define algorithms that allow efficient access to data. At higher levels of abstraction, we emphasize ease of use. The goal is to allow humans to interact efficiently with the system. The query processor component of the database system (which we study in Chapters 12 and 13) translates DML queries into sequences of actions at the physical level of the database system.

**1.4.2 Data-Definition Language**

We specify a database schema by a set of definitions expressed by a special language called a **data-definition language** (**DDL**). The DDL is also used to specify additional properties of the data.  

**1.4 Database Languages 11**

We specify the storage structure and access methods used by the database system by a set of statements in a special type of DDL called a **data storage and definition** language. These statements define the implementation details of the database schemas, which are usually hidden from the users.

The data values stored in the database must satisfy certain **consistency con- straints**. For example, suppose the university requires that the account balance of a department must never be negative. The DDL provides facilities to specify such constraints. The database system checks these constraints every time the database is updated. In general, a constraint can be an arbitrary predicate per- taining to the database. However, arbitrary predicates may be costly to test. Thus, database systems implement integrity constraints that can be tested with minimal overhead:

• **Domain Constraints**. A domain of possible values must be associated with every attribute (for example, integer types, character types, date/time types). Declaring an attribute to be of a particular domain acts as a constraint on the values that it can take. Domain constraints are the most elementary form of integrity constraint. They are tested easily by the system whenever a new data item is entered into the database.

• **Referential Integrity**. There are cases where we wish to ensure that a value that appears in one relation for a given set of attributes also appears in a cer- tain set of attributes in another relation (referential integrity). For example, the department listed for each course must be one that actually exists. More precisely, the _dept name_ value in a _course_ record must appear in the _dept name_ attribute of some record of the _department_ relation. Database modifications can cause violations of referential integrity. When a referential-integrity con- straint is violated, the normal procedure is to reject the action that caused the violation.

• **Assertions**. An assertion is any condition that the database must always satisfy. Domain constraints and referential-integrity constraints are special forms of assertions. However, there are many constraints that we cannot express by using only these special forms. For example, “Every department must have at least five courses offered every semester” must be expressed as an assertion. When an assertion is created, the system tests it for validity. If the assertion is valid, then any future modification to the database is allowed only if it does not cause that assertion to be violated.

• **Authorization**. We may want to differentiate among the users as far as the type of access they are permitted on various data values in the database. These differentiations are expressed in terms of **authorization**, the most common being: **read authorization**, which allows reading, but not modification, of data; **insert authorization**, which allows insertion of new data, but not mod- ification of existing data; **update authorization**, which allows modification, but not deletion, of data; and **delete authorization**, which allows deletion of data. We may assign the user all, none, or a combination of these types of authorization.  

**12 Chapter 1 Introduction**

The DDL, just like any other programming language, gets as input some instructions (statements) and generates some output. The output of the DDL is placed in the **data dictionary**, which contains **metadata**—that is, data about data. The data dictionary is considered to be a special type of table that can only be accessed and updated by the database system itself (not a regular user). The database system consults the data dictionary before reading or modifying actual data.

**1.5 Relational Databases**

A relational database is based on the relational model and uses a collection of tables to represent both data and the relationships among those data. It also in- cludes a DML and DDL. In Chapter 2 we present a gentle introduction to the fundamentals of the relational model. Most commercial relational database sys- tems employ the SQL language, which we cover in great detail in Chapters 3, 4, and 5. In Chapter 6 we discuss other influential languages.

**1.5.1 Tables**

Each table has multiple columns and each column has a unique name. Figure 1.2 presents a sample relational database comprising two tables: one shows details of university instructors and the other shows details of the various university departments.

The first table, the _instructor_ table, shows, for example, that an instructor named Einstein with _ID_ 22222 is a member of the Physics department and has an annual salary of $95,000. The second table, _department_, shows, for example, that the Biology department is located in the Watson building and has a budget of $90,000. Of course, a real-world university would have many more departments and instructors. We use small tables in the text to illustrate concepts. A larger example for the same schema is available online.

The relational model is an example of a record-based model. Record-based models are so named because the database is structured in fixed-format records of several types. Each table contains records of a particular type. Each record type defines a fixed number of fields, or attributes. The columns of the table correspond to the attributes of the record type.

It is not hard to see how tables may be stored in files. For instance, a special character (such as a comma) may be used to delimit the different attributes of a record, and another special character (such as a new-line character) may be used to delimit records. The relational model hides such low-level implementation details from database developers and users.

We also note that it is possible to create schemas in the relational model that have problems such as unnecessarily duplicated information. For example, sup- pose we store the department _budget_ as an attribute of the _instructor_ record. Then, whenever the value of a particular budget (say that one for the Physics depart- ment) changes, that change must to be reflected in the records of all instructors  

**1.5 Relational Databases 13**

_ID name dept name salary_

22222 Einstein Physics 95000 12121 Wu Finance 90000 32343 El Said History 60000 45565 Katz Comp. Sci. 75000 98345 Kim Elec. Eng. 80000 76766 Crick Biology 72000 10101 Srinivasan Comp. Sci. 65000 58583 Califieri History 62000 83821 Brandt Comp. Sci. 92000 15151 Mozart Music 40000 33456 Gold Physics 87000 76543 Singh Finance 80000

(a) The _instructor_ table

_dept name building budget_

Comp. Sci. Taylor 100000 Biology Watson 90000 Elec. Eng. Taylor 85000 Music Packard 80000 Finance Painter 120000 History Painter 50000 Physics Watson 70000

(b) The _department_ table
![alt A sample relational database](sample.png)
**Figure 1.2** A sample relational database.

associated with the Physics department. In Chapter 8, we shall study how to distinguish good schema designs from bad schema designs.

**1.5.2 Data-Manipulation Language**

The SQL query language is nonprocedural. A query takes as input several tables (possibly only one) and always returns a single table. Here is an example of an SQL query that finds the names of all instructors in the History department:

**select** _instructor_._name_ **from** _instructor_ **where** _instructor_._dept name_ \= ’History’;

The query specifies that those rows from the table _instructor_ where the _dept name_ is History must be retrieved, and the _name_ attribute of these rows must be displayed. More specifically, the result of executing this query is a table with a single column  

**14 Chapter 1 Introduction**

labeled _name_, and a set of rows, each of which contains the name of an instructor whose _dept name_, is History. If the query is run on the table in Figure 1.2, the result will consist of two rows, one with the name El Said and the other with the name Califieri.

Queries may involve information from more than one table. For instance, the following query finds the instructor ID and department name of all instructors associated with a department with budget of greater than $95,000.

**select** _instructor_._ID_, _department_._dept name_ **from** _instructor_, _department_ **where** _instructor_._dept name_\= _department_._dept name_ **and**

_department_._budget >_ 95000;

If the above query were run on the tables in Figure 1.2, the system would find that there are two departments with budget of greater than $95,000—Computer Science and Finance; there are five instructors in these departments. Thus, the result will consist of a table with two columns (_ID_, _dept name_) and five rows: (12121, Finance), (45565, Computer Science), (10101, Computer Science), (83821, Computer Science), and (76543, Finance).

**1.5.3 Data-Definition Language**

SQL provides a rich DDL that allows one to define tables, integrity constraints, assertions, etc.

For instance, the following SQL DDL statement defines the _department_ table:

**create table** _department_ (_dept name_ **char** (20), _building_ **char** (15), _budget_ **numeric** (12,2));

Execution of the above DDL statement creates the _department_ table with three columns: _dept name_, _building_, and _budget_, each of which has a specific data type associated with it. We discuss data types in more detail in Chapter 3. In addition, the DDL statement updates the data dictionary, which contains metadata (see Section 1.4.2). The schema of a table is an example of metadata.

**1.5.4 Database Access from Application Programs**

SQL is not as powerful as a universal Turing machine; that is, there are some computations that are possible using a general-purpose programming language but are not possible using SQL. SQL also does not support actions such as input from users, output to displays, or communication over the network. Such com- putations and actions must be written in a _host_ language, such as C, C++, or Java, with embedded SQL queries that access the data in the database. **Application programs** are programs that are used to interact with the database in this fashion.  

**1.6 Database Design 15**

Examples in a university system are programs that allow students to register for courses, generate class rosters, calculate student GPA, generate payroll checks, etc.

To access the database, DML statements need to be executed from the host language. There are two ways to do this:

• By providing an application program interface (set of procedures) that can be used to send DML and DDL statements to the database and retrieve the results.

The Open Database Connectivity (ODBC) standard for use with the C language is a commonly used application program interface standard. The Java Database Connectivity (JDBC) standard provides corresponding features to the Java language.

• By extending the host language syntax to embed DML calls within the host language program. Usually, a special character prefaces DML calls, and a preprocessor, called the **DML precompiler**, converts the DML statements to normal procedure calls in the host language.

**1.6 Database Design**

Database systems are designed to manage large bodies of information. These large bodies of information do not exist in isolation. They are part of the operation of some enterprise whose end product may be information from the database or may be some device or service for which the database plays only a supporting role.

Database design mainly involves the design of the database schema. The design of a complete database application environment that meets the needs of the enterprise being modeled requires attention to a broader set of issues. In this text, we focus initially on the writing of database queries and the design of database schemas. Chapter 9 discusses the overall process of application design.

**1.6.1 Design Process**

A high-level data model provides the database designer with a conceptual frame- work in which to specify the data requirements of the database users, and how the database will be structured to fulfill these requirements. The initial phase of database design, then, is to characterize fully the data needs of the prospective database users. The database designer needs to interact extensively with domain experts and users to carry out this task. The outcome of this phase is a specification of user requirements.

Next, the designer chooses a data model, and by applying the concepts of the chosen data model, translates these requirements into a conceptual schema of the database. The schema developed at this **conceptual-design** phase provides a detailed overview of the enterprise. The designer reviews the schema to confirm that all data requirements are indeed satisfied and are not in conflict with one another. The designer can also examine the design to remove any redundant  

**16 Chapter 1 Introduction**

features. The focus at this point is on describing the data and their relationships, rather than on specifying physical storage details.

In terms of the relational model, the conceptual-design process involves de- cisions on _what_ attributes we want to capture in the database and _how to group_ these attributes to form the various tables. The “what” part is basically a business decision, and we shall not discuss it further in this text. The “how” part is mainly a computer-science problem. There are principally two ways to tackle the problem. The first one is to use the entity-relationship model (Section 1.6.3); the other is to employ a set of algorithms (collectively known as _normalization_) that takes as input the set of all attributes and generates a set of tables (Section 1.6.4).

A fully developed conceptual schema indicates the functional requirements of the enterprise. In a **specification of functional requirements**, users describe the kinds of operations (or transactions) that will be performed on the data. Example operations include modifying or updating data, searching for and retrieving specific data, and deleting data. At this stage of conceptual design, the designer can review the schema to ensure it meets functional requirements.

The process of moving from an abstract data model to the implementation of the database proceeds in two final design phases. In the **logical-design phase**, the designer maps the high-level conceptual schema onto the implementation data model of the database system that will be used. The designer uses the resulting system-specific database schema in the subsequent **physical-design phase**, in which the physical features of the database are specified. These features include the form of file organization and the internal storage structures; they are discussed in Chapter 10.

**1.6.2 Database Design for a University Organization**

To illustrate the design process, let us examine how a database for a university could be designed. The initial specification of user requirements may be based on interviews with the database users, and on the designer’s own analysis of the organization. The description that arises from this design phase serves as the basis for specifying the conceptual structure of the database. Here are the major characteristics of the university.

• The university is organized into departments. Each department is identified by a unique name (_dept name_), is located in a particular _building_, and has a _budget_.

• Each department has a list of courses it offers. Each course has associated with it a _course id_, _title_, _dept name_, and _credits_, and may also have have associated _prerequisites_.

• Instructors are identified by their unique _ID_. Each instructor has _name_, asso- ciated department (_dept name_), and _salary_.

• Students are identified by their unique _ID_. Each student has a _name_, an associ- ated major department (_dept name_), and _tot cred_ (total credit hours the student earned thus far).  

**1.6 Database Design 17**

• The university maintains a list of classrooms, specifying the name of the _building_, _room number_, and room _capacity_.

• The university maintains a list of all classes (sections) taught. Each section is identified by a _course id_, _sec id_, _year_, and _semester_, and has associated with it a _semester_, _year_, _building_, _room number_, and _time slot id_ (the time slot when the class meets).

• The department has a list of teaching assignments specifying, for each in- structor, the sections the instructor is teaching.

• The university has a list of all student course registrations, specifying, for each student, the courses and the associated sections that the student has taken (registered for).

A real university database would be much more complex than the preceding design. However we use this simplified model to help you understand conceptual ideas without getting lost in details of a complex design.

**1.6.3 The Entity-Relationship Model**

The entity-relationship (E-R) data model uses a collection of basic objects, called _entities_, and _relationships_ among these objects. An entity is a “thing” or “object” in the real world that is distinguishable from other objects. For example, each person is an entity, and bank accounts can be considered as entities.

Entities are described in a database by a set of **attributes**. For example, the attributes _dept name_, _building_, and _budget_ may describe one particular department in a university, and they form attributes of the _department_ entity set. Similarly, attributes _ID_, _name_, and _salary_ may describe an _instructor_ entity.2

The extra attribute _ID_ is used to identify an instructor uniquely (since it may be possible to have two instructors with the same name and the same salary). A unique instructor identifier must be assigned to each instructor. In the United States, many organizations use the social-security number of a person (a unique number the U.S. government assigns to every person in the United States) as a unique identifier.

A **relationship** is an association among several entities. For example, a _member_ relationship associates an instructor with her department. The set of all entities of the same type and the set of all relationships of the same type are termed an **entity set** and **relationship set**, respectively.

The overall logical structure (schema) of a database can be expressed graph- ically by an _entity-relationship (E-R) diagram_. There are several ways in which to draw these diagrams. One of the most popular is to use the **Unified Modeling Language (UML)**. In the notation we use, which is based on UML, an E-R diagram is represented as follows:

2The astute reader will notice that we dropped the attribute _dept name_ from the set of attributes describing the _instructor_ entity set; this is not an error. In Chapter 7 we shall provide a detailed explanation of why this is the case.  

**18 Chapter 1 Introduction**

_instructor ID name salary_

_department dept\_name building budget_

_member_
![alt  A sample E-R diagram](Figure-1-3.png)
**Figure 1.3** A sample E-R diagram.

• Entity sets are represented by a rectangular box with the entity set name in the header and the attributes listed below it.

• Relationship sets are represented by a diamond connecting a pair of related entity sets. The name of the relationship is placed inside the diamond.

As an illustration, consider part of a university database consisting of instruc- tors and the departments with which they are associated. Figure 1.3 shows the corresponding E-R diagram. The E-R diagram indicates that there are two entity sets, _instructor_ and _department_, with attributes as outlined earlier. The diagram also shows a relationship _member_ between _instructor_ and _department_.

In addition to entities and relationships, the E-R model represents certain constraints to which the contents of a database must conform. One important constraint is **mapping cardinalities**, which express the number of entities to which another entity can be associated via a relationship set. For example, if each instructor must be associated with only a single department, the E-R model can express that constraint.

The entity-relationship model is widely used in database design, and Chapter 7 explores it in detail.

**1.6.4 Normalization**

Another method for designing a relational database is to use a process commonly known as normalization. The goal is to generate a set of relation schemas that allows us to store information without unnecessary redundancy, yet also allows us to retrieve information easily. The approach is to design schemas that are in an appropriate _normal form_. To determine whether a relation schema is in one of the desirable normal forms, we need additional information about the real-world enterprise that we are modeling with the database. The most common approach is to use **functional dependencies**, which we cover in Section 8.4.

To understand the need for normalization, let us look at what can go wrong in a bad database design. Among the undesirable properties that a bad design may have are:

• Repetition of information

• Inability to represent certain information  

**1.6 Database Design**          19
![alt The _faculty_ table](Figure%201.4.png)
**Figure 1.4** The _faculty_ table.

We shall discuss these problems with the help of a modified database design for our university example.

Suppose that instead of having the two separate tables _instructor_ and _depart- ment_, we have a single table, _faculty_, that combines the information from the two tables (as shown in Figure 1.4). Notice that there are two rows in _faculty_ that contain repeated information about the History department, specifically, that department’s building and budget. The repetition of information in our alterna- tive design is undesirable. Repeating information wastes space. Furthermore, it complicates updating the database. Suppose that we wish to change the budget amount of the History department from $50,000 to $46,800. This change must be reflected in the two rows; contrast this with the original design, where this requires an update to only a single row. Thus, updates are more costly under the alternative design than under the original design. When we perform the update in the alternative database, we must ensure that _every_ tuple pertaining to the His- tory department is updated, or else our database will show two different budget values for the History department.

Now, let us shift our attention to the issue of “inability to represent certain information.” Suppose we are creating a new department in the university. In the alternative design above, we cannot represent directly the information concerning a department (_dept name_, _building_, _budget_) unless that department has at least one instructor at the university. This is because rows in the faculty table require values for _ID_, _name_, and _salary_. This means that we cannot record information about the newly created department until the first instructor is hired for the new department.

One solution to this problem is to introduce **null** values. The _null_ value indicates that the value does not exist (or is not known). An unknown value may be either _missing_ (the value does exist, but we do not have that information) or _not known_ (we do not know whether or not the value actually exists). As we  

**20 Chapter 1 Introduction**

shall see later, null values are difficult to handle, and it is preferable not to resort to them. If we are not willing to deal with null values, then we can create a particular item of department information only when the department has at least one instructor associated with the department. Furthermore, we would have to delete this information when the last instructor in the department departs. Clearly, this situation is undesirable, since, under our original database design, the department information would be available regardless of whether or not there is an instructor associated with the department, and without resorting to null values.

An extensive theory of normalization has been developed that helps formally define what database designs are undesirable, and how to obtain desirable de- signs. Chapter 8 covers relational-database design, including normalization.

**1.7 Data Storage and Querying**

A database system is partitioned into modules that deal with each of the re- sponsibilities of the overall system. The functional components of a database system can be broadly divided into the storage manager and the query processor components.

The storage manager is important because databases typically require a large amount of storage space. Corporate databases range in size from hundreds of gigabytes to, for the largest databases, terabytes of data. A gigabyte is approxi- mately 1000 megabytes (actually 1024) (1 billion bytes), and a terabyte is 1 million megabytes (1 trillion bytes). Since the main memory of computers cannot store this much information, the information is stored on disks. Data are moved be- tween disk storage and main memory as needed. Since the movement of data to and from disk is slow relative to the speed of the central processing unit, it is imperative that the database system structure the data so as to minimize the need to move data between disk and main memory.

The query processor is important because it helps the database system to simplify and facilitate access to data. The query processor allows database users to obtain good performance while being able to work at the view level and not be burdened with understanding the physical-level details of the implementation of the system. It is the job of the database system to translate updates and queries written in a nonprocedural language, at the logical level, into an efficient sequence of operations at the physical level.

**1.7.1 Storage Manager**

The _storage manager_ is the component of a database system that provides the interface between the low-level data stored in the database and the application programs and queries submitted to the system. The storage manager is respon- sible for the interaction with the file manager. The raw data are stored on the disk using the file system provided by the operating system. The storage man- ager translates the various DML statements into low-level file-system commands.  

**1.7 Data Storage and Querying 21**

Thus, the storage manager is responsible for storing, retrieving, and updating data in the database.

The storage manager components include:

• **Authorization and integrity manager**, which tests for the satisfaction of integrity constraints and checks the authority of users to access data.

• **Transaction manager**, which ensures that the database remains in a consis- tent (correct) state despite system failures, and that concurrent transaction executions proceed without conflicting.

• **File manager**, which manages the allocation of space on disk storage and the data structures used to represent information stored on disk.

• **Buffer manager**, which is responsible for fetching data from disk storage into main memory, and deciding what data to cache in main memory. The buffer manager is a critical part of the database system, since it enables the database to handle data sizes that are much larger than the size of main memory.

The storage manager implements several data structures as part of the phys- ical system implementation:

• **Data files,** which store the database itself.

• **Data dictionary**, which stores metadata about the structure of the database, in particular the schema of the database.

• **Indices**, which can provide fast access to data items. Like the index in this textbook, a database index provides pointers to those data items that hold a particular value. For example, we could use an index to find the _instructor_ record with a particular _ID_, or all _instructor_ records with a particular _name_. Hashing is an alternative to indexing that is faster in some but not all cases.

We discuss storage media, file structures, and buffer management in Chapter 10. Methods of accessing data efficiently via indexing or hashing are discussed in Chapter 11.

**1.7.2 The Query Processor**

The query processor components include:

• **DDL interpreter**, which interprets DDL statements and records the definitions in the data dictionary.

• **DML compiler**, which translates DML statements in a query language into an evaluation plan consisting of low-level instructions that the query evaluation engine understands.  

**22 Chapter 1 Introduction**

A query can usually be translated into any of a number of alternative evaluation plans that all give the same result. The DML compiler also performs **query optimization**; that is, it picks the lowest cost evaluation plan from among the alternatives.

• **Query evaluation engine**, which executes low-level instructions generated by the DML compiler.

Query evaluation is covered in Chapter 12, while the methods by which the query optimizer chooses from among the possible evaluation strategies are discussed in Chapter 13.

**1.8 Transaction Management**

Often, several operations on the database form a single logical unit of work. An example is a funds transfer, as in Section 1.2, in which one department account (say _A_) is debited and another department account (say _B_) is credited. Clearly, it is essential that either both the credit and debit occur, or that neither occur. That is, the funds transfer must happen in its entirety or not at all. This all-or-none requirement is called **atomicity**. In addition, it is essential that the execution of the funds transfer preserve the consistency of the database. That is, the value of the sum of the balances of _A_ and _B_ must be preserved. This correctness requirement is called **consistency**. Finally, after the successful execution of a funds transfer, the new values of the balances of accounts _A_ and _B_ must persist, despite the possibility of system failure. This persistence requirement is called **durability**.

A **transaction** is a collection of operations that performs a single logical function in a database application. Each transaction is a unit of both atomicity and consistency. Thus, we require that transactions do not violate any database- consistency constraints. That is, if the database was consistent when a transaction started, the database must be consistent when the transaction successfully ter- minates. However, during the execution of a transaction, it may be necessary temporarily to allow inconsistency, since either the debit of _A_ or the credit of _B_ must be done before the other. This temporary inconsistency, although necessary, may lead to difficulty if a failure occurs.

It is the programmer’s responsibility to define properly the various transac- tions, so that each preserves the consistency of the database. For example, the transaction to transfer funds from the account of department _A_ to the account of department _B_ could be defined to be composed of two separate programs: one that debits account _A_, and another that credits account _B_. The execution of these two programs one after the other will indeed preserve consistency. However, each program by itself does not transform the database from a consistent state to a new consistent state. Thus, those programs are not transactions.

Ensuring the atomicity and durability properties is the responsibility of the database system itself—specifically, of the **recovery manager**. In the absence of failures, all transactions complete successfully, and atomicity is achieved easily.  

**1.9 Database Architecture 23**

However, because of various types of failure, a transaction may not always com- plete its execution successfully. If we are to ensure the atomicity property, a failed transaction must have no effect on the state of the database. Thus, the database must be restored to the state in which it was before the transaction in question started executing. The database system must therefore perform **failure recovery**, that is, detect system failures and restore the database to the state that existed prior to the occurrence of the failure.

Finally, when several transactions update the database concurrently, the con- sistency of data may no longer be preserved, even though each individual transac- tion is correct. It is the responsibility of the **concurrency-control manager** to con- trol the interaction among the concurrent transactions, to ensure the consistency of the database. The **transaction manager** consists of the concurrency-control manager and the recovery manager.

The basic concepts of transaction processing are covered in Chapter 14. The management of concurrent transactions is covered in Chapter 15. Chapter 16 covers failure recovery in detail.

The concept of a transaction has been applied broadly in database systems and applications. While the initial use of transactions was in financial applica- tions, the concept is now used in real-time applications in telecommunication, as well as in the management of long-duration activities such as product design or administrative workflows. These broader applications of the transaction concept are discussed in Chapter 26.

**1.9 Database Architecture**

We are now in a position to provide a single picture (Figure 1.5) of the various components of a database system and the connections among them.

The architecture of a database system is greatly influenced by the underlying computer system on which the database system runs. Database systems can be centralized, or client-server, where one server machine executes work on behalf of multiple client machines. Database systems can also be designed to exploit par- allel computer architectures. Distributed databases span multiple geographically separated machines.

In Chapter 17 we cover the general structure of modern computer systems. Chapter 18 describes how various actions of a database, in particular query pro- cessing, can be implemented to exploit parallel processing. Chapter 19 presents a number of issues that arise in a distributed database, and describes how to deal with each issue. The issues include how to store data, how to ensure atomicity of transactions that execute at multiple sites, how to perform concurrency control, and how to provide high availability in the presence of failures. Distributed query processing and directory systems are also described in this chapter.

Most users of a database system today are not present at the site of the database system, but connect to it through a network. We can therefore differen- tiate between **client** machines, on which remote database users work, and **server** machines, on which the database system runs.  

**24  Chapter 1** **Introduction**

Database applications are usually partitioned into two or three parts, as in Figure 1.6. In a **two-tier architecture**, the application resides at the client machine, where it invokes database system functionality at the server machine through

![alt System structure](Figure%201.5.png)
**Figure 1.5** System structure.  

**1.10 Data Mining and Information Retrieval 25**

![alt Two-tier and three-tier architectures ](Figure%201.6.png)
**Figure 1.6** Two-tier and three-tier architectures.

query language statements. Application program interface standards like ODBC and JDBC are used for interaction between the client and the server.

In contrast, in a **three-tier architecture**, the client machine acts as merely a front end and does not contain any direct database calls. Instead, the client end communicates with an **application server**, usually through a forms interface. The application server in turn communicates with a database system to access data. The **business logic** of the application, which says what actions to carry out under what conditions, is embedded in the application server, instead of being distributed across multiple clients. Three-tier applications are more appropriate for large applications, and for applications that run on the World Wide Web.

**1.10 Data Mining and Information Retrieval**

The term **data mining** refers loosely to the process of semiautomatically analyzing large databases to find useful patterns. Like knowledge discovery in artificial intelligence (also called **machine learning**) or statistical analysis, data mining attempts to discover rules and patterns from data. However, data mining differs from machine learning and statistics in that it deals with large volumes of data, stored primarily on disk. That is, data mining deals with “knowledge discovery in databases.”

Some types of knowledge discovered from a database can be represented by a set of **rules**. The following is an example of a rule, stated informally: “Young women with annual incomes greater than $50,000 are the most likely people to buy small sports cars.” Of course such rules are not universally true, but rather have  

**26 Chapter 1 Introduction**

degrees of “support” and “confidence.” Other types of knowledge are represented by equations relating different variables to each other, or by other mechanisms for predicting outcomes when the values of some variables are known.

There are a variety of possible types of patterns that may be useful, and different techniques are used to find different types of patterns. In Chapter 20 we study a few examples of patterns and see how they may be automatically derived from a database.

Usually there is a manual component to data mining, consisting of preprocess- ing data to a form acceptable to the algorithms, and postprocessing of discovered patterns to find novel ones that could be useful. There may also be more than one type of pattern that can be discovered from a given database, and manual interaction may be needed to pick useful types of patterns. For this reason, data mining is really a semiautomatic process in real life. However, in our description we concentrate on the automatic aspect of mining.

Businesses have begun to exploit the burgeoning data online to make better decisions about their activities, such as what items to stock and how best to target customers to increase sales. Many of their queries are rather complicated, however, and certain types of information cannot be extracted even by using SQL.

Several techniques and tools are available to help with decision support. Several tools for data analysis allow analysts to view data in different ways. Other analysis tools precompute summaries of very large amounts of data, in order to give fast responses to queries. The SQL standard contains additional constructs to support data analysis.

Large companies have diverse sources of data that they need to use for making business decisions. To execute queries efficiently on such diverse data, companies have built _data warehouses_. Data warehouses gather data from multiple sources under a unified schema, at a single site. Thus, they provide the user a single uniform interface to data.

Textual data, too, has grown explosively. Textual data is unstructured, unlike the rigidly structured data in relational databases. Querying of unstructured textual data is referred to as _information retrieval_. Information retrieval systems have much in common with database systems—in particular, the storage and retrieval of data on secondary storage. However, the emphasis in the field of information systems is different from that in database systems, concentrating on issues such as querying based on keywords; the relevance of documents to the query; and the analysis, classification, and indexing of documents. In Chapters 20 and 21, we cover decision support, including online analytical processing, data mining, data warehousing, and information retrieval.

**1.11 Specialty Databases**

Several application areas for database systems are limited by the restrictions of the relational data model. As a result, researchers have developed several data models to deal with these application domains, including object-based data models and semistructured data models.  

**1.12 Database Users and Administrators 27**

**1.11.1 Object-Based Data Models**

Object-oriented programming has become the dominant software-development methodology. This led to the development of an **object-oriented data model** that can be seen as extending the E-R model with notions of encapsulation, methods (functions), and object identity. Inheritance, object identity, and encapsulation (information hiding), with methods to provide an interface to objects, are among the key concepts of object-oriented programming that have found applications in data modeling. The object-oriented data model also supports a rich type system, including structured and collection types. In the 1980s, several database systems based on the object-oriented data model were developed.

The major database vendors presently support the **object-relational data model**, a data model that combines features of the object-oriented data model and relational data model. It extends the traditional relational model with a variety of features such as structured and collection types, as well as object orientation. Chapter 22 examines the object-relational data model.

**1.11.2 Semistructured Data Models**

Semistructured data models permit the specification of data where individual data items of the same type may have different sets of attributes. This is in contrast with the data models mentioned earlier, where every data item of a particular type must have the same set of attributes.

The XML language was initially designed as a way of adding markup infor- mation to text documents, but has become important because of its applications in data exchange. XML provides a way to represent data that have nested structure, and furthermore allows a great deal of flexibility in structuring of data, which is important for certain kinds of nontraditional data. Chapter 23 describes the XML language, different ways of expressing queries on data represented in XML, and transforming XML data from one form to another.

**1.12 Database Users and Administrators**

A primary goal of a database system is to retrieve information from and store new information into the database. People who work with a database can be categorized as database users or database administrators.

**1.12.1 Database Users and User Interfaces**

There are four different types of database-system users, differentiated by the way they expect to interact with the system. Different types of user interfaces have been designed for the different types of users.

• **Naı̈ve users** are unsophisticated users who interact with the system by in- voking one of the application programs that have been written previously. For example, a clerk in the university who needs to add a new instructor to  

**28 Chapter 1 Introduction**

department _A_ invokes a program called _new hire_. This program asks the clerk for the name of the new instructor, her new _ID_, the name of the department (that is, _A_), and the salary.

The typical user interface for naı̈ve users is a forms interface, where the user can fill in appropriate fields of the form. Naı̈ve users may also simply read _reports_ generated from the database.

As another example, consider a student, who during class registration period, wishes to register for a class by using a Web interface. Such a user connects to a Web application program that runs at a Web server. The appli- cation first verifies the identity of the user, and allows her to access a form where she enters the desired information. The form information is sent back to the Web application at the server, which then determines if there is room in the class (by retrieving information from the database) and if so adds the student information to the class roster in the database.

• **Application programmers** are computer professionals who write application programs. Application programmers can choose from many tools to develop user interfaces. **Rapid application development (RAD)** tools are tools that en- able an application programmer to construct forms and reports with minimal programming effort.

• **Sophisticated users** interact with the system without writing programs. In- stead, they form their requests either using a database query language or by using tools such as data analysis software. Analysts who submit queries to explore data in the database fall in this category.

• **Specialized users** are sophisticated users who write specialized database applications that do not fit into the traditional data-processing framework. Among these applications are computer-aided design systems, knowledge- base and expert systems, systems that store data with complex data types (for example, graphics data and audio data), and environment-modeling systems. Chapter 22 covers several of these applications.

**1.12.2 Database Administrator**

One of the main reasons for using DBMSs is to have central control of both the data and the programs that access those data. A person who has such central control over the system is called a **database administrator (DBA)**. The functions of a DBA include:

• **Schema definition.** The DBA creates the original database schema by execut- ing a set of data definition statements in the DDL.

• **Storage structure and access-method definition.**

• **Schema and physical-organization modification.** The DBA carries out changes to the schema and physical organization to reflect the changing needs of the organization, or to alter the physical organization to improve performance.  

**1.13 History of Database Systems 29**

• **Granting of authorization for data access**. By granting different types of authorization, the database administrator can regulate which parts of the database various users can access. The authorization information is kept in a special system structure that the database system consults whenever someone attempts to access the data in the system.

• **Routine maintenance**. Examples of the database administrator’s routine maintenance activities are:

◦ Periodically backing up the database, either onto tapes or onto remote servers, to prevent loss of data in case of disasters such as flooding.

◦ Ensuring that enough free disk space is available for normal operations, and upgrading disk space as required.

◦ Monitoring jobs running on the database and ensuring that performance is not degraded by very expensive tasks submitted by some users.

**1.13 History of Database Systems**

Information processing drives the growth of computers, as it has from the earli- est days of commercial computers. In fact, automation of data processing tasks predates computers. Punched cards, invented by Herman Hollerith, were used at the very beginning of the twentieth century to record U.S. census data, and mechanical systems were used to process the cards and tabulate results. Punched cards were later widely used as a means of entering data into computers.

Techniques for data storage and processing have evolved over the years:

• **1950s and early 1960s**: Magnetic tapes were developed for data storage. Data processing tasks such as payroll were automated, with data stored on tapes. Processing of data consisted of reading data from one or more tapes and writing data to a new tape. Data could also be input from punched card decks, and output to printers. For example, salary raises were processed by entering the raises on punched cards and reading the punched card deck in synchronization with a tape containing the master salary details. The records had to be in the same sorted order. The salary raises would be added to the salary read from the master tape, and written to a new tape; the new tape would become the new master tape.

Tapes (and card decks) could be read only sequentially, and data sizes were much larger than main memory; thus, data processing programs were forced to process data in a particular order, by reading and merging data from tapes and card decks.

• **Late 1960s and 1970s**: Widespread use of hard disks in the late 1960s changed the scenario for data processing greatly, since hard disks allowed direct access to data. The position of data on disk was immaterial, since any location on disk could be accessed in just tens of milliseconds. Data were thus freed from  

**30 Chapter 1 Introduction**

the tyranny of sequentiality. With disks, network and hierarchical databases could be created that allowed data structures such as lists and trees to be stored on disk. Programmers could construct and manipulate these data structures.

A landmark paper by Codd \[1970\] defined the relational model and nonprocedural ways of querying data in the relational model, and relational databases were born. The simplicity of the relational model and the possibility of hiding implementation details completely from the programmer were enticing indeed. Codd later won the prestigious Association of Computing Machinery Turing Award for his work.

• **1980s**: Although academically interesting, the relational model was not used in practice initially, because of its perceived performance disadvantages; rela- tional databases could not match the performance of existing network and hi- erarchical databases. That changed with System R, a groundbreaking project at IBM Research that developed techniques for the construction of an efficient relational database system. Excellent overviews of System R are provided by Astrahan et al. \[1976\] and Chamberlin et al. \[1981\]. The fully functional Sys- tem R prototype led to IBM’s first relational database product, SQL/DS. At the same time, the Ingres system was being developed at the University of California at Berkeley. It led to a commercial product of the same name. Ini- tial commercial relational database systems, such as IBM DB2, Oracle, Ingres, and DEC Rdb, played a major role in advancing techniques for efficient pro- cessing of declarative queries. By the early 1980s, relational databases had become competitive with network and hierarchical database systems even in the area of performance. Relational databases were so easy to use that they eventually replaced network and hierarchical databases; programmers using such databases were forced to deal with many low-level implementation de- tails, and had to code their queries in a procedural fashion. Most importantly, they had to keep efficiency in mind when designing their programs, which involved a lot of effort. In contrast, in a relational database, almost all these low-level tasks are carried out automatically by the database, leaving the programmer free to work at a logical level. Since attaining dominance in the 1980s, the relational model has reigned supreme among data models.

The 1980s also saw much research on parallel and distributed databases, as well as initial work on object-oriented databases.

• **Early 1990s**: The SQL language was designed primarily for decision support applications, which are query-intensive, yet the mainstay of databases in the 1980s was transaction-processing applications, which are update-intensive. Decision support and querying re-emerged as a major application area for databases. Tools for analyzing large amounts of data saw large growths in usage.

Many database vendors introduced parallel database products in this period. Database vendors also began to add object-relational support to their databases.  

**1.14 Summary 31**

• **1990s**: The major event of the 1990s was the explosive growth of the World Wide Web. Databases were deployed much more extensively than ever before. Database systems now had to support very high transaction-processing rates, as well as very high reliability and 24 × 7 availability (availability 24 hours a day, 7 days a week, meaning no downtime for scheduled maintenance activities). Database systems also had to support Web interfaces to data.

• **2000s**: The first half of the 2000s saw the emerging of XML and the associated query language XQuery as a new database technology. Although XML is widely used for data exchange, as well as for storing certain complex data types, relational databases still form the core of a vast majority of large-scale database applications. In this time period we have also witnessed the growth in “autonomic-computing/auto-admin” techniques for minimizing system administration effort. This period also saw a significant growth in use of open-source database systems, particularly PostgreSQL and MySQL.

The latter part of the decade has seen growth in specialized databases for data analysis, in particular column-stores, which in effect store each column of a table as a separate array, and highly parallel database systems designed for analysis of very large data sets. Several novel distributed data-storage systems have been built to handle the data management requirements of very large Web sites such as Amazon, Facebook, Google, Microsoft and Yahoo!, and some of these are now offered as Web services that can be used by application developers. There has also been substantial work on management and analysis of streaming data, such as stock-market ticker data or computer network monitoring data. Data-mining techniques are now widely deployed; example applications include Web-based product-recommendation systems and automatic placement of relevant advertisements on Web pages.

**1.14 Summary**

• A **database-management system** (DBMS) consists of a collection of interre- lated data and a collection of programs to access that data. The data describe one particular enterprise.

• The primary goal of a DBMS is to provide an environment that is both conve- nient and efficient for people to use in retrieving and storing information.

• Database systems are ubiquitous today, and most people interact, either di- rectly or indirectly, with databases many times every day.

• Database systems are designed to store large bodies of information. The man- agement of data involves both the definition of structures for the storage of information and the provision of mechanisms for the manipulation of infor- mation. In addition, the database system must provide for the safety of the information stored, in the face of system crashes or attempts at unauthorized access. If data are to be shared among several users, the system must avoid possible anomalous results.  

**32 Chapter 1 Introduction**

• A major purpose of a database system is to provide users with an abstract view of the data. That is, the system hides certain details of how the data are stored and maintained.

• Underlying the structure of a database is the **data model**: a collection of conceptual tools for describing data, data relationships, data semantics, and data constraints.

• The relational data model is the most widely deployed model for storing data in databases. Other data models are the object-oriented model, the object- relational model, and semistructured data models.

• A **data-manipulation language (DML)** is a language that enables users to access or manipulate data. Nonprocedural DMLs, which require a user to specify only what data are needed, without specifying exactly how to get those data, are widely used today.

• A **data-definition language (DDL)** is a language for specifying the database schema and as well as other properties of the data.

• Database design mainly involves the design of the database schema. The entity-relationship (E-R) data model is a widely used data model for database design. It provides a convenient graphical representation to view data, rela- tionships, and constraints.

• A database system has several subsystems.

◦ The **storage manager** subsystem provides the interface between the low- level data stored in the database and the application programs and queries submitted to the system.

◦ The **query processor** subsystem compiles and executes DDL and DML statements.

• **Transaction management** ensures that the database remains in a consistent (correct) state despite system failures. The transaction manager ensures that concurrent transaction executions proceed without conflicting.

• The architecture of a database system is greatly influenced by the underlying computer system on which the database system runs. Database systems can be centralized, or client-server, where one server machine executes work on behalf of multiple client machines. Database systems can also be designed to exploit parallel computer architectures. Distributed databases span multiple geographically separated machines.

• Database applications are typically broken up into a front-end part that runs at client machines and a part that runs at the back end. In two-tier architectures, the front end directly communicates with a database running at the back end. In three-tier architectures, the back end part is itself broken up into an application server and a database server.  

**Practice Exercises 33**

• Knowledge-discovery techniques attempt to discover automatically statisti- cal rules and patterns from data. The field of **data mining** combines knowledge- discovery techniques invented by artificial intelligence researchers and sta- tistical analysts, with efficient implementation techniques that enable them to be used on extremely large databases.

• There are four different types of database-system users, differentiated by the way they expect to interact with the system. Different types of user interfaces have been designed for the different types of users.

**Review Terms**

• Database-management system (DBMS)

• Database-system applications • File-processing systems • Data inconsistency • Consistency constraints • Data abstraction • Instance • Schema

◦ Physical schema

◦ Logical schema

• Physical data independence • Data models

◦ Entity-relationship model

◦ Relational data model

◦ Object-based data model

◦ Semistructured data model

• Database languages

◦ Data-definition language

◦ Data-manipulation language

◦ Query language

• Metadata • Application program • Normalization • Data dictionary • Storage manager • Query processor • Transactions

◦ Atomicity

◦ Failure recovery

◦ Concurrency control

• Two- and three-tier database archi- tectures

• Data mining • Database administrator (DBA)

**Practice Exercises**

**1.1** This chapter has described several major advantages of a database system. What are two disadvantages?

**1.2** List five ways in which the type declaration system of a language such as Java or C++ differs from the data definition language used in a database.  

**34 Chapter 1 Introduction**

**1.3** List six major steps that you would take in setting up a database for a particular enterprise.

**1.4** List at least 3 different types of information that a university would main- tain, beyond those listed in Section 1.6.2.

**1.5** Suppose you want to build a video site similar to YouTube. Consider each of the points listed in Section 1.2, as disadvantages of keeping data in a file-processing system. Discuss the relevance of each of these points to the storage of actual video data, and to metadata about the video, such as title, the user who uploaded it, tags, and which users viewed it.

**1.6** Keyword queries used in Web search are quite different from database queries. List key differences between the two, in terms of the way the queries are specified, and in terms of what is the result of a query.

**Exercises**

**1.7** List four applications you have used that most likely employed a database system to store persistent data.

**1.8** List four significant differences between a file-processing system and a DBMS.

**1.9** Explain the concept of physical data independence, and its importance in database systems.

**1.10** List five responsibilities of a database-management system. For each re- sponsibility, explain the problems that would arise if the responsibility were not discharged.

**1.11** List at least two reasons why database systems support data manipulation using a declarative query language such as SQL, instead of just providing a a library of C or C++ functions to carry out data manipulation.

**1.12** Explain what problems are caused by the design of the table in Figure 1.4.

**1.13** What are five main functions of a database administrator?

**1.14** Explain the difference between two-tier and three-tier architectures. Which is better suited for Web applications? Why?

**1.15** Describe at least 3 tables that might be used to store information in a social-networking system such as Facebook.

**Tools**

There are a large number of commercial database systems in use today. The major ones include: IBM DB2 (www.ibm.com/software/data/db2), Oracle (www.oracle.com), Microsoft SQL Server (www.microsoft.com/sql), Sybase (www.sybase.com), and IBM Informix (www.ibm.com/software/data/informix). Some of these systems are available  

**Bibliographical Notes 35**

free for personal or noncommercial use, or for development, but are not free for actual deployment.

There are also a number of free/public domain database systems; widely used ones include MySQL (www.mysql.com) and PostgreSQL (www.postgresql.org).

A more complete list of links to vendor Web sites and other information is available from the home page of this book, at www.db-book.com.

**Bibliographical Notes**

We list below general-purpose books, research paper collections, and Web sites on databases. Subsequent chapters provide references to material on each topic outlined in this chapter.

Codd \[1970\] is the landmark paper that introduced the relational model. Textbooks covering database systems include Abiteboul et al. \[1995\], O’Neil

and O’Neil \[2000\], Ramakrishnan and Gehrke \[2002\], Date \[2003\], Kifer et al. \[2005\], Elmasri and Navathe \[2006\], and Garcia-Molina et al. \[2008\]. Textbook coverage of transaction processing is provided by Bernstein and Newcomer \[1997\] and Gray and Reuter \[1993\]. A book containing a collection of research papers on database management is offered by Hellerstein  and Stonebraker \[2005\].

A review of accomplishments in database management and an assessment of future research challenges appears in Silberschatz et al. \[1990\], Silberschatz et al. \[1996\], Bernstein et al. \[1998\], Abiteboul et al. \[2003\], and Agrawal et al. \[2009\]. The home page of the ACM Special Interest Group on Management of Data (www.acm.org/sigmod) provides a wealth of information about database research. Database vendor Web sites (see the Tools section above) provide details about their respective products.  

_This page intentionally left blank_
