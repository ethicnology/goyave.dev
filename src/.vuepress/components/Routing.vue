<template>
    <div>
      <h2>Routing</h2>
      <p>
        Routing is an essential part of any Goyave application. Routes definition is the action of associating a URI, sometimes having parameters, with a handler which will process the request and respond to it. Separating and naming routes clearly is important to make your API or website clear and expressive.
      </p>
      <p>
        Routes are defined in routes registrer functions. The main route registrer is passed to goyave.Start() and is executed automatically with a newly created root-level router.
      </p>
      <pre>
        <code>
          func Register(router *goyave.Router) {
          // Register your routes here

          // With closure, not recommended
          router.Get("/hello", func(response *goyave.Response, r *goyave.Request) {
              response.String(http.StatusOK, "Hi!")
          })

          router.Get("/hello", myHandlerFunction)
          router.Post("/user", user.Register).Validate(user.RegisterRequest)
          router.Route("PUT|PATCH", "/user", user.Update).Validate(user.UpdateRequest)
          router.Route("POST", "/product", product.Store).Validate(product.StoreRequest).Middleware(middleware.Trim)
        }
        </code>
      </pre>
      <p>
        URIs can have parameters, defined using the format {name} or {name:pattern}. If a regular expression pattern is not defined, the matched variable will be anything until the next slash.
      </p>
       <p><b>Example:</b></p>
      <pre>
        <code>
          router.Get("/product/{key}", product.Show)
          router.Get("/product/{id:[0-9]+}", product.ShowById)
          router.Get("/category/{category}/{id:[0-9]+}", category.Show)
        </code>
      </pre>
      <p>Route parameters can be retrieved as a map[string]string in handlers using the request's Params attribute.</p>
      <pre>
        <code>
          func myHandlerFunction(response *goyave.Response, request *goyave.Request) {
              category := request.Params["category"]
              id, _ := strconv.Atoi(request.Params["id"])
              //...
          }
        </code>
      </pre>
      <p>Learn more about routing in the <a href="https://goyave.dev/guide/basics/routing.html">documentation</a></p>
    </div>
</template>

<script>
export default {
  name: "Routing",
}
</script>

<style lang="stylus">
h1 {
	text-align: center;
}
</style>