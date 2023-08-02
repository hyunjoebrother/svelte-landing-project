<script>
  import { onMount } from "svelte";
  import { Rain } from "./Rain.svelte";
  import RainThunder from "./RainThunder.svelte";


  //   let total = 50;
  let total;
  let rains = [];
  let drops = [];
  let thunder;
  let mouse = {x: 0, y: 0, isActive: false}

  // 초기화
  onMount(() => {
    const canvas = document.getElementById("canvas");
    const ctx = canvas.getContext("2d");
    canvas.width = innerWidth;
    canvas.height = innerHeight;


    total = Math.floor((innerWidth * innerHeight) / 15000);
    rains = []
    drops = []
    // thunder = new RainThunder()

    for (let i = 0; i < total; i++) {
      const x = randomBetween(0, innerWidth);
      const y = randomBetween(0, innerHeight);
      const velocity = {
        // x: randomBetween(-1, 1),
        y: randomBetween(13, 18),
      };
      rains.push(new Rain(x, y, velocity));
    }

    function drawRaindrops(ctx) {
    //  if (Math.random() < 0.0007) thunder.opacity = 1;
    //   thunder.animate(ctx);
      // Rain 클래스
      rains.forEach((rain) => {
        rain.animate(ctx);
      });

      // RainDrop 클래스
      drops.forEach((drop, index) => {
        drop.animate(ctx);
        if (drop.y > innerHeight) {
          drops.splice(index, 1);
        }
      });
    }

    function animate() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      drawRaindrops(ctx);

      // 매 프레임마다 지우고 그리고를 한다
      requestAnimationFrame(animate);
    }

    animate();

    canvas.addEventListener('mouseenter', ()=> mouse.isActive = true)
    canvas.addEventListener('mouseleave', ()=> mouse.isActive = false)
    canvas.addEventListener('mousemove', e => {
        mouse.x = e.clientX;
        mouse.y = e.clientY;
    })
  });

  const randomBetween = (min, max) => {
    return Math.random() * (max - min + 1) + min;
  };
</script>

<canvas id="canvas" />

<style>
  canvas {
    width: 100%;
    height: 600px;
    background: linear-gradient(to bottom, #222b33, #12171b);
  }
</style>
