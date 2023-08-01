<script>
  import Point from "./Point.svelte";

  // export let color = '#ff0000';
  export let stageWidth;
  export let stageHeight;

  let centerX;
  let centerY;
  let point;

  function init() {
    centerX = stageWidth / 2;
    centerY = stageHeight / 2;
    point = new Point({ centerX, centerY });
  }

  function resize(newStageWidth, newStageHeight) {
    stageWidth = newStageWidth;
    stageHeight = newStageHeight;
    init();
  }

  function draw(ctx) {
    ctx.beginPath();
    ctx.arc(point.x, point.y, 30, 0, 2 * Math.PI);
    ctx.fillStyle = "#ff0000";
    ctx.fill();
    ctx.closePath();

    point.update();
  }
</script>

<style>
  /* Add any necessary styles here */
</style>
