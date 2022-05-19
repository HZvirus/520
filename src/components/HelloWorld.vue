<template>
  <div class="hello">
    <div class="dddd">
      <div>
        <p class="txt le">亲爱的项女士:</p>
        <p class="txt le">您好!</p>
        <p>愿意和我处对象么？</p>
        <p class="txt ri">小贺</p>
        <p class="txt ri">2022年5月20号</p>
      </div>
    </div>

    <el-button
      @click="ok"
      type="primary"
      class="btn"
      style="left: 20%; top: 70%"
      >同意</el-button
    >
    <div
      v-if="shadow.length === 0"
      class="wraper"
      :style="{ left: `${btnLeft}%`, top: `${btnTop}%` }"
      @mouseenter="demo"
    >
      <el-button @click="handleClick" class="btn">不同意</el-button>
    </div>

    <el-button
      v-for="(item, index) in shadow"
      :key="index"
      @click="ok"
      class="btn"
      type="primary"
      :style="{ left: `${item.btnLeft}%`, top: `${item.btnTop}%` }"
      >{{ item.label }}</el-button
    >
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      plan1Times: 0,
      activeIndex: 0,
      btnLeft: 60,
      btnTop: 64,
      shadow: [],
    };
  },
  created() {},
  methods: {
    handleClick() {
      // this.activeIndex++;
      // this.activeIndex = 1;
      this.plan2();
      // switch (this.activeIndex) {
      //   case 1:
      //     this.plan1();
      //     break;
      //   case 2:
      //     break;
      //   case 3:
      //     break;
      //   case 4:
      //     break;
      //   default:
      //     break;
      // }
    },
    plan1() {
      this.btnLeft = (Math.random() * 90).toFixed(1);
      this.btnTop = (Math.random() * 90).toFixed(1);
    },
    plan2() {
      let txt = ["好的", "同意", "不同意也同意", "OK", "妥妥的"];
      for (let index = 0; index < 5; index++) {
        this.shadow.push({
          btnLeft: (Math.random() * 90).toFixed(1),
          btnTop: (Math.random() * 90).toFixed(1),
          label: txt[index],
        });
      }
    },
    plan3() {},

    demo() {
      if (this.plan1Times < 10) {
        this.plan1Times++;
        this.plan1();
      }
    },
    ok() {
      this.$alert("诚挚的邀请您于2022年5月21号共进晚餐", "", {
        showConfirmButton: false,
      });
    },
  },
  beforeDestroy() {
    if (this.timer) {
      clearInterval(this.timer); // 在Vue实例销毁前，清除我们的定时器
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
* {
  margin: 0;
  padding: 0;
}
</style>
<style scoped>
.mask {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 99;
  background: #999;
}
.currentTime {
  font-size: 32px;
  color: #333;
  margin-top: 20px;
}
.hello {
  position: relative;
  height: 100vh;
}
.btn {
  position: absolute;
  transition: 0.3s all ease-in-out;
}
.txt {
  line-height: 1.5;
}
.le {
  text-align: left;
}
.ri {
  text-align: right;
}
.s2 {
  text-indent: 2em;
}
.bg-grid {
  margin: 0 auto;
  position: relative;
  height: 400px;
  padding: 10px;
  width: 85vw;
  padding-top: 64px;
  background-color: #efefef;
  background-image: linear-gradient(#e7e6e6 1px, transparent 0),
    linear-gradient(90deg, #e7e6e6 1px, transparent 0);
  background-size: 21px 21px, 21px 21px;
  background-position: center;
}

.bg-grid:before,
.bg-grid:after {
  content: "";
  position: absolute;
  z-index: 0;
  left: 50%;
  transform: translateX(-50%);
  display: inline-block;
  background-color: #fff;
  height: 28px;
  box-shadow: 68px 0 0 0 #fff, calc(68px * 2) 0 0 0 #fff,
    calc(68px * 3) 0 0 0 #fff, calc(68px * 4) 0 0 0 #fff,
    calc(68px * 5) 0 0 0 #fff, -68px 0 0 0 #fff, calc(68px * -2) 0 0 0 #fff,
    calc(68px * -3) 0 0 0 #fff, calc(68px * -4) 0 0 0 #fff,
    calc(68px * -5) 0 0 0 #fff;
}
.bg-grid:before {
  top: 0;
  width: 10px;
}

.bg-grid:after {
  top: 26px;
  width: 28px;
  border-radius: 50%;
}
.wraper {
  position: absolute;
  display: flex;
  align-content: center;
  justify-content: center;
  width: 200px;
  padding: 60px 0;
}
.dddd {
  font-size: 24px;
  display: flex;
  height: 100vh;
  align-items: center;
  justify-content: center;
  background: url("../assets/dog.jpg") no-repeat;
  background-size: 100%;
}
</style>
