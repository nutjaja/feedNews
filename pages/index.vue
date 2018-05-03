<template>
  <div class="text-xs-center">
    <center><h1>จัดการหัวข้อข่าว / เพิ่มรายการข่าว </h1> </center>  <br>
  <v-container fluid>
    <v-layout row>
      <v-flex xs4>
        <v-subheader>NEWS</v-subheader>
      </v-flex>
      <v-flex xs8>
        <v-text-field
          name="input-1"
          label="จัดการหัวข้อข่าว"
          id="news"
        ></v-text-field>
      </v-flex>
    </v-layout>
    <v-layout row>
      <v-flex xs4>
        <v-subheader>หัวข้อข่าว</v-subheader>
      </v-flex>
      <v-flex xs8>
        <v-text-field
          name="input-2"
          label="ระบุหัวข้อข่าว"
          id="title"
        ></v-text-field>
      </v-flex>
    </v-layout>
    <v-layout row>
      <v-flex xs4>
        <v-subheader>รายละเอียดข่าว</v-subheader>
      </v-flex>
      <v-flex xs8>
        <v-text-field
          name="input-3"
          label="รายละเอียดข่าว"
          id="description"
        ></v-text-field>
      </v-flex>
    </v-layout>
    <v-layout row>
      <v-flex xs4>
        <v-subheader>ลิงค์</v-subheader>
      </v-flex>
      <v-flex xs8>
        <v-text-field
          name="input-4"
          label=" "
          id="link"
        ></v-text-field>
      </v-flex>
    </v-layout>
    <v-layout row>
      <v-flex xs4>
        <v-subheader>หมายเหตุ</v-subheader>
      </v-flex>
      <v-flex xs8>
        <v-text-field
          name="input-5"
          label=" "
          id="mask"
        ></v-text-field>
      </v-flex>
    </v-layout>
  </v-container> 
  <v-btn round color="primary" dark>บันทึก</v-btn>
  <v-btn round color="primary" dark>ยกเลิก</v-btn>
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
