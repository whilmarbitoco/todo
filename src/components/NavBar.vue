<template>
  <div class="nav">
    <h1 class="header">ToDo</h1>
    <i class="burger fa-solid fa-bars"></i>
  </div>
</template>

<script setup></script>

<style scoped>
.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  background-color: #333;
  color: white;
  border-radius: 14px;
  margin-top: 10px;
  margin-bottom: 15px;
}

.header {
  font-size: 24px;
  margin: 0;
  font-weight: lighter;
  text-transform: uppercase;
}

.burger {
  margin-right: 8px;
  font-size: 1.5rem;
  cursor: pointer;
}
</style>
