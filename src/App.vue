<template>
  <div>
    <header class="header_pc header" v-if="$mq === 'pc'">
        <div v-if="$mq === 'pc'">
            <div class="title_pc title">野鳥タイピングゲーム</div>
        </div>
    </header>
    <header class="header_sp header" v-if="$mq === 'sp'">
        <div v-if="$mq === 'sp'">
            <div class="title_sp title">野鳥タイピングゲーム</div>         
        </div>        
    </header>  
    <typingtop v-show="currentComponent === 'typingtop'" @gameStart="gameStart"></typingtop>
    <typingstart v-show="currentComponent === 'typingstart'" :kata="kata" :roman="roman" :PassSec="PassSec" :num="num" @RandomWord="RandomWord" @SendSumCount="SendSumCount2" @TypedAnimal="TypedAnimal" @MissCount="MissCount" ref="foo"></typingstart>
    <typingresult v-show="currentComponent === 'typingresult'" :sumcount="sumcount" :typing="typing" :Typed_animal="Typed_animal" :misscount="misscount"></typingresult>
  </div>
</template>

<script>
import typingstart from './components/TypingStart.vue'
import typingresult from './components/TypingResult.vue'
import typingtop from './components/TypingTop.vue'
import  { kanaToRoman } from '/Users/hazuki/vue_projects/birds_typing/src/kanaToRoman.js'

export default { 
    data() {
        return {
            currentComponent: "typingtop",
            key: '',
            PassSec: 30, //ゲームの制限時間
            typing : [{'name': 'メジロ', 'img': '@/assets/0.jpg'}, 
                {'name': 'ヒドリガモ', 'img': '@/assets/1.jpg'},
                {'name': 'エナガ', 'img': '@/assets/2.jpg'}, 
                {'name': 'カワセミ', 'img': '@/assets/3.jpg'}, 
                {'name': 'キセキレイ', 'img': '@/assets/4.jpg'}, 
                {'name': 'ツグミ', 'img': '@/assets/5.jpg'}, 
                {'name': 'モズ', 'img': '@/assets/6.jpg'}, 
                {'name': 'シジュウカラ', 'img': '@/assets/7.jpg'}, 
                {'name': 'ドバト', 'img': '@/assets/8.jpg'}, 
                {'name': 'シメ', 'img': '@/assets/9.jpg'}, 
                {'name': 'オオルリ', 'img': '@/assets/10.jpg'}, 
                {'name': 'キンクロハジロ', 'img': '@/assets/11.jpg'}, 
                {'name': 'カワラヒワ', 'img': '@/assets/12.jpg'}, 
                {'name': 'アカゲラ', 'img': '@/assets/13.jpg'}, 
                {'name': 'オオバン', 'img': '@/assets/14.jpg'}, 
                {'name': 'ジョウビタキオス', 'img': '@/assets/15.jpg'}, 
                {'name': 'ジョウビタキメス', 'img': '@/assets/16.jpg'}, 
                {'name': 'シロハラ', 'img': '@/assets/17.jpg'},
                {'name': 'セキレイ', 'img': '@/assets/18.jpg'},
                {'name': 'ツバメのヒナ', 'img': '@/assets/19.jpg'},
                {'name': 'ハッカチョウ', 'img': '@/assets/20.jpg'},
                ]
            ,kata: "",
            roman: "",
            img: "",
            num: 0,
            sumcount: 0,
            misscount: 0,
            Typed_animal: "",
            randoms : [1],
            }
    },
    mounted() {
        document.addEventListener('keydown', this.gameStart);
    },
    methods: {
        gameStart() {
        if(event.key === "Enter" && this.currentComponent === "typingtop") {  
            this.currentComponent = "typingstart";
            var tmp = this;
            const timerID = setInterval(function(){
                tmp.PassSec -= 1;
                if(tmp.PassSec === 0) {
                    tmp.currentComponent = "typingresult";
                    clearInterval(timerID); 
                }
            },1000); 
            this.RandomWord();
        } else {
                this.$refs.foo.Judge(event.key);
            }
        },
        RandomWord() {
            this.random_num = Math.floor(Math.random() * this.typing.length);
            if(!this.randoms.includes(this.random_num)){
                this.kata = this.typing[this.random_num].name;
                this.roman = kanaToRoman(this.kata,"hepburn",{bmp : false,});
                this.img = this.typing[this.random_num].img;
                this.num = this.random_num;
                this.randoms.push(this.random_num);
            } else {
                this.RandomWord();
            }
        },
        SendSumCount2(count) {
            this.sumcount = count;
        },
        TypedAnimal(Typed_Animal) {
            this.Typed_animal = Typed_Animal;
        },
        MissCount(misscount) {
            this.misscount = misscount;
        }
    },
    components: {
        typingstart,
        typingresult,
        typingtop,
    },
}

</script>

<style>
*{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

template{margin:0px;}
#app {
    font-family: 'Kosugi Maru', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}

body {
    background-color: #e7f4f1;
}

.header {
    background-color: #50C1E9;
    align-items: center;
    margin-bottom: 30px;
}

.header_pc {
    height: 60px;
    padding: 15px;
}

.header_sp {
    height: 40px;
    padding: 10px;    
}

.title {
    color: #ffffff;
    text-align: left;
}

.title_pc {
    font-size: 30px;
    height: 40px;
}

.title_sp {
    font-size: 20px;
    height: 20px;
}


</style>