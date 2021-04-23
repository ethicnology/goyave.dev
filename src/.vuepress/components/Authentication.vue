<template>
    <div>
      <h2>Authentication</h2>
      <p>Goyave provides a convenient and expandable way of handling authentication in your application. Authentication can be enabled when registering your routes:</p>
      <pre>
        <code>
          import "goyave.dev/goyave/v3/auth"

          //...

          authenticator := auth.Middleware(&model.User{}, &auth.BasicAuthenticator{})
          router.Middleware(authenticator)
        </code>
      </pre>
      <p>
        Authentication is handled by a simple middleware calling an Authenticator. This middleware also needs a model, which will be used to fetch user information on a successful login.
      </p>
      <p>
        Authenticators use their model's struct fields tags to know which field to use for username and password. To make your model compatible with authentication, you must add the auth:"username" and auth:"password" tags:
      </p>
      <pre>
        <code>
          type User struct {
              gorm.Model
              Email    string `gorm:"type:char(100);uniqueIndex" auth:"username"`
              Name     string `gorm:"type:char(100)"`
              Password string `gorm:"type:char(60)" auth:"password"`
          }
        </code>
      </pre>
      <p>When a user is successfully authenticated on a protected route, its information is available in the controller handler, through the request User field.</p>
      <pre>
        <code>
          func Hello(response *goyave.Response, request *goyave.Request) {
              user := request.User.(*model.User)
              response.String(http.StatusOK, "Hello " + user.Name)
          }
        </code>
      </pre>
      <p>Learn more about authentication in the <a href="https://goyave.dev/guide/advanced/authentication.html">documentation</a>.</p>
    </div>
</template>

<script>
export default {
  name: "Authentication",
}
</script>

<style lang="stylus">
h1 {
	text-align: center;
}
</style>