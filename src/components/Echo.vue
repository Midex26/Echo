<template>
    <div class="msg left-msg">
      <div
          class="msg-img"
      ></div>

      <div class="msg-bubble">
        <div class="msg-info">
          <div class="msg-info-name">Echo</div>
          <div class="msg-info-time"></div>
        </div>

        <div class="msg-text">
          {{ message }}
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: "Echo.vue",
  props: {
    message: String
  }
}
</script>

<style lang="scss">
  .msg-bubble{
    background: linear-gradient(45deg, #1a1d3a 0%, #212752 100%);
    max-width: 50%;
    width: fit-content;
    padding: 10px;
    border-radius: 6px 6px 6px 0px;
    margin-bottom: 20px;

    .msg-info-name{
      color: #9b9ca7;
      font-size: 14px;
      font-weight: bold;
      padding-bottom: 7px;
    }

    .msg-text{
      color: #bebec4;
    }
  }
</style>