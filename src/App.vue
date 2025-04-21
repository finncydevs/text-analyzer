<template>
  <main
    class="bg-gradient-to-r from-slate-900 to-slate-700 min-h-screen flex flex-col justify-center items-center"
  >
    <div class="max-w-xl mx-auto p-6 bg-white rounded shadow">
      <h1 class="text-2xl font-bold mb-4">Text Analyzer</h1>
      <textarea
        v-model="text"
        class="w-full p-3 border rounded resize-none focus:outline-none focus:ring-2 focus:ring-blue-500"
        rows="8"
        placeholder="Type your text here..."
      ></textarea>
      <div class="mt-4 grid grid-cols-1 sm:grid-cols-3 gap-4 text-center">
        <div class="p-4 bg-gray-100 rounded">
          <p class="text-sm text-gray-600">Letters</p>
          <p class="text-xl font-semibold">{{ letterCount }}</p>
        </div>
        <div class="p-4 bg-gray-100 rounded">
          <p class="text-sm text-gray-600">Words</p>
          <p class="text-xl font-semibold">{{ wordCount }}</p>
        </div>
        <div class="p-4 bg-gray-100 rounded">
          <p class="text-sm text-gray-600">Sentences</p>
          <p class="text-xl font-semibold">{{ sentenceCount }}</p>
        </div>
      </div>
    </div>
    <footer>
      <div class="text-center mt-6">
        <p class="text-sm text-white">
          Created with ❤️ by <b> Finn</b> with
          <a
            href="https://vuejs.org/"
            class="text-green-600"
            rel="noopener noreferrer"
            target="_blank"
            >Vue</a
          >
        </p>
        <p class="text-sm text-white">
          Source code available on
          <a
            href=""
            class="text-blue-500 hover:underline"
            target="_blank"
            rel="noopener noreferrer"
            >GitHub</a
          >
        </p>
      </div>
    </footer>
  </main>
</template>

<script>
export default {
  name: "TextAnalyzer",
  data() {
    return {
      text: "",
    };
  },
  computed: {
    letterCount() {
      // Remove all non-letter characters and count the remaining
      return (this.text.match(/[a-zA-Z]/g) || []).length;
    },
    wordCount() {
      // Match words using regex
      return (this.text.match(/\b\w+\b/g) || []).length;
    },
    sentenceCount() {
      // Match sentence-ending punctuation followed by a space or end of string
      return (this.text.match(/[^.!?]+[.!?]+(\s|$)/g) || []).length;
    },
  },
};
</script>
