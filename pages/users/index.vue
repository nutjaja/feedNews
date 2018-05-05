<template> 
  <div>
    <h1>Users List</h1> 
    <v-select
          :items="utypelist"
          v-model="utype"
          label="Select"
          single-line
    />
    <ul>
        <li v-for="urs in filteredUsers" :key="urs.id">
          <span>{{ urs.username }}</span>
          <span>{{ urs.firstname }}</span>   
          <span>{{ urs.lastname }}</span>   
        </li>     
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      utype: '1',
      users: [], //user ทั้งหมด
      utypelist: [
        {value: '1', text: 'ผู้ดูแลระบบ'},
        {value: '2', text: 'ผู้ใช้งาน'},
        {value: '3', text: 'ผู้บริหาร'},
      ],
    }
  },
  computed: {
      filteredUsers() { //สร้าง function ที่เป็น array ตัวใหม่ขึ้นมาเพื่อโหลดข้อมูลทั้งหมดของตาราง
        return this.users.filter(x => '' + x.usertype === this.utype) 
        //filter เป็น method ของอะเรย์ โดย return array ที่ผ่านเงื่อนไข
      } //วิธีการนี้ใช้ทดแทนการ watch ได้เลย สิ่งที่อ้างอิงอยู่มีความเปลี่ยนแปลง จะทำการเปลี่ยน
  },
   async created() { 
      console.log('created')
      this.getUsers() //ยิง request 1 ครั้ง เรียกตัวเองมาแสดงได้เลย
  },
  methods: {
      async getUsers(){
        let res = await this.$http.get('/users')
        this.users = res.data.users          
      },
      editUser(id){
        this.$router.push('/student/edit?id=' + id)
      }
  }
}
</script>
