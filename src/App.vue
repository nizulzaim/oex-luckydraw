<template>
    <div id="app">
        <router-view/>
    </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css?family=Poppins:900i');

* {
  box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
}

body {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  background: #212121;
  margin: 0;
  padding: 0;
}

.wrapper {
  display: flex;
  justify-content: center;
}
</style>
