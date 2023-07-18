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
      arr:["s","sa",5,7],
      car:{
        name: "kuruma",
        speed:"hayai",
        price:"takai"
      }
    }
  }
}
</script>

<template>
  <header>
    <button @click="isShow = !isShow"> toggle </button>
    <img v-if="isShow" alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
    <div class="wrapper">
      <HelloWorld v-for="item in arr" :msg="item" />
    </div>
    <ul>
      <li v-for="item in arr">
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
