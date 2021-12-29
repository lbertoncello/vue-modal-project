<template>
  <!-- 
    Modifies the click event to be triggered only when the element itself is clicked.
    That means that the click event will not be triggered when a child element is clicked.
  -->
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale', dark: theme === 'dark' }">
      <!-- Default slot -->
      <!-- We can use slots when we want to pass templates (complex, not just text which could be passed using props) to our component. -->
      <!-- "Default content" will be shown only if any default slot is passed. -->
      <slot>Default content</slot>
      <!-- Named slot -->
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: [ 'theme' ],
  methods: {
    closeModal() {
      // It creates a custom event called 'close'
      this.$emit('close')
    }
  }
}
</script>

<!-- scoped causes all styles to be applied only to the specified component -->
<style>
  .modal {
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
  }
  .backdrop {
    top: 0;
    position: fixed;
    background: rgba(0, 0, 0, 0.5);
    width: 100%;
    height: 100%;
  }
  .modal h1 {
    color: #03cfb4;
    border: none;
    padding: 0;
  }
  .modal p {
    font-style: normal;
  }
  .modal .actions {
    text-align: center;
    margin: 30px 0 10px 0;
  }
  .modal .actions a {
    color: #333;
    padding: 8px;
    border: 1px solid #eee;
    border-radius: 4px;
    text-decoration: none;
    margin: 10px;
  }

  .modal.sale {
    background: crimson;
    color: white;
  }
  .modal.sale h1 {
    color: white;
  }
  .modal.sale .actions {
    color: white;
  }
  .modal.sale .actions a {
    color: white;
  }

  .modal.dark {
    background: #000;
    color: white;
  }
  .modal.dark h1 {
    color: white;
  }
  .modal.dark .actions {
    color: white;
  }
  .modal.dark .actions a {
    color: white;
  }
</style>