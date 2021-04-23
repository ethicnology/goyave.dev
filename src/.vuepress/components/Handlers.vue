<template>
    <div>
      <h2>Status handlers</h2>
      <p>
        Status handlers are regular handlers executed during the finalization step of the request's lifecycle if the response body is empty but a status code has been set. Status handler are mainly used to implement a custom behavior for user or server errors (400 and 500 status codes).
      </p>
      <p>
        The following file http/controller/status/status.go is an example of custom 404 error handling:
      </p>
      <pre>
        <code>
          package status

          import "goyave.dev/goyave/v3"

          func NotFound(response *goyave.Response, request *goyave.Request) {
              if err := response.RenderHTML(response.GetStatus(), "errors/404.html", nil); err != nil {
                  response.Error(err)
              }
          }
        </code>
      </pre>
      
      <p>Status handlers are registered in the router.</p>
      <pre>
        <code>
          // Use "status.NotFound" for empty responses having status 404 or 405.
          router.StatusHandler(status.NotFound, 404)
        </code>
      </pre>
      <p>Learn more about status handlers in the <a href="https://goyave.dev/guide/advanced/status-handlers.html">documentation</a>.</p>

    </div>
</template>

<script>
export default {
  name: "Handlers",
}
</script>

<style lang="stylus">
h1 {
	text-align: center;
}
</style>