<template>
  <div class="hello-world-component">
    <h5>HelloWorld Component</h5>
    <div>{{ msg }}</div>
    <button type="button" @click="loadTranslations">Fetch</button>
    <ul>
      <Translation
        v-for="(value, key) in translations"
        :key="key"
        :label="key"
        :value="value"
      ></Translation>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
import Translation from "./Translation.vue";

export default {
  name: "HelloWorld",
  components: { Translation },
  props: {
    msg: String,
    other: Boolean
  },
  data() {
    return {
      translations: ""
    };
  },
  methods: {
    getTranslations(lang) {
      console.log(lang);
      let url = `https://cdn.vuplay.co.uk/ep/latest/i18n/${lang}.json`;

      axios.get(url).then(res => {
        this.translations = res.data;
      });
    },
    loadTranslations() {
      this.getTranslations("en");
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello-world-component {
  border: 1px solid #0ff;
}
</style>
