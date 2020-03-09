<template>
  <div>
    <h1>About The App</h1>
    <p>Just an app which displays corny dad jokes</p>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "About the app",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "best place for corny dad jokes"
        }
      ]
    };
  }
};
</script>

<style scoped></style>
