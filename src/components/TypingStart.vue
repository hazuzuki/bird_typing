<template>
  <div class="content">
    <p>ただいまのカウント:{{ count }}</p>
    <p>残り時間:{{PassSec}}</p>
    <img class="animal-img" :src="require(`@/assets/${num}.jpg`)">
    <p>{{ kata }}</p>
    <p class="type-word"><span class="done">{{ pressed }}</span>{{ roman2 }}</p>
  </div>
</template>

<script>

export default {
    devServer: {
    Host: 'localhost'
    },
    props: ["kata", "roman", "PassSec", "num"],
  data: function() {
    return{
      audio: new Audio(require('@/assets/Quiz-Correct_Answer02-1.mp3')),
      buzzeraudio: new Audio(require('@/assets/Quiz-Wrong_Buzzer02-1.mp3')),
      count: 0,
      misscount: 0,
      roman2: this.roman,
      pressed: "",
      typed_animal: [],
      }
  },
  methods: {
    Judge: function(key) {
      if(this.roman2.split('')[0] === key) {
        this.roman2 = this.roman2.slice(1);
        this.pressed += key;
        if(this.roman2.length == 0) {
          this.$emit('RandomWord');
          this.pressed = "";
          this.roman2 = this.roman;
          this.count += 1;
          this.audio.play();
          this.typed_animal.push(this.num);
          this.SendSumCount();
        }
      } else {
        this.buzzeraudio.play();
        this.misscount += 1;
      }
      return true
  },
  SendSumCount: function() {
     this.$emit('SendSumCount', this.count);
     this.$emit('TypedAnimal', this.typed_animal);
     this.$emit('MissCount', this.misscount);


  },
  },
watch: {
      roman: function(){
        this.roman2 = this.roman;
      }
},
  name: 'App',
}
</script>

<style>
  button {
    border: 3px solid;
  }

  .done {
    color: gray;
  }

  .type-word {
    color: black;
  }

  p {
    font-size: 30px;
  }

.animal-img {
  width: 350px;
  height: 350px;
  object-fit: cover; 
  padding: 10px;
}

</style>
