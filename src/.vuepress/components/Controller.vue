<template>
    <div>
      <h2>Controller</h2>
      <p>
        Controllers are files containing a collection of Handlers related to a specific feature. Each feature should have its own package. For example, if you have a controller handling user registration, user profiles, etc, you should create a http/controller/user package. Creating a package for each feature has the advantage of cleaning up route definitions a lot and helps keeping a clean structure for your project.
      </p>
      <p>
        A Handler is a func(*goyave.Response, *goyave.Request). The first parameter lets you write a response, and the second contains all the information extracted from the raw incoming request.
      </p>
      <p>
        Handlers receive a goyave.Response and a goyave.Request as parameters.
        goyave.Request can give you a lot of information about the incoming request, such as its headers, cookies, or body. Learn more here.
        goyave.Response implements http.ResponseWriter and is used to write a response. If you didn't write anything before the request lifecycle ends, 204 No Content is automatically written. Learn everything about reponses here.
      </p>
      <p>
        Let's take a very simple CRUD as an example for a controller definition: http/controller/product/product.go:
      </p>
      <pre>
        <code>
          func Index(response *goyave.Response, request *goyave.Request) {
              products := []model.Product{}
              result := database.Conn().Find(&products)
              if response.HandleDatabaseError(result) {
                  response.JSON(http.StatusOK, products)
              }
          }

          func Show(response *goyave.Response, request *goyave.Request) {
              product := model.Product{}
              result := database.Conn().First(&product, request.Params["id"])
              if response.HandleDatabaseError(result) {
                  response.JSON(http.StatusOK, product)
              }
          }

          func Store(response *goyave.Response, request *goyave.Request) {
              product := model.Product{
                  Name:  request.String("name"),
                  Price: request.Numeric("price"),
              }
              if err := database.Conn().Create(&product).Error; err != nil {
                  response.Error(err)
              } else {
                  response.JSON(http.StatusCreated, map[string]uint{"id": product.ID})
              }
          }

          func Update(response *goyave.Response, request *goyave.Request) {
              product := model.Product{}
              db := database.Conn()
              result := db.Select("id").First(&product, request.Params["id"])
              if response.HandleDatabaseError(result) {
                  if err := db.Model(&product).Update("name", request.String("name")).Error; err != nil {
                      response.Error(err)
                  }
              }
          }

          func Destroy(response *goyave.Response, request *goyave.Request) {
              product := model.Product{}
              db := database.Conn()
              result := db.Select("id").First(&product, request.Params["id"])
              if response.HandleDatabaseError(result) {
                  if err := db.Delete(&product).Error; err != nil {
                      response.Error(err)
                  }
              }
          }
        </code>
      </pre>
      <p>Learn more about configuration in the <a href="https://goyave.dev/guide/basics/controllers.html">documentation</a></p>
    </div>
</template>

<script>
export default {
  name: "Controller",
}
</script>

<style lang="stylus">
h1 {
	text-align: center;
}
</style>