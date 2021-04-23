<template>
	<div class="features">
        <div class="feature" id="feature-clean">
            <img :src="$withBase('/undraw_code_typing_7jnv.svg')" width="275" alt="Clean">
            <div>
            <h2>Clean Code</h2>
            <p>Goyave has an expressive, elegant syntax, a robust structure and conventions. Minimalist calls and reduced redundancy are among the Goyave's core principles.</p>
            </div>
        </div>
        <div class="feature" id="feature-fast">
            <img :src="$withBase('/undraw_speed_test_wxl0.svg')" width="275" alt="Fast">
            <div>
            <h2>Fast Development</h2>
            <p>Develop faster and concentrate on the business logic of your application thanks to the many helpers and built-in functions.</p>
            </div>
        </div>
        <div class="feature" id="feature-powerful">
            <img :src="$withBase('/undraw_upgrade_06a0.svg')" width="275" alt="Powerful">
            <div>
            <h2>Powerful functionalities</h2>
            <p>Goyave is accessible, yet powerful. The framework includes routing, request parsing, validation, localization, testing, authentication, and more!</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: "Features",
}
</script>

<style lang="stylus">
body {
    width:100%;
}
h1 {
	text-align: center;
}
</style>