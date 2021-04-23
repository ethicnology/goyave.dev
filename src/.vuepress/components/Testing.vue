<template>
    <div>
      <h2>Testing</h2>
      <p>
        Goyave provides an API to ease the unit and functional testing of your application. This API is an extension of testify. goyave.TestSuite inherits from testify's suite.Suite, and sets up the environment for you. That means:
      </p>
      <ul>
        <li>GOYAVE_ENV environment variable is set to test and restored to its original value when the suite is done.</li>
        <li>All tests are run using your project's root as working directory. This directory is determined by the presence of a go.mod file.</li>
        <li>Config and language files are loaded before the tests start. As the environment is set to test, you need a config.test.json in the root directory of your project.</li>
      </ul>

      <p>This setup is done by the function goyave.RunTest, so you shouldn't run your test suites using testify's suite.Run() function.</p>
      <p>The following example is a functional test and would be located in the test package.</p>
      <pre>
        <code>
          import (
              "github.com/username/projectname/http/route"
              "goyave.dev/goyave/v3"
          )

          type CustomTestSuite struct {
              goyave.TestSuite
          }

          func (suite *CustomTestSuite) TestHello() {
              suite.RunServer(route.Register, func() {
                  resp, err := suite.Get("/hello", nil)
                  suite.Nil(err)
                  suite.NotNil(resp)
                  if resp != nil {
                      defer resp.Body.Close()
                      suite.Equal(200, resp.StatusCode)
                      suite.Equal("Hi!", string(suite.GetBody(resp)))
                  }
              })
          }

          func TestCustomSuite(t *testing.T) {
              goyave.RunTest(t, new(CustomTestSuite))
          }
        </code>
      </pre>
      <p>When writing functional tests, you can retrieve the response body easily using suite.GetBody(response).</p>
      <pre>
        <code>
          resp, err := suite.Get("/get", nil)
          suite.Nil(err)
          if err == nil {
              defer resp.Body.Close()
              suite.Equal("response content", string(suite.GetBody(resp)))
          }
        </code>
      </pre>
      <p><b>URL-encoded requests:</b></p>
      <pre>
        <code>
          headers := map[string]string{"Content-Type": "application/x-www-form-urlencoded; param=value"}
          resp, err := suite.Post("/product", headers, strings.NewReader("field=value"))
          suite.Nil(err)
          if err == nil {
              defer resp.Body.Close()
              suite.Equal("response content", string(suite.GetBody(resp)))
          }
        </code>
      </pre>
      <p><b>JSON requests:</b></p>
      <pre>
        <code>
          headers := map[string]string{"Content-Type": "application/json"}
          body, _ := json.Marshal(map[string]interface{}{"name": "Pizza", "price": 12.5})
          resp, err := suite.Post("/product", headers, bytes.NewReader(body))
          suite.Nil(err)
          if err == nil {
              defer resp.Body.Close()
              suite.Equal("response content", string(suite.GetBody(resp)))
          }
        </code>
      </pre>
      <p><b>Testing JSON response:</b></p>
      <pre>
        <code>
          suite.RunServer(route.Register, func() {
              resp, err := suite.Get("/product", nil)
              suite.Nil(err)
              if err == nil {
                  defer resp.Body.Close()
                  json := map[string]interface{}{}
                  err := suite.GetJSONBody(resp, &json)
                  suite.Nil(err)
                  if err == nil { // You should always check parsing error before continuing.
                      suite.Equal("value", json["field"])
                      suite.Equal(float64(42), json["number"])
                  }
              }
          })
        </code>
      </pre>
      <p>
        The testing API has many more features such as record generators, factories, database helpers, a middleware tester, support for multipart and file uploads...
      </p>
      <p>Learn more about testing in the <a href="https://goyave.dev/guide/advanced/testing.html">documentation</a>.</p>
    </div>
</template>

<script>
export default {
  name: "Testing",
}
</script>

<style lang="stylus">
h1 {
	text-align: center;
}
</style>