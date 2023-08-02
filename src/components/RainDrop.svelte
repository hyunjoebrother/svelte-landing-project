<script context="module">
    import {onMount} from 'svelte';

    // 빗방울 튀기는 클래스
    export class RainDrop {
        constructor(x, y, velocity) {
            this.x = x;
            this.y = y;
            this.velocity = velocity
            this.gravity = 1.5
        }

        draw(ctx) {
            const {x, y, velocity}=this;
            ctx.beginPath();
            ctx.arc(this.x, this.y, 1.5, 0, Math.PI*2)
            ctx.fillStyle = '#8899a6'
            ctx.fill()
        }

        animate() {
            this.velocity.y += this.gravity
            this.x += this.velocity.x
            this.y += this.velocity.y

            this.draw()
        }
    }
</script>