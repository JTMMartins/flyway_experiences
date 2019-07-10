## SpringBoot Flyway setup process with JPA

In this mini project we try to establish a strategy where our initial database tables are created by JPA, using entity fields *javax.persistence* annotations.

The project is setup to integrate flyway from the begining, and the first migration will be V1__Initial_db_setup.sql, wich is an **empty** file. 

To ensure that flyway will not use any migration as the baseline, we set the property *spring.flyway.baseline-on-migrate* to false.

If you want to experiment with this project, follow this steps


***


- Step 1 - Create the Database.
- Step 2 - Correct the datasource details to match your database.
- Step 3 - Start the project in your IDE.
- Step 4 - take attention to the logs.

If everything goes OK, you should be able to see that ***user_user***,  ***wallet*** and ***flyway_schema_history*** tables have been created.

- Step 5 - **stop the project.**
- Step 6 - Manually insert some data in your tables.

Now, inside the resources folder , you will find a special folder called db.migrations. By default this where Flyway expects to find the migrations to apply (you can change that by redefining the ***spring.flyway.locations*** property).

- Step 7 - rename the file V1.1__AddColumnToUser.CHANGE_ME_TO_SQL to V1.1__AddColumnToUser.sql.
- Step 8 - start the project on your IDE.
- Step 9 - take attention to the logs.

The V1.1 migration should be applied, a phone field has been added to the **user_user** table and your data will still be there.

- Step 10 - Change the propery value in ***spring.jpa.hibernate.ddl-auto*** FROM update TO **validate**, as from now on, we will always use flyway to all changes you want to apply to the database.

Although this is probably not the best practice (as we should have a baseline migration with the DDL to create tables and fields), it presents an alternative, which might be useful in some situations.

Important reading [flyway documentation](https://flywaydb.org/documentation/migrations) 
