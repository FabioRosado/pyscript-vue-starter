<script setup lang="ts">
</script>

<template>
  <main class="mt-28 mb-12 relative w-full px-6 py-12 bg-white md:max-w-3xl md:mx-auto lg:max-w-6xl lg:px-16 h-screen">
    <div class="prose max-w-prose mx-auto lg:mx-16 md:mx-8 lg:prose-xl md:prose-lg prose-slate">
    <h1>Welcome to PyScript Vue Starter</h1>
    <p>Let's see some basic things that you can do with PyScript. In this page, we will use the <code>py-script</code> tag in the page so you can see how to use pyscript directly.</p>

    <h2>Current time</h2>
    <py-script>
        from datetime import datetime
        now = datetime.now()
        display(now.strftime("%m/%d/%Y, %H:%M:%S"))
    </py-script>

    <h2>Repl</h2>
    <py-script>print = display</py-script>
    <py-repl output="repl-output"></py-repl>
    <div id="repl-output"></div>
    </div>
  </main>
</template>
