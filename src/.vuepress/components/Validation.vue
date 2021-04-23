<template>
    <div>
      <h2>Validation</h2>
      <p>Goyave provides a powerful, yet easy way to validate all incoming data, no matter its type or its format, thanks to a large number of validation rules.</p>
      <p>Incoming requests are validated using rules set, which associate rules with each expected field in the request.</p>
      <p>Validation rules can alter the raw data. That means that when you validate a field to be number, if the validation passes, you are ensured that the data you'll be using in your controller handler is a float64. Or if you're validating an IP, you get a net.IP object.</p>
      <p>Validation is automatic. You just have to define a rules set and assign it to a route. When the validation doesn't pass, the request is stopped and the validation errors messages are sent as a response.</p>
      <p>
        Rule sets are defined in the same package as the controller, typically in a separate file named request.go. Rule sets are named after the name of the controller handler they will be used with, and end with Request. For example, a rule set for the Store handler will be named StoreRequest. If a rule set can be used for multiple handlers, consider using a name suited for all of them. The rules for a store operation are often the same for update operations, so instead of duplicating the set, create one unique set called UpsertRequest.
      </p>
      <p>Example: (http/controller/product/request.go)</p>
      <pre>
        <code>
          var (
            StoreRequest validation.RuleSet = validation.RuleSet{
                "name":  {"required", "string", "between:3,50"},
                "price": {"required", "numeric", "min:0.01"},
                "image": {"nullable", "file", "image", "max:2048", "count:1"},
            }

            // ...
        </code>
      </pre>
      <p>Once your rules sets are defined, you need to assign them to your routes using the Validate() method.</p>
      <pre>
        <code>
          router.Post("/product", product.Store).Validate(product.StoreRequest)
        </code>
      </pre>
      <p>Learn more about validation in the <a href="https://goyave.dev/guide/basics/validation.html">documentation</a></p>
    </div>
</template>

<script>
export default {
  name: "Validation",
}
</script>

<style lang="stylus">
h1 {
	text-align: center;
}
</style>