<template>
    <div>
      <h2>Middleware</h2>
      <p>
        Middleware are handlers executed before the controller handler. They are a convenient way to filter, intercept or alter HTTP requests entering your application. For example, middleware can be used to authenticate users. If the user is not authenticated, a message is sent to the user even before the controller handler is reached. However, if the user is authenticated, the middleware will pass to the next handler. Middleware can also be used to sanitize user inputs, by trimming strings for example, to log all requests into a log file, to automatically add headers to all your responses, etc.
      </p>
      <pre>
        <code>
          func MyCustomMiddleware(next goyave.Handler) goyave.Handler {
              return func(response *goyave.Response, request *goyave.Request) {
                  // Do something
                  next(response, request) // Pass to the next handler
              }
          }
        </code>
      </pre>
      <p>
        To assign a middleware to a router, use the router.Middleware() function. Many middleware can be assigned at once. The assignment order is important as middleware will be executed in order.
      </p>
      <pre>
        <code>
          router.Middleware(middleware.MyCustomMiddleware)
        </code>
      </pre>
      <p>Learn more about middleware in the <a href="https://goyave.dev/guide/basics/middleware.html">documentation</a>.</p>
    </div>
</template>

<script>
export default {
  name: "Middleware",
}
</script>

<style lang="stylus">
h1 {
	text-align: center;
}
</style>