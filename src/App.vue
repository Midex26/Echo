<template>
  <div class="nav">
    <h1>V2 de l'IA Echo</h1>
  </div>
  <perfect-scrollbar ref="scroll" class="msger" id="chat">
    <main class="msger-chat">
      <div v-for="message in chat.slice(2)">
        <Echo v-if="message.role === 'assistant'" :message="message.content" />
        <Sender v-if="message.role === 'user'" :message="message.content" />
      </div>
      <Loading v-if="loading" />
    </main>

    <div class="msger-inputarea" >
      <input type="text" class="msger-input" v-model="user"  v-on:keyup.enter="send()" placeholder="Ecrivez votre message...">
      <button @click="send()" class="msger-send-btn"><Icon icon="tabler:send" />
      </button>
    </div>
  </perfect-scrollbar>
</template>

<script >
  import axios from "axios";
  import Sender from './components/Sender.vue'
  import Echo from './components/Echo.vue'
  import Loading from "@/components/Loading.vue";
  import { Icon } from '@iconify/vue';

  export default {
    components: {Loading, Echo, Sender, Icon},
    data(){
      return {
        chat : [
            {
              "role": "system",
              "content": "tu es moniteur d'auto-école français et tu dois aider un élève sur le code de la route, tu ne peux répondre qu'au question qui sont liées au code de la route. Si on te pose une question sur un autre thème, tu ne réponds pas. Ton nom est Echo"
            }
        ],
        user : "Présente toi en quelques mots pour commencer la conversation.",
        loading : false
      }
    },
    mounted() {
      this.send()
    },

    methods: {
      send() {
        if(this.user !== null && this.user !== ''){
          this.loading = true;
          this.chat.push({"role": "user", "content": this.user})
          this.user = null;
          this.$refs.scroll.$el.scrollTop = document.getElementById('chat').offsetHeight;

          axios.post(
              'https://api.openai.com/v1/chat/completions',
              {
                'model': 'gpt-4-turbo-preview',
                "messages": this.chat

              },
              {
                headers: {
                  'Content-Type': 'application/json',
                  'Authorization': 'Bearer ' + import.meta.env.VITE_API_KEY
                }
              }
          ).then(response => {
            this.chat.push({"role": "assistant", "content": response.data.choices[0].message.content})
            this.loading = false;
            this.$refs.scroll.$el.scrollTop = document.getElementById('chat').offsetHeight;

          } );
        }
      }
    }
  }
</script>

<style scoped lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300..800;1,300..800&family=Poppins&display=swap');

$main-bg: #0e0e23;
$body-color: #9b9ca7;

  .nav{
    background: radial-gradient(circle, #161938 0%, #13162f 100%);
    width: 100%;
    padding: 10px 30px;
    display: flex;
    align-items: center;
    border-radius: 6px;
    font-size: 15px;

    h1{
      color: white;
      font-size: 30px;
      font-weight: 500;
      font-family: "Open Sans", sans-serif;

    }
  }

.msger{
  width: 100%;
  background: radial-gradient(circle, #1a2049 0%, #13162f 100%);
  margin: 40px auto;
  padding: 20px;
  border-radius: 6px;
  max-height: 75vh;
  overflow: auto;
}

.msger-inputarea{
  input{
    margin-top: 10px;
    width: 85%;
    padding: 10px;
    border: none;
    background: #1a2049;
    color: white;
    font-size: 15px;
    font-family: "Open Sans", sans-serif;
    border-left: #4255d4 5px solid;
  }

  button{
    margin-top: 10px;
    width: 15%;
    padding: 10px;
    border: none;
    background: #1a2049;
    color: white;
    font-size: 15px;
    font-family: "Open Sans", sans-serif;
    border-left: #4255d4 5px solid;
  }
}
</style>
