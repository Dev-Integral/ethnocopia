<template>
  <div class="container">
    <header class="py-3 mb-4 border-bottom">
      <h1>Vue Tom Select Wrapper</h1>
    </header>
    <main>
      <TomSelect v-model="selectedOption" :options="options" @input="handleInput" />
      <p class="mt-3">Selected Option: {{ selectedOption }}</p>
    </main>
  </div>
</template>

<script>
import TomSelect from './components/TomSelect.vue';

export default {
  components: {
    TomSelect,
  },
  data() {
    return {
      selectedOption: null,
      options: [
        { value: 'option1', text: 'Option 1' },
        { value: 'option2', text: 'Option 2' },
        { value: 'option3', text: 'Option 3' },
      ],
    };
  },
  methods: {
    // Handle input event emitted by TomSelect component
    handleInput(value) {
      this.selectedOption = value;
    }
  }
};
</script>

<style>
/* You can add custom styles here if needed */
</style>
