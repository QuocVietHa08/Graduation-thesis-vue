<template>
  <div class="hero-container">
    <div class="text-container">
      <div class="text-wrapper">
        <div class="title">the best authors here</div>
        <div class="elementor-heading-title elementor-size-xxl">
          A new place to collect &amp; sell
          <span class="decor">NFT</span> assets
        </div>
        <button class="button-view-market">
          View Market
        </button>
      </div>
    </div>
    <div class="image-container">
      <div class="flex flex-col gap-3">
        <img src="../../static/hero-image/abstract-figure-1.webp" alt="" />
        <img src="../../static/hero-image/abstract-figure-2.webp" alt="" />
        <div class="white-circle"><span>25K</span><br /> Items</div>
      </div>
      <div class="flex flex-col gap-3">
        <img src="../../static/hero-image/abstract-figure-3.webp" alt="" />
        <img src="../../static/hero-image/abstract-figure-4.webp" alt="" />
      </div>
      <div class="flex flex-col gap-3">
        <img src="../../static/hero-image/abstract-figure-5.webp" alt="" />
        <img src="../../static/hero-image/abstract-figure-6.webp" alt="" />
        <img src="../../static/hero-image/abstract-figure-7.webp" alt="" />
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.hero-container {
  height: 100vh;
  width: 100vw;
  display: flex;
  align-items: center;
  justify-content: center;
}
.text-container {
  height: 100%;
  width: 45%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.text-wrapper {
  margin: 0px 20px;
}

.title {
  font-size: 14px;
  text-transform: uppercase;
  line-height: 1.2em;
  letter-spacing: 1.8px;
}

.elementor-heading-title {
  font-size: 67px;
  line-height: 1.063em;
  letter-spacing: -2.4px;
  font-size: 3.563em;
  font-weight: 500;
  font-style: normal;
  line-height: 1em;
  text-decoration: none;
  text-transform: none;
  letter-spacing: -1.8px;
  margin-top: 1.1em;
  margin-bottom: 0.4em;
  font-family: 'Quattrocento Sans', sans-serif;
}

.image-container {
  height: 100%;
  width: 45%;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 30px;
  margin: 30px 20px;
}

.button-view-market {
  background-color: #9cbe11;
  color: white;
  padding: 15px 35px;
  border-radius: 25px;
}

.white-circle {
  width: 188px;
  height: 188px;
  border: 2px solid white;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  span {
    font-size: 42px;
    line-height: 0px;
    text-align: center;
    }
  }
</style>
