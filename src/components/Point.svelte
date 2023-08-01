<script>
  export let x;
  export let y;

  const fieldY = y;
  const speed = 0.1;
  let cur = 0;
  const max = Math.random() * 100 + 150;

  function update() {
    cur += speed;
    y = fieldY + Math.sin(cur) * max;
  }
</script>
