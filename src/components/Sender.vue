<template>
    <div class="msg right-msg">
      <div
          class="msg-img"
          style="background-image: url(https://image.flaticon.com/icons/svg/145/145867.svg)"
      ></div>

      <div class="msg-bubble">
        <div class="msg-info">
          <p class="msg-info-name">Vous</p>
          <div class="msg-info-time"></div>
        </div>

        <p class="msg-text">
          {{ message }}
        </p>
      </div>
    </div>
</template>

<script>
export default {
  name: "Sender.vue",
  props: {
    message: String
  }
}
</script>

<style scoped lang="scss">
.msg-bubble{
  background: linear-gradient(-45deg, #1a1d3a 0%, #212752 100%);
  max-width: 50%;
  width: fit-content;
  padding: 10px;
  border-radius: 6px 6px 6px 0px;
  margin-left: auto;
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