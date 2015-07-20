# foray
notes about a "build-time" ORM that emits SQL that can be inspected ahead-of-time


```bash
foray generate query user-by-email
```


```ruby 

class UserByEmail
  def initialize(email)
    @email = email
  end

  def execute
    sql = <<-SQL
    SELECT * FROM users
    WHERE u.email = ?
    SQL
    
    User.new(connection.execute(sql, @email).to_h
  end
end

```

Not that interesting yet?
Intent is to support DB interaction without the ambiguity of "what SQL is being generated", and perhaps also without the ambiguity of the statefulness of the objects.
