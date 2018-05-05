<template>
  <div>
    <v-dialog v-model="dialog" max-width="500px">
      <v-btn color="primary" dark slot="activator" class="mb-2">เพิ่มข่าว</v-btn>
      <v-card>
        <v-card-title>
          <span class="headline">{{ formTitle }}</span>
        </v-card-title>
        <v-card-text>
          <v-container grid-list-md>
            <v-layout wrap>
              <v-flex xs12 sm6 md4>
                <v-text-field label="หัวข้อข่าว" v-model="editedItem.news_head"></v-text-field>
              </v-flex>
              <v-flex xs12 sm6 md4>
                <v-text-field label="วันที่" v-model="editedItem.news_date"></v-text-field>
              </v-flex>
              <v-flex xs12 sm6 md4>
                <v-text-field label="สถานะแสดงผล" v-model="editedItem.news_status"></v-text-field>
              </v-flex>
              <v-flex xs12 sm6 md4>
                <v-text-field label="ไฟล์" v-model="editedItem.news_files"></v-text-field>
              </v-flex>
            </v-layout>
          </v-container>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="blue darken-1" flat @click.native="close">Cancel</v-btn>
          <v-btn color="blue darken-1" flat @click.native="save">Save</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <v-data-table
      :headers="headers"
      :items="items"
      hide-actions
      class="elevation-1"
    >
      <template slot="items" slot-scope="props">
        <td>{{ props.item.news_head }}</td>
        <td class="text-xs-right">{{ props.item.news_date }}</td>
        <td class="text-xs-right">{{ props.item.news_status }}</td>
        <td class="text-xs-right">{{ props.item.news_files }}</td>
        <td class="justify-center layout px-0">
          <v-btn icon class="mx-0" @click="editItem(props.item)">
            <v-icon color="teal">edit</v-icon>
          </v-btn>
          <v-btn icon class="mx-0" @click="deleteItem(props.item)">
            <v-icon color="pink">delete</v-icon>
          </v-btn>
        </td>
      </template>
      <template slot="no-data">
        <v-btn color="primary" @click="getNews">Reset</v-btn>
      </template>
    </v-data-table>
  </div>
</template>

<script>
  export default {
    data: () => ({
      dialog: false,
      headers: [
        {
          text: 'หัวข้อข่าว',
          align: 'left',
          sortable: false,
          value: 'news_head'
        },
        { text: 'วันที่ประกาศ', value: 'news_date' },
        { text: 'สถานะ', value: 'news_status' },
        { text: 'ลิงค์ไฟล์', value: 'news_file' },
        { text: 'Actions', value: 'news_head', sortable: false }
      ],
      items: [],
      editedIndex: -1,
      editedItem: {
        news_head: '',
        news_date: '',
        news_status: '',
        news_file:''
      },
      defaultItem: {
        news_head: '',
        news_date: '',
        news_status: '',
        news_file: ''
      }
    }),

    computed: {
      formTitle () {
        return this.editedIndex === -1 ? 'New Item' : 'Edit Item'
      }
    },

    watch: {
      dialog (val) {
        val || this.close()
      }
    },

async created() { 
      this.getNews() //ยิง request 1 ครั้ง เรียกตัวเองมาแสดงได้เลย
    },

    methods: {
      async getNews(){
        let res = await this.$http.get('/news')
        this.items = res.data.news          
      },

      editItem (item) {
        this.editedIndex = this.items.indexOf(item)
        this.editedItem = Object.assign({}, item)
        this.dialog = true
      },

      deleteItem (item) {
        const index = this.items.indexOf(item)
        confirm('คุณต้องการลบข้อมูลใช่หรือไม่?') && this.items.splice(index, 1)
      },

      close () {
        this.dialog = false
        setTimeout(() => {
          this.editedItem = Object.assign({}, this.defaultItem)
          this.editedIndex = -1
        }, 300)
      },

      save () {
        if (this.editedIndex > -1) {
          Object.assign(this.items[this.editedIndex], this.editedItem)
        } else {
          this.items.push(this.editedItem)
        }
        this.close()
      }
    }
  }
</script>
