<template>
  <section>
    <img :src="pic" alt="picture student" :width="size" :height="size" />
    <form @submit.prevent="getSummit">
      <label >กรอกชื่อเล่น : </label>
      <!-- <input type="text" @input="getName"> -->
      <input type="text" ref="nameRef">
      <button type="submit">บันทึก</button>
    </form>
    <h1>ชื่อนักเรียน : {{ getFullName}}</h1>
    <h1>ชื่อเล่น : {{ nickname}}</h1>
    <h1>อายุ : {{ age }}</h1>
    <h2>เงินเดือน : {{ salary }}</h2>
    <h2>ตำแหน่งงาน : {{ getRank }}</h2>
    <button @click="getSalary(5000)">เพิ่มเงินเดือน</button>
<button @click="toggleCheck">{{check ? "ซ่อน" : "แสดง"}}รายละเอียด</button>
    <div v-show="check">
      <h1>ที่อยู่ : <span v-html="Address"></span></h1>
    <h1>ลิงค์ : <a :href="facebook" target="_blank">Facebook</a></h1>
    <p v-if="hobby.length == 0">ไม่มีงานอดิเรก :</p>
    <div v-else>
      <ul>
        <li v-for="(item, index) in hobby" :key="index">
          {{ item }}
        </li>
      </ul>
    </div>
    <p>ข้อมูลพื้นฐาน :</p>
    <ul>
      <li v-for="(item, k) in genaral" :key="k">{{ item }}</li>
    </ul>
    </div>
  </section>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      firstName: "Parcharapon",
      lastName: "Kongjay",
      age: 22,
      Address: "<strong>สมุทรปราการ</strong>",
      pic: "https://cdn-icons-png.flaticon.com/512/219/219986.png",
      size: 300,
      facebook: "https:/facebook.com",
      hobby: ["เล่นเกมส์", "นอน", "ดูการ์ตูน"],
      genaral: { gender: "เพศชาย", pet: "เลี้ยงแมว" },
      check: false,
      salary: 30000,
      nickname:""
    };
  },
  methods: {
    toggleCheck(){
        this.check = !this.check
    },
    getSalary(v) {
      return this.salary += v;
    },
    // getName(event){
    //   console.log(event.target.value)
    // },
    getSummit(){
      this.nickname = this.$refs.nameRef.value
    }
  },
  computed:{
    getFullName() {
      return this.firstName + " " + this.lastName;
    },
    getRank() {
      return this.salary > 35000 ? "Project Manager" : "Programmer";
    },
  },
  watch:{
    salary(value){
       if(value >50000){
        alert("เงินเดือนไม่ควรเกิน 50000 บาท")
        this.salary = 30000;
        }
       }
    }
  }
</script>

<style>
</style>
