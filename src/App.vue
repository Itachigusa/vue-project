<script>
import Card from './components/Card.vue'

export default{
  components: {
    Card
  },
  data(){
    return {
      title:"神経衰弱",

      turnCount:0,
      currentState:0,

      symbols:["♠","♣","♥","♦"],
      values:["1","2","3","4","5","6","7","8","9","10","J","Q","K"],

      firstValue:"",
      firstIndex:0
    }
  },
  methods:{
    openCard(value, index)
    {
      if(this.currentState == 2
      || this.currentState == 3)
      {
        return;
      }

      if(this.currentState == 0)
      {
        this.firstValue = value;
        this.firstIndex = index;

        this.currentState = 1;
      }
      else if(this.currentState == 1)
      {
        if(this.check(value))
        {
          this.currentState = 2;
            setTimeout(() => {
              this.currentState = 0;

              this.firstIndex = 0;
              this.firstValue = "";
            }, 2000);
        }
        else
        {
          this.currentState = 3;
            setTimeout(() => {
              this.$refs.cards[this.firstIndex].setOpenState(false);
              this.$refs.cards[index].setOpenState(false);

              this.currentState = 0;

              this.firstIndex = 0;
              this.firstValue = "";
            }, 2000);
        }
      }

      this.$refs.cards[index].setOpenState(true);
    },
    check(value)
    {
      return this.firstValue == value;
    }
  },
  computed:{
    list()
    {
      var temp = [];
      
      for (let i = 0; i < 8; i++) 
      {
        var symbol = this.symbols[Math.floor(Math.random()*this.symbols.length)];
        var value = this.values[Math.floor(Math.random()*this.values.length)];
        temp.push(symbol+value);
        temp.push(symbol+value);
      }

      for (let i = temp.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [temp[i], temp[j]] = [temp[j], temp[i]];
      }
      return temp;
    }
  }
}
</script>

<template>
  <header>
    <h1>{{title}}</h1>
  </header>
  <main>
    <div v-if="currentState == 0">
      Select 1st Card
    </div>
    <div v-if="currentState == 1">
      Select 2nd Card
    </div>
    <div v-if="currentState == 2">
      Success
    </div>
    <div v-if="currentState == 3">
      Failed
    </div>
    <div v-for="i in 16">
      <Card :index=i-1  :value = list[i-1] ref = "cards" @card-open="openCard"/>
    </div>
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
