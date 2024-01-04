<template>
        <div class="box_game">
            <div class="game animate__animated" :class="zoom_in_out" ref="OpenCloseNav" @animationend="finaltransition">
                <img src="../assets/bg-pentagon.svg" alt="" class="to_back">
                    <div class="images_game">
                        <div class="game1" @click="selectPaper">
                            <div class="game1-interior">
                                <img src="../assets/icon-paper.svg">
                            </div>
                        </div>
                        <div class="game2" @click="selectScissors">
                            <div class="game2-interior">
                                <img src="../assets/icon-scissors.svg">
                            </div>
                        </div>
                        <div class="game3" @click="selectRock">
                            <div class="game3-interior">
                                <img src="../assets/icon-rock.svg">
                            </div>
                        </div>
                        <div class="game4" @click="selectLizard">
                            <div class="game3-interior">
                                <img src="../assets/icon-lizard.svg">
                            </div>
                        </div>
                        <div class="game5" @click="selectSpock">
                            <div class="game3-interior">
                                <img src="../assets/icon-spock.svg">
                            </div>
                        </div>
                    </div>
            </div>
        </div>
        <div id="picked" ref="pick">
            <div class="images_game game-picked">
                <h3 class="you_picked">You picked</h3>
                <div class="circle_min circle_min1_left animate__animated" :class="fade_in" v-show="show_left">
                </div>
                <div class="circle_min circle_min2_left animate__animated" :class="fade_in" v-show="show_left">
                </div>
                <div class="circle_min circle_min3_left animate__animated" :class="fade_in" v-show="show_left">
                </div>
                <div :class="userSuperiorClass" class="game1_user animate__animated animate__bounceIn">
                    <div :class="`${userInteriorClass}-interior`">
                        <img :src="userImage" alt="user choice">
                    </div>
                </div>
            </div>
            <div class="play_again animate__animated" v-show="show_play_again" :class="zoom_in_down">
                <div class="winner_is">
                    <h1>{{ winner_lose }}</h1>
                    <button @click="play_again">PLAY AGAIN</button>
                </div>
            </div>
            <div class="images_game game-picked">
                <h3 class="the_machine_picked">The Computer picked</h3>
                <div class="circle_min circle_min1_right animate__animated" :class="fade_in" v-show="show_right">
                </div>
                <div class="circle_min circle_min2_right animate__animated" :class="fade_in" v-show="show_right">
                </div>
                <div class="circle_min circle_min3_right animate__animated" :class="fade_in" v-show="show_right">
                </div>
                <div :class="machineSuperiorClass" class="game1_machine animate__animated">
                    <div :class="`${machineInteriorClass}-interior`">
                        <img :src="machineImage">
                    </div>
                </div>
            </div>
        </div>
