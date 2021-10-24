<template>
  <div class="background">
    <div class="main-window">
      <Header />
      <Body />
    </div>
    <img class="svg" src='./assets/metaball-union.svg' />
  </div>
</template>

<script>
import Header from './components/Header'
import Body from './components/Body'

export default {
  name: 'App',
  data() {
    return {

  }},
  components: {
    Header,
    Body
  }
}
</script>

<style>
.background, .svg {
    width: 100%;
    height: 1500px;
    background-color: rgb(41, 41, 41);
    position: relative;
    overflow: hidden;
}

.svg {
  background-color: #121212;
  width: 125%;
  height: 100%;
  left: -100px;
  top: 0px;
  right: 0;
  bottom: 0;
  opacity: 1;
  box-shadow: inset 0px 0px 20px #121212;
}

.main-window {
    width: 644px;
    height: 627px;
    position: absolute;
    z-index: 2;
    left: 50%;
    margin-left: -322px;
    top: 50%;
    margin-top: -313.5px; 
    border-radius: 20px 20px 20px 20px;
    box-shadow: 0px 10px 20px #0e0e0e26;
}

  @media screen and (max-width: 1400px) {
    .background, .svg {
      width: 100%;
      height: 800px;
    }

    .svg {
      width: 100%;
      height: 800px;
      left: 0;
    }
  }

  @media screen and (max-width: 1050px) {
    .svg {
      width: 130%;
    }
  }
  
  /* Ipad Pro Portrait */

  @media all and (device-width: 1024px) and (device-height: 1366px) and (orientation: portrait) {
    .background {
      height: 1366px !important;
    }

    .svg {
      height: 100% !important;
    }
  }

  /* Ipad Pro Landscape */

  @media only screen and (min-device-width: 1366px) and (device-height: 1024px) and (orientation: landscape) {
    .background {
      height: 1024px !important;
    }

    .svg {
      height: 100% !important;
    }
  }

  /* Ipad Portrait */

  @media all and (device-width: 768px) and (device-height: 1024px) and (orientation: portrait) {
    .background {
      height: 1024px !important;
    }

    .svg {
      height: 100% !important;
    }
  }

  /* Ipad Landscape */

  @media all and (device-width: 1024px) and (device-height: 768px) and (orientation: landscape) {
    .background {
      height: 768px !important;
    }

    .svg {
      height: 100% !important;
    }
  }

  @media screen and (max-width: 820px) {
    .svg {
      width: 150%;
    }
  }

  @media screen and (max-width: 720px) {
    .svg {
      width: 160%;
    }
  }

  @media screen and (max-width: 650px) {
    .svg {
      width: 190%;
    }
    .main-window {
        width: 400px;
        margin-left: -200px;
    }
  }
  

  @media screen and (max-width: 550px) {
    svg {
      width: 200%;
    }
  }

  /* Iphone X */

  @media screen and (max-width: 375px) {
    .main-window {
        width: 330px;
        margin-left: -165px;
        height: 500px;
        margin-top: -250px;
    }

    .svg {
      width: 290%;
    }
  }

</style>
