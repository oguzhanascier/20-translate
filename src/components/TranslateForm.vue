<template>
  <form @submit.prevent="translateIt" class="well">
    <textarea
      v-model="translateText"
      cols="30"
      rows="5"
      class="form-control"
      placeholder="Çevirmek istediğiniz kelime/cümle yazınız."
    ></textarea>

    <br />
    <div class="text-left">
      <strong>Çeviri:</strong> <span>Türkçeden İngilizceye</span>
    </div>
    <br />
    <button type="submit" class="btn btn-primary btn-block">
      Çevir Gelsin!
    </button>
  </form>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      translateText: "",
      translateFrom: "tr-TR",
      translateTo: "en-GB",
    };
  },
  methods: {
    translateIt() {
      let url =
        "https://api.mymemory.translated.net/get?q=" +
        this.translateText +
        "&langpair=tr" +
        "|" +
        this.translateTo;

      axios
        .get(url)
        .then((response) => {
          this.$emit(
            "translatedEvent",
            response.data.responseData.translatedText
          );
          console.log(response);

          let history = {
            from: this.translateFrom.split("-")[0],
            to: this.translateTo.split("-")[0],
            translateText: this.translateText,
            translatedText: response.data.responseData.translatedText,
          };
          this.$emit('historyEvent',history)
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
};
</script>

<style></style>
