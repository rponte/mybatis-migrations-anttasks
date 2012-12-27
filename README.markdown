MYBATIS MIGRATIONS ANT TASKS
===============================================================

It's an Ant Script to MyBatis Migrations' commands (and other common shortcuts) just to make the developer's life easier.

The names of the tasks are following the style of Ruby On Rails Migrations.

How to Install
-----------------
After downloading or cloning this repository you just need to copy three artifacts to your project, `build.xml`, `build.properties` and `mybatis-migrations` directory.

You'll need to run this command to prepare the mybatis structure within your project:
		$ ant db:migrate:init

When the command is completed, the directory `./db` will be created containing the following sub-directories:

- `./drivers`
	* Place your JDBC driver .jar or .zip files in this directory. Upon running a migration, the drivers will be dynamically loaded.
- `./environments`
	* In the environments folder you will find .properties files that represent your database instances. By default a **development.properties** file is created for you to configure your development time database properties. You can also create `test.properties` and `production.properties` files.
- `./scripts`
	* This directory contains your migration SQL files. These are the files that contain your DDL to both upgrade and downgrade your database structure. By default, the directory will contain the script to create the **changelog** table, plus one empty example migration script. 

To create a new migration script, use the **"db:migrate:new"** task. To run all pending migrations, use the **"db:migrate:up"** task. To undo the last migration applied, use the **"db:migrate:down"** task etc. For more details, please, read the [MyBatis Migrations Documentation](https://github.com/rponte/mybatis-migrations-anttasks/blob/master/mybatis-migrations/MyBatis-3-Migrations.pdf).

Tasks
-------------
Actually there're only these tasks:

- `db:migrate:init`
	* Creates (if necessary) and initializes a migration path.
- `db:migrate:new`
	* Creates a new migration with the provided description.
- `db:migrate:bootstrap`
	* Runs the bootstrap SQL script (see `scripts/bootstrap.sql` for more).
- `db:migrate:status`
	* Prints the changelog from the database if the changelog table exists.
- `db:migrate:up`
	* Run all unapplied migrations.
- `db:migrate:up:force`
	* Run all unapplied migrations and forces script to continue even if SQL errors are encountered.
- `db:migrate:down`
	* Undoes the last migration applied to the database.
- `db:migrate:setup`
	* Runs both tasks `db:migrate:bootstrap` and `db:migrate:up`.

Changing the environment
-----------------------------------------------------------------
The default environment is `development` but you may change it through `build.properties` file, just change the property `default.environment` for the one you want to.

It's also possible to specify what environment to use for the migration through command line, just use the `ENV` argument when running a task:

		$ ant db:migrate:status -DENV=production 
		
More informations about MyBatis Migrations
--------------------------------------------

- http://www.mybatis.org/java.html
- http://code.google.com/p/mybatis/