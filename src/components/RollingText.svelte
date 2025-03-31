
<script>
  import { gsap } from "gsap";
  import { onMount } from "svelte";

  export let stagger = 3;
  export let duration = 0.8;
  export let repeat = -1;
  export let repeatDelay = 0;
  export let ease = "expo.inOut";

  let animation;
  let container;

  onMount(() => {
    animation = gsap.timeline({
      repeat,
      repeatDelay,
      defaults: { duration, ease },
    });

    gsap.set(container.querySelectorAll("span"), { autoAlpha: 0, yPercent: -100 });
    animation
      .to(container.querySelectorAll("span"), { yPercent: 0, autoAlpha: 1, stagger })
      .to(
        container.querySelectorAll("span"),
        { yPercent: 100, autoAlpha: 0, stagger },
        stagger
      );
  });
</script>

<div bind:this={container} class="rolling-text">
  <slot />
</div>