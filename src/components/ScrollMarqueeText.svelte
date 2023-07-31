<!-- 스크롤 애니메이션 -->
<script>
  import { onMount } from "svelte";
  export let pTag;
  export let text;
  export let direction;
  let count = 0;

  // 테이프 문장 단어 띄어쓰기 처리
  function initTexts(element, textArray) {
    let joinedText = textArray.join("\u00A0\u00A0\u00A0");
    element.innerText = joinedText;
  }

  // 무한 스크롤
  function marqueeText(count, element, direction) {
    if (count > element.scrollWidth / 2) {
      element.style.transform = `translateX(0)`;
      count = 0;
    }
    element.style.transform = `translateX(${count * direction}px)`;

    return count;
  }

  function animate() {
    count++;
    count = marqueeText(count, pTag, direction);

    window.requestAnimationFrame(animate);
  }

  onMount(() => {
    initTexts(pTag, text);
    animate();

    // scroll 함수를 통해 scroll 속도값 조정
    window.addEventListener("scroll", () => {
      count += 15;
    });
  });
</script>

<div class="text-marquee">
  <div class="cover">
    <p class="first-tape" bind:this={pTag} direction={direction} text={text} />
  </div>
</div>

<style>
  .text-marquee {
    position: relative;
  }

  .cover {
    width: 100vw;
    height: 140px;
    display: flex;
  }

  p {
    font-size: 32px;
    color: #fff;
    display: flex;
    padding: 3rem 0;
  }
</style>
