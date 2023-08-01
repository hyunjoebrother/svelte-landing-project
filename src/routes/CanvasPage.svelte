<script>
  import CanvasPractice from "../components/CanvasPractice.svelte";
  import CanvasWave from "../components/CanvasWave.svelte";
</script>

<!-- Scroll 애니메이션 없는 Canvas 페이지 -->
<div class="container">
  <CanvasWave />
  <CanvasPractice />
</div>

<style>
  .container {
    top: 0;
    width: 100%;
    height: 100%;
    background-color: #fff;
  }
</style>
