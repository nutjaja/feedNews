<template>
  <div>
      <h1> Chat Room </h1>
      <div>
          <v-text-field v-model="name" label= "ชื่อ" />
          <v-text-field v-model="text" label= "ข้อความ" />
          <v-btn @click = "send">ส่ง</v-btn>
      </div>
      <ui>
          <li v-for="(m, idx) in msg" :key="idx">
              <b>{{ m.name }}</b> พูดว่า {{m.text}}
          </li>
      </ui>
  </div>
</template>
<script>
export default {
    data(){
      return{
          name: '',
          text: '',
          msg: [],
      }
    },  
 
    created(){
        this.$socket.subscribe('room39',this.onMsg)
    },//created เขียนเพื่อ subscribe

    beforeDestroy(){
        this.$socket.subscribe('room39')
    }, //เขียนเพื่อ unsubscribe
   
    methods:{
        send(){
            this.$socket.publish('room39',{
                name: this.name,
                text: this.text,
            })
        }, //send ส่งข้อความลงห้องchat
        onMsg(data){
            this.msg.unshift(data)//แสดงข้อความใหม่อยู่ข้างบน
         }
    }//method
}
</script>
