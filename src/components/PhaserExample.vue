<template>
  <ion-phaser
    v-bind:game.prop='game'
    v-bind:initialize.prop='initialize'
  />
</template>

<script>
import Phaser from "phaser"

export default {
  name: 'PhaserExample',
  data() {
    return {
      initialize: false,
      game: {
        type: Phaser.AUTO,
        width: 800,
        height: 600,
        physics: {
          default: 'arcade',
          arcade: {
            gravity: { y: 200 }
          }
        },
        scene: {
          preload() {
            this.load.setBaseURL('http://labs.phaser.io');

            this.load.image('sky', 'assets/skies/space3.png');
            this.load.image('logo', 'assets/sprites/phaser3-logo.png');
            this.load.image('red', 'assets/particles/red.png');
          },
          create () {
            this.add.image(400, 300, 'sky');

            let particles = this.add.particles('red');

            let emitter = particles.createEmitter({
                speed: 100,
                scale: { start: 1, end: 0 },
                blendMode: 'ADD'
            });

            let logo = this.physics.add.image(400, 100, 'logo');

            logo.setVelocity(100, 200);
            logo.setBounce(1, 1);
            logo.setCollideWorldBounds(true);

            emitter.startFollow(logo);
          }
        }
      }
    }
  },
  methods: {
    initializeGame() {
      this.initialize = true
    }
  },
  created() {
    this.initializeGame()
  }
}
</script>
