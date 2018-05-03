<template>
  <div>
    <center><h1>จัดการหัวข้อข่าว / เพิ่มรายการข่าว </h1> </center>  <br>
    <input type="text" v-model="code"> <br>
    <input type="text" v-model="name">
    <button @click="addNews">ADD</button> 
    <button @click="CANCLE">CANCLE</button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      id: 1,
    }
  },
}
</script>
