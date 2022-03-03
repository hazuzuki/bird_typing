<template>
    <div class="contents">
        <div class="content">
            <img src="@/assets/bird_watching.png" alt="バードウオッチングの画像" width="40%" height="40%">
        </div>
        <div>
            <div v-if="$mq === 'pc'">
                <div class="content start"><span class="emphasis_color">Enter</span>を押してゲーム開始</div>
                <div class="content play">
                    <img src="@/assets/keijiban.png" alt="掲示板" width="700px" height="350px">
                    <div class="how_to_play">
                            <h2>遊び方</h2>
                            <p>あなたは、お散歩にでかけました。今日は、どんな野鳥に出会えるかな。</p>
                            <ol>
                                <li>Enterを押すとゲームが開始します。</li>
                                <li>制限時間は、10秒です。制限時間内にたくさんの野鳥を見つけてください。</li>
                                <li>ゲーム終了後、見つけた野鳥を一覧で確認できます。</li>
                            </ol>
                    </div>
                </div>
            </div>
            <div v-if="$mq === 'sp'">
                <div class="content">
                    訪問ありがとうございます。<br>
                    こちらは、パソコン専用のサイトです。<br>
                    パソコンからアクセスしてください。<br>
                </div>
                <!-- <div class="content video">
                    <div class="video-description">▽ゲームのプレイ動画はこちら</div> 
                    <iframe width="100%" src="https://www.youtube.com/embed/3JgsTd0hHKE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                </div> -->
            </div>
        </div>
        <div class="content change_log">
            <div class="log">
                <h2>更新履歴</h2>
                <dl>
                <dt>2022.3.2</dt>
                <dd>野鳥タイピングゲームをリリースしました。</dd>
                </dl>
            </div>
            <img src="@/assets/animal_chara_mogura_kouji_ana.png" alt="掲示板" width="20%" height="20%">
        </div>
        <div class="content profile">
            <h2>ゲームについて</h2>
                <div>
                    <p>ゲームのご意見・ご感想は下記のtwitterまで！</p>
                    <a target="_blank" href="https://twitter.com/animal_typ"><img class="icon" src="@/assets/twitter_icon.png" alt="アイコン" width="80px" height="80px"></a>
                </div>
        </div>
        <div class="content anothor_game">
            <h2>関連のゲーム</h2>
                <div>
                    <p>こちらも遊んでみてね</p>
                    <div><img class="icon" src="@/assets/animal_typ.png" alt="アイコン" width="20%" height="20%"></div>
                    <a class="btn btn-small" target="_blank" href="https://hazuzuki.github.io/animal_typing/">動物タイピングゲーム</a>
                </div>
        </div>
    </div>
</template>

<script>


</script>

<style>
.contents {
    padding: 20px;
    text-align: center;
}

.content {
    margin-bottom: 50px;
}

h2 {
    font-size: 20px !important;
    margin-bottom: 10px; 
}


.start {
    font-size: 30px;
}

.emphasis_color {
    color:  #50C1E9;
}

.video {
    margin-top: 30px;
    padding: 15px;
    background-color: #a2ce82;
}

.video-description {
    color: #000000;
    margin-bottom: 10px;
    text-align: left;
}

p {
    font-size: 15px !important;
    margin-bottom: 10px;
}


.play {
    position: relative;
    width: 700px;
    height: 410px;
    margin: 0 auto;
}

.play > img {
    position: absolute;
    right: 0px;
}

.how_to_play {
    width: 400px;
    margin: 0 auto;    
    display: inline-block;
    position: absolute;
    top: 50px;
    left: 150px;
    font-size: 15px !important;

}

.how_to_play > p {
    font-size: 15px !important;
    margin-bottom: 10px;
    text-align: left;
    line-height: 20px;
}

.how_to_play > ol > li {
    text-align: left;
    padding-top: 3px;
    padding-bottom: 3px;
    list-style-position: inside;
    margin-left: 0.9em;
    text-indent: -0.9em;
}

.change_log > .log {
    background-color: #ffffff;
    padding: 20px;
    display: inline-block;
    border-radius: 15px;
    position: relative;
    margin-bottom: 10px;
}

.change_log > .log ::before {
  content: "";
  position: absolute;
  top: 100%;
  left: 50%;
  margin-left: -15px;
  border: 15px solid transparent;
  border-top: 15px solid #ffffff;
}

.change_log > .content > dl {
    text-align: left;
    line-height: 1.5em;
}

.change_log > .content > dl> dt {
    float: left;
}

.change_log > .content > dl > dd {
    margin-left: 80px;
}

.change_log  > img {
    display: block;
    margin: 0 auto;
}

.anothor_game {
    margin-bottom: 150px;
    display: inline-block;
}

.game {
    background-color: #ffffff;
    padding: 20px 0px;
    border-radius: 15px;
}

.game > img {
    margin-bottom: 10px;
}









</style>