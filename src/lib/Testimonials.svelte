<script lang="ts">
  import { onMount } from "svelte";
  import type { HTMLElement } from "svelte";

  let slider: HTMLElement;
  let slideTrack: HTMLElement;
  let animation: Animation;

  interface AnimationOptions {
    duration: number;
    iterations: number;
    easing: string;
  }

  function createAnimation(): Animation {
    const animationOptions: AnimationOptions = {
      duration: 16000,
      iterations: Infinity,
      easing: "linear",
    };

    return slideTrack.animate(
      [
        { transform: "translateX(0)" },
        { transform: "translateX(calc(-250px * 7))" },
      ],
      animationOptions
    );
  }

  function handleMouseEnter(): void {
    animation.updatePlaybackRate(0.5);
  }

  function handleMouseLeave(): void {
    animation.updatePlaybackRate(1);
  }

  onMount(() => {
    animation = createAnimation();
    slider.addEventListener("mouseenter", handleMouseEnter);
    slider.addEventListener("mouseleave", handleMouseLeave);

    return () => {
      slider.removeEventListener("mouseenter", handleMouseEnter);
      slider.removeEventListener("mouseleave", handleMouseLeave);
      animation.cancel();
    };
  });
</script>

<body>
  <div
    class="slider"
    bind:this={slider}
    on:mouseenter={handleMouseEnter}
    on:mouseleave={handleMouseLeave}
  >
    <div class="slide-track" bind:this={slideTrack}>
      <div class="slide">
        <img
          src="https://crypto-central.io/library/uploads/Messari-Logo.png"
          height="100"
          width="100"
          alt=""
        />
      </div>
      <div class="slide">
        <img
          src="https://crypto-central.io/library/uploads/Messari-Logo.png"
          height="100"
          width="100"
          alt=""
        />
      </div>
      <div class="slide">
        <img
          src="https://crypto-central.io/library/uploads/Messari-Logo.png"
          height="100"
          width="100"
          alt=""
        />
      </div>
      <div class="slide">
        <img
          src="https://crypto-central.io/library/uploads/Messari-Logo.png"
          height="100"
          width="100"
          alt=""
        />
      </div>
      <div class="slide">
        <img
          src="https://crypto-central.io/library/uploads/Messari-Logo.png"
          height="100"
          width="100"
          alt=""
        />
      </div>
      <div class="slide">
        <img
          src="https://crypto-central.io/library/uploads/Messari-Logo.png"
          height="100"
          width="100"
          alt=""
        />
      </div>
      <div class="slide">
        <img
          src="https://crypto-central.io/library/uploads/Messari-Logo.png"
          height="100"
          width="100"
          alt=""
        />
      </div>
      <div class="slide">
        <img
          src="https://crypto-central.io/library/uploads/Messari-Logo.png"
          height="100"
          width="100"
          alt=""
        />
      </div>
      <div class="slide">
        <img
          src="https://crypto-central.io/library/uploads/Messari-Logo.png"
          height="100"
          width="100"
          alt=""
        />
      </div>
      <div class="slide">
        <img
          src="https://crypto-central.io/library/uploads/Messari-Logo.png"
          height="100"
          width="100"
          alt=""
        />
      </div>
      <div class="slide">
        <img
          src="https://crypto-central.io/library/uploads/Messari-Logo.png"
          height="100"
          width="100"
          alt=""
        />
      </div>
      <div class="slide">
        <img
          src="https://crypto-central.io/library/uploads/Messari-Logo.png"
          height="100"
          width="100"
          alt=""
        />
      </div>
      <div class="slide">
        <img
          src="https://crypto-central.io/library/uploads/Messari-Logo.png"
          height="100"
          width="100"
          alt=""
        />
      </div>
      <div class="slide">
        <img
          src="https://crypto-central.io/library/uploads/Messari-Logo.png"
          height="100"
          width="100"
          alt=""
        />
      </div>
    </div>
  </div>
</body>

<style>
  body {
    align-items: center;
    justify-content: center;
  }

  @keyframes scroll {
    0% {
      transform: translateX(0);
    }
    100% {
      transform: translateX(calc(-250px * 7));
    }
  }

  .slider {
    text-align: center;
    background-color: #16181c;
    height: 110px;
    border-radius: 20px;
    margin: auto;
    overflow: hidden;
    position: relative;
    width: auto;
  }

  .slider .slide-track {
    animation: scroll 16s linear infinite;
    display: flex;
    width: calc(250px * 12);
  }

  .slider .slide {
    display: grid;
    height: 100px;
    width: 100%;
    justify-content: center;
  }

  .slide {
    cursor: pointer;
  }

  /* For large screens, wider than 1440px */
  @media (max-width: 1440px) {
    .slider {
      max-width: 720px;
    }
  }

  /* For medium screens, between 1024px and 1440px */
  @media (max-width: 1024px) {
    .slider {
      max-width: 600px;
    }
  }

  /* For small screens, between 768px and 1024px */
  @media (max-width: 768px) {
    .slider {
      max-width: 500px;
    }
  }

  /* For extra small screens, less than 768px */
  @media (max-width: 480px) {
    .slider {
      max-width: 300px;
    }
  }

</style>
