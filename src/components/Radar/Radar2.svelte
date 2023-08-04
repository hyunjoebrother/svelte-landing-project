<script>
  let personLocation = [];
  function getRandomPercentage() {
    return Math.floor(Math.random() * 98) + 1;
  }

  for (let i = 0; i < 30; i++) {
    personLocation.push({
      left: getRandomPercentage(),
      top: getRandomPercentage(),
    });
  }

  // 레이더와 타겟 교차 여부를 확인하는 함수
  function checkIntersection(target, radar) {
    const targetRect = target.getBoundingClientRect();
    const radarRect = radar.getBoundingClientRect();

    const targetCenterX = targetRect.left + targetRect.width / 2;
    const targetCenterY = targetRect.top + targetRect.height / 2;

    const radarCenterX = radarRect.left + radarRect.width / 2;
    const radarCenterY = radarRect.top + radarRect.height / 2;

    const distanceX = Math.abs(targetCenterX - radarCenterX);
    const distanceY = Math.abs(targetCenterY - radarCenterY);

    const isIntersect =
      distanceX + 70 <= targetRect.width / 2 + radarRect.width / 2 &&
      distanceY + 70 <= targetRect.height / 2 + radarRect.height / 2;

    return isIntersect;
  }

  // 교차 애니메이션을 처리하는 함수
  function animateIntersection() {
    const radar = document.querySelector(".radar-line");
    const targets = document.querySelectorAll(".target");

    targets.forEach((target) => {
      const isIntersect = checkIntersection(target, radar);
      if (isIntersect) {
        // target.style.backgroundColor = "red"
        target.style.visibility = "visible";
        console.log("레이더와 타겟이 겹칩니다!");
      } else {
        // target.style.backgroundColor = "green"
        target.style.visibility = "hidden";
      }
    });

    requestAnimationFrame(animateIntersection);
  }

  // 교차 애니메이션 시작
  animateIntersection();
</script>

<div class="container">
  <ul class="radar-wrapper">
    <li />
    <li />
    <li />
    <li />
    <li />
    <li />
    <li />
    <li class="radar-line" />
    <div class="target" id="target1">
      <img src="/targetPerson.svg" alt="target" style="width: 16px" />
      <p>대통령</p>
    </div>
    <div class="target" id="target2">
      <img src="/targetPerson.svg" alt="target" style="width: 16px" />
      <p>국회의원</p>
    </div>
    <div class="target" id="target3">
      <img src="/targetPerson.svg" alt="target" style="width: 16px" />
      <p>김현조</p>
    </div>
    {#each personLocation as person}
      <div class="target" id="person" style={`left: ${person.left}%; top: ${person.top}%;`}>
        <img src="/person.svg" alt="person" style="width: 12px" />
      </div>
    {/each}
  </ul>
</div>

<style>
  .container {
    width: 100%;
    height: 600px;
    background: linear-gradient(180deg, #004cbf, #000 90%);
  }

  .radar-wrapper {
    position: absolute;
    top: 48%;
    left: 50%;
    transform: translate(-50%, -50%);
    margin: 0;
    padding: 0;
    width: 440px;
    height: 440px;
    border-radius: 50%;
    /* border: 8px solid #2f2929; */
    /* background: linear-gradient(180deg, #004cbf, #000 100%); */
  }

  /* 오브젝트 표시 */
  .radar-wrapper .target {
    content: "";
    position: absolute;
    top: 80%;
    left: 45%;
    filter: blur(0.2px);
    visibility: visible;
    /* border: solid 1px #fff; */
    /* animation: scale 3s linear infinite; */
    animation: glow 1s linear infinite;
    cursor: pointer;
  }

  .target {
    position: absolute;
    align-items: center;
    justify-content: center;
    width: 48px;
    height: 44px;
  }

  .target p {
    position: relative;
    display: flex;
    font-size: 4px;
    color: #00ffe0;
    font-weight: 600;
    text-align: center;
  }

  .radar-wrapper .target:hover {
    /* transform: scale(2); */
  }

  #target1 {
    top: 80%;
    left: 45%;
  }

  #target2 {
    top: 50%;
    left: 75%;
  }

  #target3 {
    top: 20%;
    left: 25%;
  }

  #person1 {
    top: 60%;
    left: 65%;
  }

  /* .radar-wrapper::after {
      content: "";
      position: absolute;
      
      background: yellow;
      border-radius: 50%;
      filter: blur(3px);
      animation: glow 1s linear infinite;
    } */

  /* 수직선 */
  /* .radar-wrapper li:nth-child(1),
  .radar-wrapper li:nth-child(2),
  .radar-wrapper li:nth-child(3),
  .radar-wrapper li:nth-child(4) {
    list-style: none;
    position: absolute;
    top: 50%;
    height: 0.8px;
    width: 100%;
    background: #fff;
    border-radius: 50%;
  } */

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
    border: 0.07px solid #fff;
    opacity: 0.4;
    background: transparent;
    border-radius: 50%;
  }

  /* 원형선 */
  .radar-wrapper li:nth-child(5) {
    width: 100px;
    height: 100px;
  }

  .radar-wrapper li:nth-child(6) {
    width: 240px;
    height: 240px;
  }

  .radar-wrapper li:nth-child(7) {
    width: 380px;
    height: 380px;
  }

  /* 레이더 감지선 */
  .radar-line {
    list-style: none;
    position: absolute;
    top: 50%;
    left: 50%;
    width: 240px;
    height: 220px;
    transform-origin: top left;
    background: linear-gradient(45deg, #fff 0%, transparent 50%);
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
