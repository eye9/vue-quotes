<template>
  <main>
    <h1>QUOTES</h1>
    <div class="loader" id="loader" :hidden="!isHidden" ref="loader"></div>
    <section class="quote-container" ref="qcontainer" :hidden="isHidden">
      <p class="text">
        <i class="fas fa-quote-left"></i>
        <span id="quote" class="quote"> {{ quote }}</span>
      </p>
      <p class="author" id="author">{{ author }}</p>
      <div class="buttons">
        <button class="new-quote" id="new-quote" @click="showNewQuote">
          NEW QUOTE
        </button>
      </div>
    </section>
  </main>
</template>

<script>
import { getLocalQuote } from "./components/localQuotes.js";

export default {
  data() {
    return {
      isHidden: false,
      quote:
        "What you are is what you have been. What you'll be is what you do now.",
      author: "Buddha",
    };
  },

  methods: {
    flip() {
      this.isHidden = !this.isHidden;
    },

    showNewQuote() {
      this.flip();
      setTimeout(this.flip, 1000);
      
      const newQuote = getLocalQuote();

      this.quote = newQuote.text;
      if (!newQuote.author) newQuote.author = "Unknown";
      this.author = newQuote.author;
    },
  },
};
</script>

<style></style>
