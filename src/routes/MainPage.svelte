<!-- 스크롤 애니메이션 -->
<script>
  import ScrollMarqueeText from "../components/ScrollMarqueeText.svelte";
  let name = "lol";
  let pTag1;
  let pTag2;

  let textTape1 =
    "You know, without you, Im so lonely. When youre not here, 911 calling";
  let textTape2 =
    "Into your heat again, Im diving. Darling you, darling you, baby";
</script>

<div class="container">
  <div class="text-marquee">
      <ScrollMarqueeText
        bind:this={pTag1}
        text={textTape1.split(" ")}
        direction={1}
      />
      <ScrollMarqueeText
        bind:this={pTag2}
        text={textTape2.split(" ")}
        direction={-1}
      />
  </div>

  <div class="text-scroll">
    <h1>Hello {name}!</h1>
    <h1>마치 된 것 같아</h1>
    <h1>손오공</h1>
    <h1>I luv My Team!</h1>
    <h1>I luv My Crew!</h1>
    <h1>다룸다림다</h1>
    <h1>"이 밤은 짧고, 넌 당연하지 않아"</h1>
  </div>
</div>

<style>
  .container {
    top: 0;
    width: 100%;
    height: 8000px;
  }

  .text-marquee {
    position: absolute;
    top: 300px;
    height: 300px;
  }

  h1 {
    color: #fff;
    text-align: center;
    margin-top: 1000px;
  }
</style>
