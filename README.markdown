MYBATIS MIGRATIONS ANT TASKS
===============================================================

It's an Ant Script to MyBatis Migrations' commands (and other common shortcuts) just to make the developer's life easier.

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
- `db:migrate:down`
	* Undoes the last migration applied to the database.
- `db:migrate:setup`
	* Runs both tasks `db:migrate:bootstrap` and `db:migrate:up`.

Changing the environment
-----------------------------------------------------------------
The default environment is `development`, but it's possible to specify what environment to use for the migration, just use the `ENV` argument when running a task:

		$ ant db:migrate:status -DENV=production 
		
More informations about MyBatis Migrations
--------------------------------------------

- http://www.mybatis.org/java.html
- http://code.google.com/p/mybatis/