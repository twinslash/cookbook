# Drop all tables without permissions on drop whole db

An alternative way to `rake db:drop` which you couldn't execute if you have no permission to drop databases.

## PostgreSQL

Run `rails console` and put this on it:
```ruby
connection = ActiveRecord::Base.connection

query = <<-SQL
SELECT 'DROP TABLE IF EXISTS "' || tablename || '" CASCADE;' AS "drop_table"
FROM pg_tables
WHERE schemaname = 'public';
SQL

connection.execute(query).to_a.each do |record|
  connection.execute(record["drop_table"])
end
```

## MySQL

Run `rails console` and put this on it:
```ruby
connection = ActiveRecord::Base.connection

query = <<-SQL
  SHOW TABLES;
SQL

connection.execute(query).to_a.flatten.each do |record|
  connection.execute("DROP TABLE IF EXISTS \n#{record}\n CASCADE;")
end
```

