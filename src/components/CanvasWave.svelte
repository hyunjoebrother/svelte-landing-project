<script>
  import { onMount } from "svelte";
  import Wave from "./Wave.svelte";

  let canvas;
  let ctx;

  // 캔버스 크기
  let stageWidth;
  let stageHeight;

  // 웨이브 객체 생성
  let wave;

  // 초기화 함수
  function init() {
    canvas = document.createElement("canvas"); // 캔버스 엘리먼트 생성
    ctx = canvas.getContext("2d"); // 2D 컨텍스트 얻기
    document.body.appendChild(canvas);
    // 웨이브 객체 생성
    wave = new Wave({ stageWidth, stageHeight });
  }

  // 사이즈가 변할 때 실행될 콜백
  function resize() {
    stageWidth = document.body.clientWidth;
    stageHeight = document.body.clientHeight;
    canvas.width = stageWidth * 2;
    canvas.height = stageHeight * 2;
    // 캔버스에서 1개의 픽셀이 차지할 크기를 정함
    ctx.scale(2, 2);
    // 웨이브에도 리사이즈가 적용 되도록 설정
    wave.resize(stageWidth, stageHeight);
  }

  function animate(t) {
    // 지정된 사각 영역을 rgba(0, 0, 0, 0)의 색상으로 만듦
    ctx.clearRect(0, 0, stageWidth, stageHeight);
    wave.draw(ctx); // 애니메이션이 실행되면 웨이브가 그려지도록 설정
    requestAnimationFrame(animate); // 애니메이션 프레임 요청
  }

  // 컴포넌트가 DOM(객체 모델)에 추가될 때 호출된다
  onMount(() => {
    init(); // 초기화 함수 실행
    window.addEventListener("resize", resize);
    resize(); // 최초 사이즈 설정
    requestAnimationFrame(animate); // 애니메이션 프레임 요청
  });
</script>

<div class="canvas-container">
  <Wave {stageWidth} {stageHeight} />
</div>
<style>
  .canvas-container {
    width: 100%;
    height: 500px;
    background-color: antiquewhite;
  }
</style>
