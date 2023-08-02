<script context="module">
  import { onMount } from "svelte";
  import RainDrop from "./RainDrop.svelte";

  let mouse = {x: 0, y: 0, isActive: false}

  // 빗줄기 클래스
  export class Rain {
    constructor(x, y, velocity) {
      this.x = x;
      this.y = y;
      this.velocity = velocity;
    }

    draw(ctx) {
      const { x, y, velocity } = this;
      ctx.beginPath();
      ctx.moveTo(x, y);
      ctx.lineTo(x + velocity.x * 2, y + velocity.y * 2);
      ctx.strokeStyle = "#8899a6";
      ctx.lineWidth = 1.3;
      ctx.stroke();
    }

    // Drop 추가
    splash(ctx) {
      let drops = [];
      for (let i = 0; i < 3; i++) {
        const velocity = {
          x: -this.velocity.x + randomBetween(-2, 2),
          y: -this.velocity.y + randomBetween(5, 10),
        };
        drops.push(new RainDrop(this.x, innerHeight, velocity));
      }
    }

    animate(ctx) {
      if (this.y > innerHeight) {
        this.x = randomBetween(-innerWidth*0.2, innerWidth*1.2);
        this.y = -20;
      }

      // 마우스 이벤트 추가
      this.velocity.x = mouse.isActive
        ? randomBetween(-1, 1) + (-innerWidth / 2 + mouse.x) / 150
        : randomBetween(-1, 1);

      // 속력 추가
      this.x += this.velocity.x;
      this.y += this.velocity.y;

      this.draw(ctx);
    }
  }


  const randomBetween = (min, max) => {
    return Math.random() * (max - min + 1) + min;
  };
</script>
