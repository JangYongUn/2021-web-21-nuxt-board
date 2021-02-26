<template lang="pug">
  div.container-wrapper
    Header
		.global-wrapper
    	nuxt.next-wrapper
</template>
<script>
import Header from '~/'

export default {
	name: 'board',
	components: { Header, }
}
</script>
<style lang="scss" scoped>
  .container-wrapper {
		
  }
</style>