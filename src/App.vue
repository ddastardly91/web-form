<template>
  <SignupForm />
</template>

<script>
import SignupForm from "./components/SignupForm.vue";
export default {
  name: "App",
  components: { SignupForm },
};
</script>

<style>
body {
  background: #eee;
  margin: 0;
  text-align: center;
}
</style>
