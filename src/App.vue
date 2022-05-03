<template>
  <div>
    <header>JS30 Day3 Playing with CSS variables and JS</header>
    <body>
      <h5>Update CSS Variables with <span class="hl">JS</span></h5>
      <div class="controls">
        <label for="spacing">Spacing:</label>
        <input
          id="spacing"
          type="range"
          name="spacing"
          min="10"
          max="200"
          value="10"
          data-sizing="px"
          @change="updateChange"
          @mousemove="updateChange"
        />

        <label for="blur">Blur:</label>
        <input
          id="blur"
          type="range"
          name="blur"
          min="0"
          max="25"
          value="0"
          data-sizing="px"
          @change="updateChange"
          @mousemove="updateChange"
        />

        <label for="base">Base Color</label>
        <input
          id="base"
          type="color"
          name="base"
          value="#ffc600"
          @change="updateChange"
          @mousemove="updateChange"
        />
      </div>

      <img src="https://source.unsplash.com/7bwQXzbF6KE/800x500" />
    </body>
    <footer>Chaco Wang</footer>
  </div>
</template>
<script>
export default {
  name: "App",
  methods: {
    updateChange(e) {
      const suffix = e.target.dataset.sizing || "";
      document.documentElement.style.setProperty(
        `--${e.target.name}`,
        e.target.value + suffix
      );
    },
  },
};
</script>

<style>
body,
html {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
}
:root {
  --base: #ffc600;
  --spacing: 0px;
  --blur: 0px;
}
header {
  width: 100%;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 3.5rem;
  font-family: "Square Peg", cursive;
  letter-spacing: 0.5 rem;
  background-color: rgba(200, 200, 200, 0.8);
}
img {
  padding: var(--spacing);
  background: var(--base);
  filter: blur(var(--blur));
}
.hl {
  color: var(--base);
}
body {
  text-align: center;
  background: #193549;
  color: white;
  font-family: "helvetica neue", sans-serif;
  font-weight: 100;
  font-size: 30px;
}
.controls {
  margin-bottom: 20px;
}
input {
  width: 100px;
  margin: 0 20px;
}
footer {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 2rem;
  position: fixed;
  bottom: 0;
  font-size: 1rem;
  font-weight: 200;
  letter-spacing: 2px;
  color: #fff;
  background-color: rgba(46, 43, 43, 0.7);
}
</style>
