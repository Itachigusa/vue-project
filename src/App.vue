<script>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'

export default{
  components: {
    HelloWorld,
    TheWelcome
  },
  data(){
    return {
      hoge:"igyo",
      isShow:true,
      listArr:[0, 1, 3],
      arr:[0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610],
      car:{
        name: "kuruma",
        speed:"hayai",
        price:"takai"
      },
      counter:0
    }
  },
  methods:{
    toggleShow(){
      this.isShow = !this.isShow;
      console.log(this.isShow);
    },
    reset(){
      this.counter = 0;
    },
    incrementX(add){
      this.counter = this.counter + add;
      console.log(this.counter);
    }
  }
}
</script>

<template>
  <header>
    <p>{{counter}}</p>
    <button @click="reset"> reset </button>
    <button @click="incrementX(50)"> +50 </button>
    <button @click="toggleShow"> toggle </button>
    <img v-if="isShow" alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <button v-for="item in arr" @click="incrementX(item)">{{item}}</button>

    <div class="wrapper">
      <HelloWorld v-for="item in listArr" :msg="item" />
    </div>
    <ul>
      <li v-for="item in listArr">
        {{item}}
      </li>
    </ul>
    <ul>
      <li>{{car.name}}</li>
      <li>{{car.speed}}</li>
      <li>{{car.price}}</li>
    </ul>
    <p>{{car}}</p>
  </header>
  <main>
    <TheWelcome />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
