<script context="module">
  import { onMount } from "svelte";

  // 빗방울 천둥 클래스
  export class RainThunder {
    constructor() {
      this.opacity = 0;
    }

    draw(ctx) {
      const gradient = ctx.createLinearGradient(0, 0, 0, innerHeight);
      gradient.addColorStop(0, `rgba(66,84,99,${this.opacity})`);
      gradient.addColorStop(1, `rgba(18,23,27,${this.opacity})`);
      ctx.fillStyle = gradient;
      ctx.fllRect(0, 0, innerWidth, innerHeight);
    }

    animate(ctx) {
        if(this.opacity < 0)
        return this.opacity -= 0.005
      this.draw(ctx);
    }
  }
</script>
