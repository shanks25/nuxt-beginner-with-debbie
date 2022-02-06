<template>
  <h1 class="text-3xl font-bold underline">{{title}}!</h1>
</template>
<script>
export default {
  name: 'IndexPage',
data() {
  return {
    title: 'Home Page'
  }
},
  head() {
    return {
      title: this.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Home page description',
        },
      ],
    }
  },
}
</script>
