<template>
<main class="mt-28 mb-12 relative w-full px-6 py-12 bg-white md:max-w-3xl md:mx-auto lg:max-w-6xl lg:px-16">
    <div class="prose max-w-prose mx-auto lg:mx-16 md:mx-8 lg:prose-xl md:prose-lg prose-slate">
      <h1>Using a python file as source</h1>
      <p>In this page the pyscript is being sourced directly from <code>test.py</code>, we need to add the file into the <code>public</code> folder so pyscript has access to it.</p>
    </div>
  </main>
    <div id="output"></div>
    <py-script src="/test.py">
    </py-script>

</template>

