<template>
  <div class="container">
    <h1 class="text-center">From Turkish to English</h1>
    <br />
    <div class="row">
      <div class="col-md-12 text-center"></div>
      <TranslateForm
        @historyEvent="history.push($event)"
        @translatedEvent="translatedText = $event"
      />
      <h3 class="text-success text-center">{{ translatedText }}</h3>
      <SearcHistory :history="history" />
    </div>
  </div>
</template>

<script>
import TranslateForm from "./components/TranslateForm";
import SearcHistory from "./components/SearchHistory";
export default {
  components: {
    TranslateForm,
    SearcHistory,
  },
  data() {
    return {
      translatedText: "",
      history: "",
    };
  },
};
</script>

<style></style>
