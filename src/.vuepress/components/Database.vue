<template>
    <div>
      <h2>Database</h2>
      <p>Most web applications use a database. In this section, we are going to see how Goyave applications can query a database, using the awesome Gorm ORM.</p>
      <p>Database connections are managed by the framework and are long-lived. When the server shuts down, the database connections are closed automatically. So you don't have to worry about creating, closing or refreshing database connections in your application.</p>
      <p>Very few code is required to get started with databases. There are some configuration options that you need to change though:</p>
      <ul>
        <li>database.connection</li>
        <li>database.host</li>
        <li>database.port</li>
        <li>database.name</li>
        <li>database.username</li>
        <li>database.password</li>
        <li>database.options</li>
        <li>database.maxOpenConnection</li>
        <li>database.maxIdleConnection</li>
        <li>database.maxLifetime</li>
      </ul>
      <pre>
        <code>
          user := model.User{}
          db := database.Conn()
          db.First(&user)

          fmt.Println(user)
        </code>
      </pre>
      <p>Models are usually just normal Golang structs, basic Go types, or pointers of them. sql.Scanner and driver.Valuer interfaces are also supported.</p>
      <pre>
        <code>
          func init() {
              database.RegisterModel(&User{})
          }

          type User struct {
              gorm.Model
              Name         string
              Age          sql.NullInt64
              Birthday     *time.Time
              Email        string  `gorm:"type:varchar(100);uniqueIndex"`
              Role         string  `gorm:"size:255"` // set field size to 255
              MemberNumber *string `gorm:"unique;not null"` // set member number to unique and not null
              Num          int     `gorm:"autoIncrement"` // set num to auto incrementable
              Address      string  `gorm:"index:addr"` // create index with name `addr` for address
              IgnoreMe     int     `gorm:"-"` // ignore this field
          }
        </code>
      </pre>
      <p>Learn more about using databases in the <a href="https://goyave.dev/guide/basics/database.html">documentation</a>.</p>
    </div>
</template>

<script>
export default {
  name: "Database",
}
</script>

<style lang="stylus">
h1 {
	text-align: center;
}
</style>