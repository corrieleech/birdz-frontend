<template>
  <div class="card">
    <slot></slot>
  </div>
</template>

<style>
.card {
  align-content: center;
  width: 25em;
  font-size: x-large;
  border: 3px solid;
  border-radius: 0.5rem;
  padding: 1rem;
  margin: auto;
  margin-bottom: 1rem;
  text-align: left;
}
.bigCheckbox {
  width: 15px;
  height: 15px;
}
</style>
