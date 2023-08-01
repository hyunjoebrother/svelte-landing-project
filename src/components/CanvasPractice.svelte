<script>
  import { onMount } from "svelte";

  let canvas;
  let canvas2;

  // 컴포넌트가 DOM(객체 모델)에 추가될 때 호출된다
  onMount(() => {
    const ctx = canvas.getContext("2d");
    const centerX = canvas.width / 2;
    const centerY = canvas.height / 2;
    const circleCount = 8;
    const circleRadius = 20;
    const circleGap = 10;
    const verticalLines = 12;
    const lineLength = 90;

    // 마우스 이벤트
    const canvas2 = document.getElementById("canvas-draw");
    const ctx2= canvas2.getContext("2d");
    canvas2.addEventListener(
      "mousedown",
      function (e) {
        mDown(e);
      },
      false
    );
    canvas2.addEventListener(
      "mousemove",
      function (e) {
        mMove(e);
      },
      false
    );
    canvas2.addEventListener(
      "mouseup",
      function (e) {
        mUp(e);
      },
      false
    );
    canvas2.addEventListener(
      "mouseout",
      function (e) {
        mOut(e);
      },
      false
    );

      // 처음 마우스 좌표
  var stX = 0;
  var stY = 0;

  // 마우스를 캔버스에서 움직였을 때 그림 그리기 여부
  var drag = false;

  // 커스텀
  ctx2.strokeStyle = 'red';
  ctx2.lineWidth = 1.2;
  ctx2.lineCap = 'round'

  // 마우스 버튼을 누르고 있을 때 현재 마우스 좌표를 담음
  function mDown(e) {
    stX = e.offsetX;
    stY = e.offsetY;
    drag = true;
    console.log(stX, stY, drag);
  }

  // 마우스 움직일 때
  function mMove(e) {
    if (!drag) {
      return;
    }

    var nowX = e.offsetX;
    var nowY = e.offsetY;
    canvasDraw(nowX, nowY); // 실질적으로 그리는 부분
    stX = nowX;
    stY = nowY;
  }

  function canvasDraw(currentX, currentY) {
    // 마우스 누르고 움직일 때마다 시작점 재지정
    ctx2.beginPath(); // 초기화
    ctx2.moveTo(stX, stY); // 출발점을 좌표로
    // 마우스 시작점부터 현재 점까지 라인그리기
    ctx2.lineTo(currentX, currentY); // 도착점을 좌표로
    ctx2.stroke();
  }

  // 마우스 떼었을 때 그리기 중지
  function mUp(e) {
    drag = false;
  }

  // 마우스가 캔버스 밖으로 벗어날 때 그리기 중지
  function mOut(e) {
    drag = false;
  }

    // 원형판 그리기
    for (let i = 0; i < circleCount; i++) {
      const radius = circleRadius + i * circleGap;
      ctx.beginPath();
      ctx.arc(centerX, centerY, radius, 0, 2 * Math.PI);
      ctx.stroke();
    }
    // 세로줄 그리기
    const angleStep = (2 * Math.PI) / verticalLines;
    for (let i = 0; i < verticalLines; i++) {
      const angle = i * angleStep;
      const x = centerX + Math.cos(angle) * lineLength;
      const y = centerY + Math.sin(angle) * lineLength;
      ctx.beginPath();
      ctx.moveTo(centerX, centerY);
      ctx.lineTo(x, y);
      ctx.stroke();
    }

    // object 띄우기
    ctx.fillRect(50, 100, 10, 10);
  });
</script>

<div class="canvas-container">
    <canvas bind:this={canvas2} id="canvas-draw" />
  <canvas bind:this={canvas} />
</div>

<style>
  .canvas-container {
    position: relative;
    width: 100%;
    height: 100%;
  }

  canvas {
    width: 400px;
    height: 400px;
    background-color: #fff;
  }
</style>
