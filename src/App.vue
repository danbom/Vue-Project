<template>
  <div>
    <!-- 모달창 UI -->
    <div class="black-bg" v-if="detailModal" @click="detailModal = false">
      <div class="white-bg">
        <h4>상세페이지</h4>
        <p>상세페이지 내용</p>
      </div>
    </div>

    <div class="menu">
      <a v-for="(a, i) in menu" :key="i">{{ a }}</a>
    </div>
    <div v-for="(a, i) in products" :key="i">
      <img class="room-img" :src="require(`./assets/image/room${i}.jpg`)" />
      <h4 @click="detailModal = true">{{ a }}</h4>
      <p>999,999원</p>
      <button @click="ReportFunc(i)">허위매물신고</button>
      <span>신고 수 : {{ report[i] }} </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      isReport: [false, false, false],
      report: [0, 1, 2],
      menu: ["Home", "Products", "About"],
      products: ["동글원룸", "네모원룸", "세모원룸"],
      detailModal: false,
    };
  },
  methods: {
    ReportFunc(i) {
      if (this.isReport[i] === false) {
        this.report[i]++;
        this.isReport[i] = true;
      } else {
        alert("이미 신고하셨습니당");
      }
    },
  },
  components: {},
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
div {
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
