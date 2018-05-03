<template>
  <div class="text-xs-center">
    <center><h1>จัดการหัวข้อข่าว / เพิ่มรายการข่าว </h1> </center>  <br>
  <v-container fluid>
    <v-layout row>
      <v-flex xs4>
        <li class="big" :class='{red}'>
        <v-subheader>NEWS</v-subheader>
        </li>
      </v-flex>
      <v-flex xs8>
        <v-text-field
          name="input-1"
          label="จัดการหัวข้อข่าว"
          id="testing"
        ></v-text-field>
      </v-flex>
    </v-layout>
    <v-layout row>
      <v-flex xs4>
        <v-subheader>หัวข้อข่าว</v-subheader>
      </v-flex>
      <v-flex xs8>
        <v-text-field
          name="input-1"
          label="ระบุหัวข้อข่าว"
          id="testing"
        ></v-text-field>
      </v-flex>
    </v-layout>
    <v-layout row>
      <v-flex xs4>
        <v-subheader>รายละเอียดข่าว</v-subheader>
      </v-flex>
      <v-flex xs8>
        <v-text-field
          name="input-1"
          label="รายละเอียดข่าว"
          id="testing"
        ></v-text-field>
      </v-flex>
    </v-layout>
    <v-layout row>
      <v-flex xs4>
        <v-subheader>ลิงค์</v-subheader>
      </v-flex>
      <v-flex xs8>
        <v-text-field
          name="input-1"
          label=" "
          id="testing"
        ></v-text-field>
      </v-flex>
    </v-layout>
    <v-layout row>
      <v-flex xs4>
        <v-subheader>หมายเหตุ</v-subheader>
      </v-flex>
      <v-flex xs8>
        <v-text-field
          name="input-1"
          label=" "
          id="testing"
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
