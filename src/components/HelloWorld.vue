<template>
  <ion-phaser
    v-bind:game.prop='game'
    v-bind:initialize.prop='initialize'
  />
</template>

<script>
import Phaser from "phaser"

export default {
  name: 'HelloWorld',
  data() {
    return {
      initialize: false,
      game: {
        width: "50%",
        height: "50%",
        type: Phaser.AUTO,
        scene: {
          init() {
            this.cameras.main.setBackgroundColor("#aaddee");
          },
          create() {
            this.helloWorld = this.add.text(
              this.cameras.main.centerX,
              this.cameras.main.centerY,
              "Hello World",
              { font: "40px Arial",  fill: "#ffffff" }
            );
            this.helloWorld.setOrigin(0.5);
          },
          update() {
            this.helloWorld.angle += 1;
          }
        }
      }
    }
  },
  methods: {
    initializeGame() {
      this.initialize = true;
    }
  },
  created() {
    this.initializeGame()
  }
}
</script>
