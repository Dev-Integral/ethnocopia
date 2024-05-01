<template>
  <div>
    <label for="select">Select an option:</label>
    <select id="select" ref="select" class="form-select w-full" placeholder="Select an option"></select>
  </div>
</template>

<script>
import TomSelect from 'tom-select';
import 'bootstrap/dist/css/bootstrap.min.css'; // Import Bootstrap CSS

export default {
  props: ['options', 'value'],
  mounted() {
    const select = new TomSelect(this.$refs.select, {
      plugins: ['remove_button'], // Optional plugins
      ...this.$attrs, // Pass through any additional attributes
      options: this.options,
    });
    
    select.on('change', () => {
      const selectedValue = select.getValue();
      this.$emit('input', selectedValue); // Emit selected value to parent
    });
    
    // Set the initial value
    if (this.value) {
      select.setValue(this.value);
    }
  },
  watch: {
    value(newValue) {
      // Update the select value when the model value changes
      const select = this.$refs.select.tomselect;
      if (select) {
        select.setValue(newValue);
      }
    }
  }
};
</script>
