<template>
  <div>
    <input :type="type" :placeholder="placeholder" />
  </div>
</template>

<script>
export default {
  name: "BaseInput",

  props: {
    placeholder: {
      type: String
    },
    type: {
      type: String,
      default: "text"
    }
  },

  components: {},

  methods: {}
};
</script>