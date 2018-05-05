<template> <!-- request ทุกครั้งที่มีการเปลี่ยนชั้นปี -->
  <div>
    <h1>Student List</h1> 
    <v-select
          :items="clslist"
          v-model="cls"
          label="Select"
          single-line
    />
    <ul>
        <li v-for="st in students" :key="st.id">
          <span>{{ st.code }}</span>
          <span>{{ st.first_name }}</span>   
          <span>{{ st.last_name }}</span>   
        </li>     
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      cls: '1',
      students: [],
      clslist: [
        {value: '1', text: 'ชั้นปีที่ 1'},
        {value: '2', text: 'ชั้นปีที่ 2'},
        {value: '3', text: 'ชั้นปีที่ 3'},
      ],
    }
  },
  watch: {
    cls(){  //ตัวแปรที่ต้องเฝ้าระวังว่าเปลี่ยนค่าเมื่อไรให้ยิง request ทันที
        this.getStudent()
    }  
  },
  async created() { 
      console.log('created')
      this.getStudent() //ยิง request 1 ครั้ง เรียกตัวเองมาแสดงได้เลย
  },
  methods: {
      async getStudent(){
        let res = await this.$http.get('/student', {params: {"class": this.cls}})
        //  console.log(res.data.student)
        this.students = res.data.student          
      }
  }
}
</script>
