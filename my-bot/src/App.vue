<template>
  <amplify-chatbot
      bot-title="Chatbot Lex"
      bot-name="BookTrip_dev"
      welcome-message="こんにちは、何かお手伝いできることはございますか？"
      voice-enabled="true"
  >
    <!-- eslint-disable-next-line vue/no-deprecated-slot-attribute -->
    <div slot="header" className="custom-header">
        <img
            src="https://raw.githubusercontent.com/aws-amplify/amplify-js/main/vscode/images/logo.png"
            height="40"
        />
        Amplify Chatbot
    </div>
  </amplify-chatbot>
</template>

<script>
const handleChatComplete = (event) => {
    const { data, err } = event.detail;
    if (data) alert('success!\n' + JSON.stringify(data));
    if (err) alert(err);
};
export default {
    name: 'App',
    components: {},
    mounted() {
        this.$el.addEventListener('chatCompleted', handleChatComplete);
    },
    beforeUnmount() {
        this.$el.removeEventListener('chatCompleted', handleChatComplete);
    },
};
</script>

<style>
:root {
  --amplify-primary-color: #fd8abd;
}

amplify-chatbot {
  --width: 450px;
  --height: 600px;
  --header-color: rgb(40, 40, 40);
  --bot-background-color: #eaebff;
  --bot-text-color: rgb(40, 40, 40);
  --user-background-color: #fd8abd;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.custom-header {
  padding: 1.25rem 0.375rem 1.25rem 0.375rem;
  text-align: center;
  font-size: 1.6rem;
}
</style>
