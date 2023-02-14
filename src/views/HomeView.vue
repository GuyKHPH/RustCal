<template>
  <main>
    <div class="flex h-screen justify-center items-center bg-slate-600">
      <div class="w-80 text-2xl font-bold text-slate-500">
        <div
          class="bg-slate-800 py-5 mb-1 pr-4 text-white text-right transition delay-75 ease-in-out"
        >
          <h1 class="text-lg">
            {{ numinput2 }}
          </h1>
          <div>{{ numinput }}</div>
        </div>
        <div class="grid grid-cols-4 grid-rows-5 gap-1 text-center">
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="setto0()"
          >
            <h1>CE</h1>
          </button>
          <button
            @click="persent()"
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
          >
            <h1>%</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="deletOneLast()"
          >
            <h1>x=</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="funcal(4)"
          >
            <h1>/</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="clickNumber('7')"
            >
            <h1 >7</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="clickNumber('8')"
            >
            <h1 >8</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="clickNumber('9')"
            >
            <h1 >9</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="funcal(3)"
          >
            <h1>x</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="clickNumber('4')"
            >
            <h >4</h>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="clickNumber('5')"
            >
            <h1 >5</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="clickNumber('6')"
            >
            <h1 >6</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="funcal(2)"
          >
            <h1>-</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="clickNumber('1')"
            >
            <h1 >1</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="clickNumber('2')"
            >
            <h1 >2</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="clickNumber('3')"
            >
            <h1>3</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="funcal(1)"
          >
            <h1>+</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="convert()"
          >
            <h1>+/-</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
          >
            <h1 @click="clickNumber('0')">0</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
          >
            <h1>.</h1>
          </button>
          <button
            class="bg-slate-800 font-bold text-slate-500 transition delay-75 ease-in-out py-5"
            @click="cal()"
          >
            <h1>=</h1>
          </button>
        </div>
      </div>
    </div>
  </main>
</template>
<script>
export default {
  data() {
    return {
      numinput: "0",
      numinput2: null,
      stat: null,
      
    };
  },
  methods: {
    // บวก
    funcal(stat) {
      if (this.stat != null) {
        this.cal();
        this.funcal(stat);
      } else {
        this.stat = stat;
        console.log(this.stat);
        this.setval();
      }
    },
    // แปลงบวกเป็นลบ
    convert() {
      this.numinput *= -1;
    },
    // เปลียนศูยร์
    setto0() {
      this.numinput = 0;
      this.numinput2 = null;
      this.stat = null;
    },
    // ทักมาถามละกัน
    setval() {
      this.numinput2 = this.numinput;
      this.numinput = 0;
    },
    cal() {
      switch (this.stat) {
        case 1:
          this.numinput = parseInt(this.numinput) + parseInt(this.numinput2);
          break;
        case 2:
          this.numinput = parseInt(this.numinput2) - parseInt(this.numinput);
          break;
        case 3:
          this.numinput = parseInt(this.numinput2) * parseInt(this.numinput);
          break;
        case 4:
          if (this.numinput != 0) {
            this.numinput = parseInt(this.numinput2) / parseInt(this.numinput);
          } else {
            this.numinput = "Not div 0";
          }
          break;
        default:
          break;
      }
      this.numinput2 = null;
      this.stat = null;
    },
    clickNumber(number) {
      if (this.numinput == "0") {
        this.numinput = number;
      } else {
        this.numinput += number;
      }
    },
    deletOneLast() {
      if (this.numinput.length == 1) {
        this.numinput = "0";
      } else {
        this.numinput = this.numinput.slice(0, -1);
      }
    },
    persent() {
      this.numinput = parseInt(this.numinput) / 100;
    },
  },
};
</script>
<style>
button:hover {
  color: #fff;
  text-shadow: 0 0 7px #17df67, 0 0 10px #fff, 0 0 21px #4520ff, 0 0 42px #0fa,
    0 0 82px #0fa, 0 0 92px #0fa, 0 0 102px #0fa, 0 0 151px #0fa;
}
</style>
