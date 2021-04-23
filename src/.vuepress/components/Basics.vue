<template>
    <div>
      <h1>Features Tour</h1>
      
      <div>
        <h2>Hello world from scratch</h2>
        <p>The example below shows a basic Hello world application using Goyave.</p>
        <pre>
          <code>
            import "goyave.dev/goyave/v3"
            
            func registerRoutes(router *goyave.Router) {
                router.Get("/hello", func(response *goyave.Response, request *goyave.Request) {
                    response.String(http.StatusOK, "Hello world!")
                })
            }

            func main() {
                if err := goyave.Start(registerRoutes); err != nil {
                    os.Exit(err.(*goyave.Error).ExitCode)
                }
            }
          </code>
        </pre>
      </div>

    <div>
      <h2>Configuration</h2>
      <p>To configure your application, use the config.json file at your project's root. If you are using the template project, copy config.example.json to config.json. The following code is an example of configuration for a local development environment:</p>
      <pre>
        <code>
          {
            "app": {
                "name": "goyave_template",
                "environment": "localhost",
                "debug": true,
                "defaultLanguage": "en-US"
            },
            "server": {
                "host": "127.0.0.1",
                "maintenance": false,
                "protocol": "http",
                "domain": "",
                "port": 8080,
                "httpsPort": 8081,
                "timeout": 10,
                "maxUploadSize": 10
            },
            "database": {
                "connection": "mysql",
                "host": "127.0.0.1",
                "port": 3306,
                "name": "goyave",
                "username": "root",
                "password": "root",
                "options": "charset=utf8mb4&collation=utf8mb4_general_ci&parseTime=true&loc=Local",
                "maxOpenConnections": 20,
                "maxIdleConnections": 20,
                "maxLifetime": 300,
                "autoMigrate": false
            }
          } 
        </code>
      </pre>
      <p>If this config file misses some config entries, the default values will be used.</p>
      <p>
        All entries are validated. That means that the application will not start if you provided an invalid value in your config (for example if the specified port is not a number). That also means that a goroutine trying to change a config entry with the incorrect type will panic.
        Entries can be registered with a default value, their type and authorized values from any package.
      </p>
      <p><b>Getting a value:</b></p>
      <pre>
        <code>
          config.GetString("app.name") // "goyave"
          config.GetBool("app.debug") // true
          config.GetInt("server.port") // 80
          config.Has("app.name") // true
        </code>
      </pre>
      <p><b>Setting a value:</b></p>
      <pre>
        <code>
          config.Set("app.name", "my awesome app")
        </code>
      </pre>
      <p><b>Using environment variables:</b></p>
      <pre>
        <code>
          {
            "database": {
              "host": "${DB_HOST}"
            }
          }
        </code>
      </pre>
      <p>Learn more about configuration in the <a href="https://goyave.dev/guide/configuration.html">documentation</a>.</p>
    </div>

    </div>
</template>

<script>
export default {
  name: "Basics",
}
</script>

<style lang="stylus">
h1 {
	text-align: center;
}
</style>