<template>
  <section class="grid-container">
    <div class="grid-x grid-margin-x">
      <div class="window grid-x grid-margin-x">
        <div class="cell small-12 medium-12 large-6">
          <h4>Enter text here</h4>

          <textarea
            v-on:input="translateText"
            v-model="textInput"
            placeholder="For a real time translation..."
          />
        </div>

        <div class="cell small-12 medium-12 large-6">
          <select>
            <option v-for="lang in langs" :key="lang.code">{{
              lang.lang
            }}</option>
          </select>
          <p>{{ translatedText[0] }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import axios from "axios";
import { langs } from "../data/supportedLangs";
export default {
  name: "Window",
  data() {
    return {
      langs,
      textInput: "",
      translatedText: "",
      selectedLang: langs[0],
    };
  },
  methods: {
    translateText() {
      axios
        .get(
          `https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190409T183835Z.eaf4d3d10ac5dab5.97be973af651913b93ab4476473668024436e374&text=${this.textInput}&lang=en-de`
        )
        .then((res) => {
          this.translatedText = res.data.text;
        });
    },
  },
};
</script>

<style scoped>
.window {
  background-color: #fff;
  border-radius: 10px;
  min-height: 400px;
  width: 80%;
  margin: 20px auto 50px;
  padding: 30px;
}

.window div:nth-of-type(1) {
  border-right: 3px solid #333;
  padding-right: 30px;
}

.window h4 {
  font-weight: 800;
  text-transform: uppercase;
  font-size: 18px;
  margin-top: 11px;
  margin-bottom: 9px;
}

.window textarea {
  width: 100%;
  height: 80%;
  border: none;
  font-family: "Open Sans", -apple-system, BlinkMacSystemFont, "Segoe UI",
    "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans",
    "Helvetica Neue", sans-serif;
  box-shadow: none;
  padding-top: 0;
  padding-left: 0;
}

.window textarea:focus {
  outline-style: none;
}

.window select {
  font-family: "Open Sans", -apple-system, BlinkMacSystemFont, "Segoe UI",
    "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans",
    "Helvetica Neue", sans-serif;
  border: none;
  text-transform: uppercase;
  font-weight: 800;
  font-size: 18px;
  padding-left: 0;
  height: auto;
  margin-bottom: 0;
}

.window select:active,
.window select:focus {
  outline-style: none;
  box-shadow: none;
}

div[contenteditable] {
  border: 1px solid black;
  max-height: 200px;
  overflow: auto;
}

@media screen and (max-width: 1023px) {
  .window div:nth-of-type(1) {
    border-right: none;
    padding: 0;
    border-bottom: 3px solid #333;
    padding-bottom: 30px;
  }
}
</style>
