<script setup>
//import
import { ref } from "vue";
//ตัวแปร

const travelList = ref([
  { name: "ท่าช้าง", price: 80, size: { s: 80, m: 150, l: 200 }, img: "https://www.kinnaii.com/wp-content/uploads/2020/04/Tachangnice.jpg" },
  { name: "GoodViews", price: 120, size: { s: 120, m: 180, l: 250 }, img: "https://changpuakmagazine.com/images/article/103536CHAM2650.JPG" },
  { name: "RiverSide", price: 150, size: { s: 150, m: 190, l: 300 }, img: "https://i.pinimg.com/1200x/23/4c/66/234c6672b08f6847e8f011b3c7ba376e.jpg" },
  { name: "WarmUp", price: 100, size: { s: 100, m: 200, l: 500 }, img: "https://tidroam.com/wp-content/uploads/2022/09/14-1.jpg" },
  { name: "ตะวันแดง", price: 90, size: { s: 90, m: 250, l: 700 }, img: "https://sls-prod.api-onscene.com/partner_files/trueidintrend/21246/CC697BDB-184E-48B4-9CD1-A85019FE3B35.jpeg" },
  { name: "ไวท์เฮ้าส์", price: 90, size: { s: 120, m: 220, l: 800 }, img: "https://img.wongnai.com/p/624x0/2018/04/18/cd28b784e56c4e88bbc3e39c325fc0a6.jpg" },
]);

const bookingList=ref ([])
const customerName = ref('');
const phoneNumber = ref('');
const bookingDate = ref('');
const bookingTime = ref('');

  //function
function booking(name, tableCount, customerName, phoneNumber, bookingDate, bookingTime) {
  bookingList.value.push({ name, tableCount, customerName, phoneNumber, bookingDate, bookingTime });
}

</script>

<template>

  <div class="container bg-dark text-white">
    <header style="font-size: 50px;">Reservation For table</header>
    <div class="container text-center">
      <div class="row align-items-center">
        <div class="col mb-3 my-3" v-for="(i, index) in travelList" :key="index">
          <div class="card" style="width: 18rem;">
            <img :src="i.img" class="card-img-top" alt="...">
            <div class="card-body">
              <h5 class="card-title">{{ i.name }}</h5>
              <p class="card-text">จำนวนที่โต๊ะ : <input type="number" v-model="i.tableCount"></p>
              <p class="card-text">ชื่อคนจอง: <input type="text" v-model="customerName"></p>
              <p class="card-text">เบอร์โทร: <input type="tel" v-model="phoneNumber"></p>
              <p class="card-text">วันที่จอง: <input type="date" v-model="bookingDate"></p>
              <p class="card-text">เวลาจอง: <input type="time" v-model="bookingTime"></p>
              <a href="#" class="btn btn-primary" @click="booking(i.name, i.tableCount, customerName, phoneNumber, bookingDate, bookingTime)">จองโต๊ะ</a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <table class="table" v-if="bookingList.length > 0">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">ร้านที่จอง</th>
          <th scope="col">จำนวนโต๊ะ</th>
          <th scope="col">ชื่อคนจอง</th>
          <th scope="col">เบอร์โทร</th>
          <th scope="col">วันที่จอง</th>
          <th scope="col">เวลาจอง</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in bookingList" :key="index">
          <th scope="row">{{ index + 1 }}</th>
          <td>{{ item.name }}</td>
          <td>{{ item.tableCount }}</td>
          <td>{{ item.customerName }}</td>
          <td>{{ item.phoneNumber }}</td>
          <td>{{ item.bookingDate }}</td>
          <td>{{ item.bookingTime }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>