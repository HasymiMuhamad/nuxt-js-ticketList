<template>
  <div>
    <!-- <navbar/> -->
  
    <div class="card-item">
      <v-card
        id="card-1"
        :loading="loading"
        class="mx-auto my-12"
        style="margin-top:30px"
        v-for="(item, index) in dataName"
        v-bind:key="item.id"
      >
      <!-- {{console.log('dataName',dataName)}} -->
      <div class="card-title">
        <v-img class="icon-image" :src="item.image"/>
        <v-card-title>{{item.listName}} - {{index}}</v-card-title>
      </div>
      
      
      <v-card-text>
        <v-chip-group
          v-model="selection"
          active-class="deep-purple accent-4 white--text"
          column
        >
          <v-chip>{{item.counterNum}}</v-chip>
      
          <v-chip>7:30PM</v-chip>
      
          <v-chip>8:00PM</v-chip>
      
          <v-chip>9:00PM</v-chip>
        </v-chip-group>
      </v-card-text>
      <!-- <Spin/> -->
      <!-- <a-spin /> -->
      
      <v-card-actions>
        <v-btn
          color="deep-purple lighten-2"
          text
          @click="add(item.id)"
        >
          Add
        </v-btn>
        <v-btn
          color="deep-purple lighten-2"
          text
          @click="reserve(item.id)"
        >
          Reserve
        </v-btn>
      </v-card-actions>
      </v-card>

      
    </div>
  </div>
</template>

<script>
import navbar from '../components/navbar'
// import {Spin} from 'antd'
// import 'ant-design-vue/dist/antd.css';
// import { Spin } from 'ant-design-vue';
import '../assets/css/main.css'



export default {
    components:{
      navbar
    },
    data: () => ({
      loading: false,
      selection: 1,
      counter: 0,
      dataName : [
        {
          id : '1',
          listName : 'Lion Air',
          image: 'https://ik.imagekit.io/tvlk/image/imageResource/2015/12/17/1450349861201-09ec8f298222a73d66e8e96aa3b918f0.png?tr=dpr-2,q-75,w-28',
          counterNum: 0
        },
        {
          id : '2',
          listName : 'Citilink',
          image: 'https://ik.imagekit.io/tvlk/image/imageResource/2015/12/17/1450350561012-6584b693edd67d75cfc25ecff41c5704.png?tr=dpr-2,q-75,w-28',
          counterNum: 0
        },
        {
          id : '3',
          listName : 'Garuda Indonesia',
          image: 'https://ik.imagekit.io/tvlk/image/imageResource/2019/12/12/1576140134467-906ded3638e9045d664adc40caa8ec47.png?tr=dpr-2,q-75,w-28',
          counterNum: 0
        }
      ]
    }),

    methods: {
      reserve (data) {
        // this.dataName[data].counterNum--
        // this.dataName.find(item => item.id === data).counterNum--
        if (this.dataName.find(item => item.id === data)){
          if (this.dataName[data - 1].counterNum > 0){
            this.dataName[data - 1].counterNum--
          } else {
            return 0
          }
        }
      },
      add (data){
        console.log('data add', data)
        // this.dataName[data].counterNum++
        console.log("data boolean",Boolean(this.dataName.find(item => item.id === data)))
        // this.dataName.find(item => item.id === data).counterNum++
        if (this.dataName.find(item => item.id === data)){
          this.dataName[data - 1].counterNum++
        }
      }
    },
  }
</script>