</template>
<script>
export default {
    name: 'ContainGame',
    data (){
        return{
            user_select: '',
            machine_select: '',
            zoom_in_out: '',
            cont: 0,
            winner_lose: '',
            fade_in: '',
            zoom_in_down: '',
            show_right: false,
            show_left: false,
            show_play_again: false,
            userSuperiorClass: "",
            userInteriorClass: "",
            userImage: "",
            machineSuperiorClass: "",
            machineInteriorClass: "",
            machineImage: ""
        }
    },
    methods: {
        selectPaper(){
            console.log("Has seleccionado papel")
            let showpicks = this.$refs.pick;
            if (this.zoom_in_out === ''){
                this.zoom_in_out = 'animate__zoomOut';
                showpicks.style.display = 'flex';
            }
            this.userSuperiorClass = "game1";
            this.userInteriorClass = "game1";
            this.userImage = require("../assets/icon-paper.svg");
            this.select_user = 'paper';
            setTimeout(() => {
                this.selectMachine()
            }, 1000)
            setTimeout(() => {
                this.winnerIs()
            }, 2000)
        },
        selectScissors(){
            console.log("Has seleccionado tijeras");
            let showpicks = this.$refs.pick;
            if (this.zoom_in_out === ''){
                this.zoom_in_out = 'animate__zoomOut';
                showpicks.style.display = 'flex';
            }
            this.userSuperiorClass = "game2";
            this.userInteriorClass = "game2";
            this.userImage = require("../assets/icon-scissors.svg");
            this.select_user = 'scissors';
            setTimeout(() => {
                this.selectMachine()
            }, 1000)
            setTimeout(() => {
                this.winnerIs()
            }, 2000)
        },
        selectRock(){
            console.log("Has seleccionado roca");
            let showpicks = this.$refs.pick;
            if (this.zoom_in_out === ''){
                this.zoom_in_out = 'animate__zoomOut';
                showpicks.style.display = 'flex';
            }
            this.userSuperiorClass = "game3";
            this.userInteriorClass = "game3";
            this.userImage = require("../assets/icon-rock.svg");
            this.select_user = 'rock';
            setTimeout(() => {
                this.selectMachine()
            }, 1000)
            setTimeout(() => {
                this.winnerIs()
            }, 2000)
        },
        selectLizard(){
            console.log("Has seleccionado lizard")
            let showpicks = this.$refs.pick;
            if (this.zoom_in_out === ''){
                this.zoom_in_out = 'animate__zoomOut';
                showpicks.style.display = 'flex';
            }
            this.userSuperiorClass = "game4";
            this.userInteriorClass = "game3";
            this.userImage = require("../assets/icon-lizard.svg");
            this.select_user = 'lizard';
            setTimeout(() => {
                this.selectMachine()
            }, 1000)
            setTimeout(() => {
                this.winnerIs()
            }, 2000)
        },
        selectSpock(){
            console.log("Has seleccionado spock")
            let showpicks = this.$refs.pick;
            if (this.zoom_in_out === ''){
                this.zoom_in_out = 'animate__zoomOut';
                showpicks.style.display = 'flex';
            }
            this.userSuperiorClass = "game5";
            this.userInteriorClass = "game3";
            this.userImage = require("../assets/icon-spock.svg");
            this.select_user = 'spock';
            setTimeout(() => {
                this.selectMachine()
            }, 1000)
            setTimeout(() => {
                this.winnerIs()
            }, 2000)
        },
        selectMachine(){
            let machineOptions = ["rock", "paper", "scissors", "lizard"];
            let randomIndex = Math.floor(Math.random() * machineOptions.length);
            let machineChoice = machineOptions[randomIndex];
            if (machineChoice == "rock"){
                let showpicks = this.$refs.pick;
                if (this.zoom_in_out === ''){
                    this.zoom_in_out = 'animate__zoomOut';
                    showpicks.style.display = 'flex';
                }
                this.machineSuperiorClass = "game3 " + "animate__bounceIn";
                this.machineInteriorClass = "game3";
                this.machineImage = require("../assets/icon-rock.svg");
                this.select_machine = 'rock';
            } else if(machineChoice == "scissors") {
                let showpicks = this.$refs.pick;
                if (this.zoom_in_out === ''){
                    this.zoom_in_out = 'animate__zoomOut';
                    showpicks.style.display = 'flex';
                }
                this.machineSuperiorClass = "game2 " + "animate__bounceIn";
                this.machineInteriorClass = "game2";
                this.machineImage = require("../assets/icon-scissors.svg");
                this.select_machine = 'scissors';
            }else if(machineChoice == "paper") {
                let showpicks = this.$refs.pick;
                if (this.zoom_in_out === ''){
                    this.zoom_in_out = 'animate__zoomOut';
                    showpicks.style.display = 'flex';
                }
                this.machineSuperiorClass = "game1 " + "animate__bounceIn";
                this.machineInteriorClass = "game1";
                this.machineImage = require("../assets/icon-paper.svg");
                this.select_machine = 'paper';
            } else if(machineChoice == "lizard") {
                let showpicks = this.$refs.pick;
                if (this.zoom_in_out === ''){
                    this.zoom_in_out = 'animate__zoomOut';
                    showpicks.style.display = 'flex';
                }
                this.machineSuperiorClass = "game4 " + "animate__bounceIn";
                this.machineInteriorClass = "game3";
                this.machineImage = require("../assets/icon-lizard.svg");
                this.select_machine = 'lizard';
            }else if(machineChoice == "spock") {
                let showpicks = this.$refs.pick;
                if (this.zoom_in_out === ''){
                    this.zoom_in_out = 'animate__zoomOut';
                    showpicks.style.display = 'flex';
                }
                this.machineSuperiorClass = "game5 " + "animate__bounceIn";
                this.machineInteriorClass = "game3";
                this.machineImage = require("../assets/icon-spock.svg");
                this.select_machine = 'spock';
            // lo mismo para el resto
            }
        },
        finaltransition(){
            let OpenCloseNav = this.$refs.OpenCloseNav;
            if (this.zoom_in_out === 'animate__zoomOut'){
                OpenCloseNav.style.display = 'none';
            }else{
                OpenCloseNav.style.display = 'flex';
            }
        },
        winnerIs(){
            let select_user = this.select_user;
            let machine_user = this.select_machine;
            let result;
            if (select_user === machine_user) {
                result = "EMPATE";
                this.winner_lose = "IT'S A DRAW";
            } else if (
                (select_user === "paper" && machine_user === "rock") ||
                (select_user === "rock" && machine_user === "scissors") ||
                (select_user === "scissors" && machine_user === "paper") ||
                (select_user === "lizard" && (machine_user === "spock" || machine_user === "paper")) ||
                (select_user === "spock" && (machine_user === "scissors" || machine_user === "rock"))
            ) {
                result = "Winner is USER";
                this.cont += 1;
                this.fade_in = "animate__fadeIn";
                this.show_left = true;
                console.log('Valor de cont antes de emitir el evento:', this.cont);
                this.winner_lose = "YOU WIN";
            } else {
                result = "Winner is MACHINE";
                this.fade_in = "animate__fadeIn";
                this.show_right = true;
                this.winner_lose = "YOU LOSE";
            }
            console.log(result);
            setTimeout(()=> {
                this.show_play_again = true
                this.zoom_in_down = 'animate__zoomInDown';
            }, 1000)
            this.$emit('update_number', this.cont);
        },
        play_again(){
            let showpicks = this.$refs.pick;
            showpicks.style.display = 'none';
            let OpenCloseNav = this.$refs.OpenCloseNav;
            OpenCloseNav.style.display = 'flex';
            this.user_select = '';
            this.machine_select = '';
            this.zoom_in_out = '';
            this.winner_lose = '';
            this.fade_in = '';
            this.zoom_in_down = '';
            this.show_right = false;
            this.show_left = false;
            this.show_play_again = false;
            this.userSuperiorClass = "";
            this.userInteriorClass = "";
            this.userImage = "";
            this.machineSuperiorClass = "";
            this.machineInteriorClass = "";
            this.machineImage = "";
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
#picked
    display: none
    align-items: center
    width: 100vw
    justify-content: center
    color: #fff
.you_picked, .the_machine_picked
    width: 50%
    display: flex
    align-items: center
    margin-top: 5%
    position: absolute
    top: 9.375vw
    justify-content: center
    letter-spacing: 0.1rem
.circle_min
    border: none
    border-radius: 100%
    width: 225px
    height: 225px
    position: absolute
.circle_min1_left
    background-color: hsla(217, 16%, 45%, 0.14)
    top: -0.6rem !important
    left: -8.8rem !important
.circle_min2_left
    background-color: hsla(217, 16%, 45%, 0.10)
    width: 300px
    height: 300px
    top: -3.1rem !important
    left: -11.2rem !important
.circle_min3_left
    background-color: hsla(217, 16%, 45%, 0.06)
    width: 375px
    height: 375px
    top: -5.3rem !important
    left: -13.7rem !important
.circle_min1_right
    background-color: hsla(217, 16%, 45%, 0.14)
    top: -0.6rem !important
    left: 21.7rem !important
.circle_min2_right
    background-color: hsla(217, 16%, 45%, 0.10)
    width: 300px
    height: 300px
    top: -2.9rem !important
    left: 19.3rem !important
.circle_min3_right
    background-color: hsla(217, 16%, 45%, 0.06)
    width: 375px
    height: 375px
    top: -5.2rem !important
    left: 17rem !important
.the_machine_picked
    right: -7.5vw !important
    top: -5vw !important
.you_picked
    left: -9vw !important
    top: -5vw !important
.game-picked
    width: 30vw
    display: flex
    align-items: center
    margin-top: 5vw
    position: absolute
    top: 13.8889vw
    justify-content: center
    .game1, .game2, .game3, .game4, .game5
        top: 0vw
        bottom: 0vw
        left: 0vw
        right: 0vw
        cursor: inherit
        transition: none
        &:hover
            transform: none
    .game1_user
        top: 1.75vw !important
        left: -6.4vw !important
    .game1_machine
        top: 1.75vw !important
        left: 25.5vw !important
.play_again
    display: flex
    align-items: center
    justify-content: center
    flex-direction: column
    position: absolute
    top: 22.22vw
    .winner_is
        display: flex
        align-items: center
        justify-content: center
        flex-direction: column
        h1
            font-size: 2.4rem
            letter-spacing: 0.1rem
            margin-bottom: 2%
        button
            margin-top: 5%
            border: none
            background: #fff
            color: hsl(229, 25%, 31%)
            width: 8.5rem
            height: 2rem
            border-radius: 5px
            font-weight: 600
            letter-spacing: 0.1rem
            transition: ease-in-out
            transition-duration: 0.2s
            cursor: pointer
            &:hover
                transform: scale(1.1)
.box_game
    display: flex
    align-items: center
    justify-content: center
    margin-top: 2%
.game
    display: flex
    align-items: center
    justify-content: center
    width: 100vw
    height: 32vw
    img
        width: 410px
.images_game
    position: absolute
.game1, .game2, .game3, .game4, .game5
    position: absolute
    cursor: pointer
    content: ""
    height: 150px
    width: 150px
    background-image: linear-gradient(to right, hsl(230, 89%, 62%), hsl(230, 89%, 65%))
    border-radius: 100%
    top: -130px
    right: -260px
    transition: ease-in-out
    transition-duration: 0.2s
    &:hover
        transform: scale(1.1)
.game1-interior, .game2-interior, .game3-interior, game4-interior, game5-interior
    position: relative
    height: 110px
    width: 110px
    top: 14%
    left: 13%
    background-color: #fff
    z-index: 4
    border-radius: 50%
    display: flex
    align-items: center
    justify-content: center
    box-shadow: inset 0 10px 15px -10px rgba(0, 0, 0, 0.5), inset 0 -10px 15px -10px rgba(0, 0, 0, 0.5)
    img
        width: 50%
.game2
    background-image: linear-gradient(to right, hsl(39, 89%, 49%), hsl(40, 84%, 53%))
    top: -250px
    right: -80px
    &:hover
        transform: scale(1.1)
.game3
    background-image: linear-gradient(to right, hsl(349, 71%, 52%), hsl(349, 70%, 56%))
    top: 90px
    left: 40px
    &:hover
        transform: scale(1.1)
.game4
    background-image: linear-gradient(to right, hsl(261, 73%, 60%), hsl(261, 72%, 63%))
    top: 90px
    left: -190px
    &:hover
        transform: scale(1.1)
.game5
    background-image: linear-gradient(to right, hsl(189, 59%, 53%), hsl(189, 58%, 57%))
    top: -130px
    left: -255px
    &:hover
        transform: scale(1.1)
</style>