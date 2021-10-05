<template>
  <div class="full">
    <div class="nav">
      <div class="logo">vuelog</div>
      <div class="menu">
        <a v-for="(a, i) in menu" :key="i" @click="mode = a">{{ a }}</a>
      </div>
    </div>
    <div class="header">
      <div class="header-bg">
        <p class="title">VUELOG</p>
        <p class="sub">Blog Wepapp made by Vue.</p>
      </div>
    </div>
    <div v-if="mode == 'Home'">
      <div class="feed">
        <div class="title">
          <div @click="post = yourpost"># Your Feed</div>
          <div @click="post = globalpost"># Global Feed</div>
        </div>
        <div v-for="(a, i) in post" :key="i">
          <div class="item">
            <div class="item-top">
              <div class="profile-img"></div>
              <div class="user-info">
                <div class="user_name">{{ a.user_name }}</div>
                <div class="date">{{ a.date }}</div>
              </div>
            </div>
            <div class="item-bottom">
              <div class="title">{{ a.title }}</div>
              <div class="content">{{ a.content }}</div>
              <div class="heart-box" @click="HeartFunc(a)">
                <span v-if="a.isHeart">💚</span>
                <span v-else>🤍</span> {{ a.heart }}
              </div>
              <!-- <div class="hit-box">
                🏏 128
              </div> -->
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- <div v-for="(a, i) in products" :key="i">
      <div
        class="black-bg"
        v-if="detailModal[i]"
        @click="detailModal[i] = false"
      >
        <div class="white-bg">
          <h4>{{ a.title }}</h4>
          <p>{{ a.content }}</p>
        </div>
      </div>

      <img class="room-img" :src="require(`./assets/image/room${i}.jpg`)" />
      <img class="room-img" :src="a.image" />
      <h4 @click="detailModal[i] = true">{{ a.title }}</h4>
      <p>{{ a.price }}원</p>
      <button @click="ReportFunc(i)">허위매물신고</button>
      <span>신고 수 : {{ report[i] }} </span>
    </div> -->
  </div>
</template>

<script>
import yourpost from "./assets/post";
import globalpost from "./assets/globalpost";

