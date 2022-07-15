<template>
  <button><slot /></button>
</template>

<style scoped>
    button {
        padding: 12px 20px;
        margin: 8px 0;
        display: inline-block;
        border: 1px solid #ccc;
        border-radius: 4px;
        box-sizing: border-box;
    }
    button:hover {
        background-color: orange;
    }
    button:active {
        background-color: orangered;
    }
</style>
