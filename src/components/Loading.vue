<template>
  <div class="loading">
    <img src="./../assets/loading.png" alt="loading..." width="125px">
    <div class="progress-bar">
      <div class="progress"></div>
    </div>
  </div>
</template>

<script lang="ts">
import {Vue, Component, Prop} from 'vue-property-decorator';

@Component
export default class Spinner extends Vue {}
</script>

<style lang="scss" scoped>
.loading {
  background: hsl(205, 15, 15);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  img {
    animation-name: spin;
    animation-duration: 1s;
    animation-iteration-count: infinite;
    animation-timing-function: ease;
  }
  .progress-bar {
    margin-top: 20px;
    height: 10px;
    width: 300px;
    background: hsl(205, 25, 25);
    border-radius: 5px;
    .progress {
      border-radius: 5px;
      background: #A57D64;
      width: 150px;
      height: 100%;
    }
  }
  @keyframes spin {
    from {transform:rotate(0deg);}
    to {transform:rotate(360deg);}
  }
}

</style>