export default {
  name: "App",
  data() {
    return {
      // isHeart: [false, false, false, false, false, false],
      mode: "Home",
      feedmode: "Your",
      menu: ["Home", "✒️ New Post", "⚙️ Settings", "user_name"],
      post: yourpost,
      yourpost: yourpost,
      globalpost: globalpost,
    };
  },
  methods: {
    HeartFunc(a) {
      if (a.isHeart === false) {
        a.heart++;
        a.isHeart = true;
      } else {
        alert("이미 공감하셨습니당");
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

/* 폰트 */
@font-face {
  font-family: "NEXON Lv2 Gothic Bold";
  src: url(./assets/font/NEXONLv2GothicBold.ttf) format("woff");
  font-weight: normal;
  font-style: normal;
}
@font-face {
  font-family: "NEXON Lv2 Gothic Light";
  src: url(./assets/font/NEXONLv2GothicLight.ttf) format("woff");
  font-weight: normal;
  font-style: normal;
}
@font-face {
  font-family: "NEXON Lv2 Gothic Medium";
  src: url(./assets/font/NEXONLv2GothicMedium.ttf) format("woff");
  font-weight: normal;
  font-style: normal;
}
@font-face {
  font-family: "NEXON Lv2 Gothic";
  src: url(./assets/font/NEXONLv2Gothic.ttf) format("woff");
  font-weight: normal;
  font-style: normal;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

::-webkit-scrollbar {
  /* width: 20px; */
  display: none;
}
/* ::-webkit-scrollbar-thumb {
  background-color: #c6e883ad;
  border-radius: 10px;
}
::-webkit-scrollbar-track {
  background-color: transparent;
} */

.nav {
  left: 15%;
  display: flex;
  position: relative;
  width: 70%;
  height: 70px;

  user-select: none;
}

.nav .logo {
  flex: none;

  line-height: 70px;

  background: linear-gradient(130deg, #7ad8af 0%, #c7e883 100%);
  background-clip: text;
  color: transparent;

  font-size: 24px;
  font-family: "NEXON Lv2 Gothic Bold";
  letter-spacing: -1px;

  cursor: pointer;
}

.nav .menu {
  margin-left: auto;

  line-height: 70px;

  display: flex;
  align-items: baseline;
}

.nav .menu a {
  padding: 0 0 0 27px;

  font-size: 16px;
  font-family: "NEXON Lv2 Gothic";
  letter-spacing: -0.7px;
  color: rgb(131, 131, 131);

  cursor: pointer;

  transition: all ease 0.2s;
}

.nav .menu a:hover {
  color: rgb(46, 46, 46);
  transform: translateY(-3px);
}

.header-bg {
  width: 100%;
  height: max-content;
  padding: 10px 0;

  background: linear-gradient(130deg, #7ad8af 0%, #c7e883 100%);

  text-align: center;

  cursor: pointer;
}

.header-bg .title {
  color: white;
  font-size: 38px;
  font-family: "NEXON Lv2 Gothic Bold";
  font-weight: bold;
  letter-spacing: -2px;

  margin-bottom: 0;
}

.header-bg .sub {
  color: white;
  font-size: 18px;
  font-family: "NEXON Lv2 Gothic";
  margin-bottom: 40px;
}

.feed {
  /* left: 15%; */
  position: relative;
  padding: 7% 15%;
}

.feed .title {
  display: flex;
  width: 100%;
}

.feed .title div {
  padding-right: 27px;
  height: 37px;

  font-size: 16px;
  font-family: "NEXON Lv2 Gothic";
  letter-spacing: -0.7px;
  color: rgb(148, 148, 148);

  border-bottom: 5px solid;
  border-color: rgb(238, 238, 238);

  cursor: pointer;

  transition: all ease 0.3s;
}

.feed .title div:hover {
  background: linear-gradient(130deg, #7ad8af 0%, #c7e883 100%);
  background-clip: text;
  color: transparent;
  border-color: #7ad8af;
}

.item {
  padding: 30px 30px 25px 30px;
  margin: 30px 0;

  border-bottom: 0px solid #fff;

  position: relative;

  cursor: pointer;

  transition: all ease 0.3s;
}

.item:hover {
  transform: translateY(-8px);
  border-bottom: 8px solid #fff;
}

.item-top {
  height: max-content;

  display: flex;
}

.item-top .profile-img {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: rgb(238, 238, 238);
}

.item-top .user-info {
  margin-left: 10px;
}

.item-top .user_name {
  margin-top: 2.5px;

  font-size: 17px;
  font-family: "NEXON Lv2 Gothic";
  letter-spacing: -0.4px;
  color: #65c59c;

  cursor: pointer;
}

.item-top .date {
  font-size: 13px;
  font-family: "NEXON Lv2 Gothic";
  color: rgb(148, 148, 148);
}

.item-bottom {
  margin-top: 40px;

  cursor: pointer;
}

.item-bottom .title {
  font-size: 22px;
  font-family: "NEXON Lv2 Gothic Bold";
  color: rgb(116, 116, 116);
}

/* .item-bottom .title:hover {
  background: linear-gradient(130deg, #7ad8af 0%, #c7e883 100%);
  background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: hue 1s infinite linear;
  animation-direction: alternate;
  -webkit-animation: hue 1s infinite linear;
  -webkit-animation-direction: alternate;
} */

/* @keyframes hue {
  from {
    filter: hue-rotate(0deg);
  }
  to {
    filter: hue-rotate(90deg);
  }
} */

/* @-webkit-keyframes hue {
  from {
    -webkit-filter: hue-rotate(0deg);
  }
  to {
    -webkit-filter: hue-rotate(90deg);
  }
} */

.item-bottom .content {
  padding-top: 10px;

  font-size: 13px;
  font-family: "NEXON Lv2 Gothic";
  color: rgb(116, 116, 116);
}

.item-bottom .heart-box {
  width: 50px;
  margin-top: 35px;
  font-size: 13px;
  font-family: "NEXON Lv2 Gothic Medium";
  color: rgb(141, 141, 141);

  cursor: pointer;

  /* border: 1px solid rgb(187, 187, 187);
  border-radius: 5px; */

  transition: all ease 0.3s;
}

.item-bottom .heart-box:hover {
  /* border-color: #65c59c; */
  color: #65c59c;
}
</style>
