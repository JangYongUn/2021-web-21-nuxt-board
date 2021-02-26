<template lang="pug">
	.list-wrapper
    .title-wrapper
        h2 Nuxt / Vue를 활용한 게시판
    v-data-table(:headers="headers" :items="list" :items-per-page="5" class="elevation-1")
</template>
<script>
export default {
	name: 'list',
	layout: 'board',
  data(s) {
    return {
      headers: [
        { text: '번호', align: 'center', sortable: true, value: 'id',},
          { text: '제목', value: 'title' },
          { text: '작성자', value: 'writer' },
          { text: '작성일', value: 'wdate' },
          { text: '첨부파일', value: 'orifile' },
          { text: '조회수', value: 'readnum' },
      ],
    }
  },
  async asyncData({ $axios, store, params, query }) {
    try {
      let { data: list } = await this.$axios.get('http://127.0.0.1:3000/api/list')
      list.map(v => {
        v.wdate = moment(v.created).format('YYYY-MM-DD')
      })
      return { list }
    }
    catch {

    }
  },
}
</script>
<style lang="scss">
	.title-wrapper {
    background-color: $colorLighter;
    color: $colorDarker;
    padding: 1em;
    margin: 2em 0;
  }
  table {
    td {
      text-align: center;
      &:nth-child() {
        
      }
    }
  }
</style>