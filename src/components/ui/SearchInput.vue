<template>
    <label>
      <input type="text" placeholder="Заголовок поста" v-on:keyup.enter="onEndInput()" />
    </label>
  </template>
  <script>
  export default {
    props: {
      onEndInput: Function
    }
  }
  </script>
  <style lang="scss" module>
  input {
    border: 1.5px solid #e9ecef;
    border-radius: 8px;
    padding: 16px;
    transition: 0.5s linear;
    width: 100%;
    &::placeholder {
      font-weight: 400;
      font-size: 14px;
      color: #76787d;
    }
    &:focus {
      border: 1.5px solid #e31f24;
      outline: none;
      transition: 0.5s linear;
    }
  }
  </style>