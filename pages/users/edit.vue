<template>
  <div>
      <h1>Users Edit </h1>
      <v-text-field v-model="firstname" label="ชื่อ" />
      <v-text-field v-model="lastname" label="นามสกุล" />
      <v-text-field v-model="depart" label="งาน/แผนก" />
      <v-text-field v-model="usertype" label="ประเภทผู้ใช้งาน" />     
      <v-btn @click="save"> บันทึก </v-btn>
  </div>
</template>
<script>
//http://localhost:3000/student/edit?id=1
export default {
  data(){
      return{
          firstname: '',
          lastname: '',
          depart: '',
          usertype: '',
      }
  },
  async created(){
    let res = await this.$http.get('/users/id/' + this.$route.query.id)
    this.firstname = res.data.users.firstname || '' // '' ใน script มีค่าเป็นเท็จ
    this.lastname = res.data.users.lastname || ''
    this.depart = res.data.users.depart || ''
    this.usertype = res.data.users.usertype || ''
   },
  methods: {
      async save() {
          console.log("tesssssttttt")
          let res = await this.$http.post('/users/save', {
          id: this.$route.query.id,
          firstname: this.firstname,
          lastname: this.lastname,
          depart: this.depart,
          usertype: this.usertype,
          })
          if (!res.data.ok){
              //TODO: แสดงข้อความว่า บันทึกไม่สำเร็จ
          } else {
              // แสดงข้อความว่า บันทึกสำเร็จ
          }
      },
  },
}
</script>

