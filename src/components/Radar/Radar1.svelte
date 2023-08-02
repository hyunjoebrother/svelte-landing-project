<div class="container">
  <ul class="radar-wrapper">
    <li />
    <li />
    <li />
    <li />
    <li />
    <li />
    <li />
    <li />
    <div class="target" id="target1"></div>
    <div class="target" id="target2"></div>
  </ul>
</div>

<style>
  .container {
    width: 500px;
    height: 800px;
    background-color: #000;
  }

  .radar-wrapper {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    margin: 0;
    padding: 0;
    width: 440px;
    height: 440px;
    border-radius: 50%;
    border: 8px solid #2f2929;
    background: rgb(255,164,252);
background: linear-gradient(208deg, rgba(255,164,252,1) 3%, rgba(194,87,227,1) 47%, rgba(229,144,255,1) 86%);
  }

  /* 오브젝트 표시 */
.radar-wrapper  .target {
    content: "";
    position: absolute;
    top: 80%;
    left: 45%;
    width: 8px;
    height: 12px;
    background: red;
    border-radius: 50%;
    filter: blur(3px);
    /* border: solid 1px #fff; */
    /* animation: scale 3s linear infinite; */
    animation: glow 1s linear infinite;
    cursor: pointer;
}
 
.radar-wrapper  .target:hover {
    transform: scale(2);
}

#target1 {
    top: 80%;
    left: 45%;
    width: 8px;
    height: 12px;
}

#target2 {
    top: 60%;
    left: 65%;
    width: 8px;
    height: 12px;
}

  /* .radar-wrapper::after {
    content: "";
    position: absolute;
    
    background: yellow;
    border-radius: 50%;
    filter: blur(3px);
    animation: glow 1s linear infinite;
  } */

  .radar-wrapper li:nth-child(1),
  .radar-wrapper li:nth-child(2),
  .radar-wrapper li:nth-child(3),
  .radar-wrapper li:nth-child(4) {
    list-style: none;
    position: absolute;
    top: 50%;
    height: 1px;
    width: 100%;
    background: rgb(150, 33, 127);
    border-radius: 50%;
  }

  .radar-wrapper li:nth-child(2) {
    transform: rotate(90deg);
  }

  .radar-wrapper li:nth-child(3) {
    transform: rotate(45deg);
  }

  .radar-wrapper li:nth-child(4) {
    transform: rotate(-45deg);
  }

  /* 좌표선 */
  .radar-wrapper li:nth-child(5),
  .radar-wrapper li:nth-child(6),
  .radar-wrapper li:nth-child(7) {
    list-style: none;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    border: 1px solid #8d0799;
    background: transparent;
    border-radius: 50%;
  }

  /* 원형선 */
  .radar-wrapper li:nth-child(5) {
    width: 120px;
    height: 120px;
  }

  .radar-wrapper li:nth-child(6) {
    width: 240px;
    height: 240px;
  }

  .radar-wrapper li:nth-child(7) {
    width: 360px;
    height: 360px;
  }

  .radar-wrapper li:nth-child(8) {
    list-style: none;
    position: absolute;
    top: 50%;
    left: 50%;
    width: 6px;
    height: 220px;
    transform-origin: top left;
    background: linear-gradient(
      45deg,
      rgb(188, 55, 177) 0%,
      transparent 70%
    ); /* 레이더 감지선 */
    animation: animate 2s linear infinite;
  }

  @keyframes scale {
    0% {
      transform: scale(0);
    }
    50% {
      transform: scale(1.2);
    }
    51%,
    100% {
      opacity: 0;
    }
  }

  @keyframes glow {
    0% {
      opacity: 0;
    }
    50% {
      opacity: 1;
    }
    100% {
      opacity: 0;
    }
  }

  @keyframes animate {
    0% {
      transform-origin: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
</style>
