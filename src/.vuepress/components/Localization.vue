<template>
    <div>
      <h2>Localization</h2>
      <p>The Goyave framework provides a convenient way to support multiple languages within your application. Out of the box, Goyave only provides the en-US language.</p>
      <p>Language files are stored in the resources/lang directory.</p>
      <pre>
        <code>
          .
          └── resources
              └── lang
                  └── en-US (language name)
                      ├── fields.json (optional)
                      ├── locale.json (optional)
                      └── rules.json (optional)
        </code>
      </pre>
      <p>
        The fields.json file contains the field names translations and their rule-specific messages. Translating field names helps making more expressive messages instead of showing the technical field name to the user. Rule-specific messages let you override a validation rule message for a specific field.
      </p>
      <p><b>Example:</b></p>
      <pre>
        <code>
          {
              "email": {
                  "name": "email address",
                  "rules": {
                      "required": "You must provide an :field."
                  }
              }
          }
        </code>
      </pre>
      <p>The locale.json file contains all language lines that are not related to validation. This is the place where you should write the language lines for your user interface or for the messages returned by your controllers.</p>
      <p><b>Example:</b></p>
      <pre>
        <code>
          {
              "product.created": "The product have been created with success.",
              "product.deleted": "The product have been deleted with success."
          }
        </code>
      </pre>
      <p>
        The rules.json file contains the validation rules messages. These messages can have placeholders, which will be automatically replaced by the validator with dynamic values. If you write custom validation rules, their messages shall be written in this file.
      </p>
      <p><b>Example:</b></p>
      <pre>
        <code>
          {
              "integer": "The :field must be an integer.",
              "starts_with": "The :field must start with one of the following values: :values.",
              "same": "The :field and the :other must match."
          }
        </code>
      </pre>
      <p>
        When an incoming request enters your application, the core language middleware checks if the Accept-Language header is set, and set the goyave.Request's Lang attribute accordingly. Localization is handled automatically by the validator.
      </p>
      <p><b>Example:</b></p>
      <pre>
        <code>
          func ControllerHandler(response *goyave.Response, request *goyave.Request) {
              response.String(http.StatusOK, lang.Get(request.Lang, "my-custom-message"))
          }
        </code>
      </pre>
      <p>Learn more about localization in the <a href="https://goyave.dev/guide/advanced/localization.html">documentation</a>.</p>
    </div>
</template>

<script>
export default {
  name: "Localization",
}
</script>

<style lang="stylus">
h1 {
	text-align: center;
}
</style>