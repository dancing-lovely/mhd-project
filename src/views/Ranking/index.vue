<template>
  <div class="page-ranking">
    <normal-header title = '排行'></normal-header>
    <div class="ranking-main">
      <header-type :types = 'types' @click = "onChange"></header-type>
      <cartoon-list :list = 'cartoonList' :isRanking = 'true'></cartoon-list>
    </div>
  </div>
</template>

<script>
import NormalHeader from '@/components/NormalHeader'
import CartoonList from '@/components/CartoonList'
import HeaderType from '@/components/HeaderType'
import { getRankList } from '@/api/cartoon'
import { unformat } from '@/utils/apiHelp'

export default {
  name: 'Ranking',
  data () {
    return {
      types: [
        { id: 1, description: '热搜榜', ranktype: 6 },
        { id: 2, description: '人气榜', ranktype: 1 },
        { id: 3, description: '畅销榜', ranktype: 4 },
        { id: 4, description: '新书榜', ranktype: 2 },
        { id: 5, description: '完结榜', ranktype: 5 },
        { id: 6, description: '免费榜', ranktype: 3 }
      ],
      ranklist: []
    }
  },
  computed: {
    cartoonList () {
      return this.ranklist.map(item => {
        return {
          id: item.bigbookid,
          coverurl: item.coverurl,
          name: item.name,
          author: item.author,
          view: item.sales
        }
      })
    }
  },
  components: {
    NormalHeader,
    CartoonList,
    HeaderType
  },
  methods: {
    getRankList (ranktype) {
      getRankList(ranktype).then(res => {
        if (res.code === 200) {
          // this.types = res.info
          const result = JSON.parse(unformat(res.info))
          this.ranklist = result.ranklist
        } else {
          alert(res.code_msg)
        }
      }).catch(err => {
        console.log(err)
        alert('网络异常')
      })
    },
    onChange (payload) {
      this.getRankList(payload.data.ranktype)
    }
  },
  created () {
    this.getRankList(this.types[0].ranktype)
  }
}
</script>

<style lang="scss" scoped>
.page-ranking {
  display: flex;
  flex-direction: column;
  height: 100%;

  .ranking-main {
    flex: 1;
    overflow-y: auto;
  }
}
</style>
