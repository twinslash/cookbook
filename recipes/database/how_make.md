# An alternative way of rake db:drop if you haven't grant to drop databse & don't know root password on db

## postgres database:

in rails console

```ruby
a = ActiveRecord::Base.connection
sql = <<-SQL
select 'drop table if exists "' || tablename || '" cascade;' as "drop_table"
  from pg_tables
 where schemaname = 'public';
 SQL

  a.execute(sql).to_a.each do |record|
    a.execute(record["drop_table"])
  end
```

## mysql database

in rails console

```ruby
a = ActiveRecord::Base.connection
sql = <<-SQL
  SHOW TABLES;
 SQL

  a.execute(sql).to_a.flatten.each do |record|
    a.execute("drop table if exists \n"+record+"\n cascade;")
  end
```
