<template>
  <div>
    <ul> 
      <li class="big" v-for="Ns in news" :key="Ns.newsId">
        <span>{{ Ns.newsId }}</span>
        <span>{{ Ns.topic }}</span>
        <span> แก้ไข </span>
        <span> ลบ </span>    
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      topic: 'จัดการข่าว',
      news: [
        { newsId: '001', topic: 'กำหนดการปฐมนิเทศนักศึกษาใหม่'},
        { newsId: '002', topic: 'ประกาศจัดซื้อจัดจ้าง'}, 
        { newsId: '003', topic: 'ใบลงทะเบียน ปีการศึกษา 2561'},
        { newsId: '004', topic: 'ประกาศผลการสอบ'},
      ],
    }
  }, // end data
  methods: {
    addNews(){
      this.news.push({
        newsId: this.newsId,
        topic: this.topic,
      })
    }
  }, // end methods
}
</script>
<style scoped>
.big {
  font-size: 16px;
}
.red {
  color: red;
}
</style>