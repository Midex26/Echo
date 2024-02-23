<template>
  <div class="msg left-msg">
    <div
        class="msg-img"
        style="background-image: url(https://image.flaticon.com/icons/svg/145/145867.svg)"
    ></div>

    <div class="msg-bubble">
      <div class="msg-info">
        <div class="msg-info-name">Echo</div>
        <div class="msg-info-time"></div>
      </div>

      <div class="msg-text">
        <svg version="1.1" id="L4" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
             viewBox="0 0 100 10" enable-background="new 0 0 0 0" xml:space="preserve">
          <circle fill="#bebec4" stroke="none" cx="6" cy="5" r="4">
            <animate
                attributeName="opacity"
                dur="1s"
                values="0;1;0"
                repeatCount="indefinite"
                begin="0.1"/>
          </circle>
                  <circle fill="#bebec4" stroke="none" cx="21" cy="5" r="4">
            <animate
                attributeName="opacity"
                dur="1s"
                values="0;1;0"
                repeatCount="indefinite"
                begin="0.2"/>
          </circle>
                  <circle fill="#bebec4" stroke="none" cx="36" cy="5" r="4">
            <animate
                attributeName="opacity"
                dur="1s"
                values="0;1;0"
                repeatCount="indefinite"
                begin="0.3"/>
          </circle>
        </svg>
      </div>
    </div>
  </div>

</template>

<script>
export default {
  name: "Loading"
}

</script>

<style scoped lang="scss">
svg{
  width: 100px;
  display:inline-block;
  color: white;
}


</style>