<template>
  <div>
    <!-- <h2>Child Component</h2> -->
    <!-- <slot></slot> -->

    <!-- fall back contents -->
    <!-- <slot>default slot</slot> -->

    <div>
      <h2>Child Component</h2>
      <slot name="head"></slot>
      <slot>default slot</slot>
      <slot name="foot"></slot>
    </div>
  </div>
</template>
