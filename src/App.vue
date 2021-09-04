<template>
  <div
    class="app-container"
    :class="[setImage ? 'image-background' : 'image-color']"
  >
    <div v-if="!setImage" class="app-loader">
      <HeartLoading />
    </div>
    <div v-if="showTitle" class="app-title-wrapper">
      <div class="app-title">Cậu yêu tớ có phải không &#128540;</div>
      <div class="app-title--small">
        Cậu không trả lời hoặc thoát ra thì cậu là vợ tớ đấy nhé :>
      </div>
    </div>
    <div v-if="openModal" class="app-modal-wrapper">
      <div class="app-modal">
        <HelloModal @close-modal="closeModal" />
      </div>
    </div>
    <div v-if="showTitle" class="app-button-wrapper">
      <div class="app-button__yes">
        <button @click="onIDo">Ok tớ đồng ý &lt;3 </button>
      </div>
      <div @mouseover="changePosition" class="app-button__no">
        <button>Cậu mơ đi :3</button>
      </div>
    </div>
    <MessageSending
    :show="showMessageModal"
    @send-message="onSendMessage"
    />
    <MessageResponse
    :show="showResponseModal"
    @response-message="onResponseMessage"
    />
  </div>
</template>

<script>
import HelloModal from "./components/modal/ImageModal.vue";
import HeartLoading from "./components/loader/HeartLoading.vue";
import MessageSending from "@/components/message/MessageSending"
import MessageResponse from "@/components/message/MessageResponse"

export default {
  name: "App",
  components: {
    HelloModal,
    MessageSending,
    MessageResponse,
    HeartLoading,
  },
  mounted() {
    setTimeout(() => this.showImage(), 3000);
  },
  data() {
    return {
      openModal: false,
      setImage: false,
      showTitle: false,
      showMessageModal: false,
      showResponseModal: false,
      counter: 0,
    };
  },
  methods: {
    showImage() {
      console.log("hello");
      this.setImage = true;
      setTimeout(() => (this.openModal = true), 800);
    },
    closeModal() {
      this.openModal = false;
      this.showTitle = true;
    },
    changePosition() {
      var b = document.querySelector(".app-button__no");
      console.log(window.screen.height)
      console.log(window.screen.width)
      if (this.counter < 4) {
        var i = Math.floor(Math.random() * 300) + 1;
        var j = Math.floor(Math.random() * 300) + 1;
        console.log(i, j)
        b.style.display = "block";
        b.style.position = "absolute";
        b.style.left = i + "px";
        b.style.top = j + "px";
        this.counter = this.counter + 1;
      } else {
        var c = document.querySelector(".app-button__yes");
        const yesLeft = c.offsetLeft;
        const yesTop = c.offsetTop;

        b.style.left = yesLeft + "px";
        b.style.top = yesTop + "px";
        b.style.margin = 0;

        b.style.position = "static";
        c.style.position = "absolute";
      }
    },
    onIDo() {
      this.showMessageModal = true
    },
    onSendMessage() {
      this.showMessageModal = false
      this.showResponseModal = true
    },
    onResponseMessage() {
      // this.showResponseModal = false
      window.location.href='https://www.instagram.com/dangkhoa1312/';
    }
  },
};
</script>

<style scoped lang="scss">
$base-color: #f17171;
%general-button {
  border-radius: 4px;
  padding: 8px;
  font-size: 16px;
  border: 2px solid white;
  color: white;
  outline: none;
  cursor: pointer;
  &:active {
    transform: scale(0.98);
  }
}

.image-background {
  height: 100%;
  // filter: blur(3px);
  background-image: url("./assets/mily_image.jpg");
  background-size: 100% 100%;
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-position: center; 
  @media only screen and (max-width: 4) {
    background-image: url("./assets/anh_co.jpg");
  } 
}
.image-color {
  height: 100%;
  background-image: linear-gradient(rgb(247, 138, 232), rgb(231, 187, 233));
}

.app-container {
  .app-loader {
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .app-modal-wrapper {
    position: relative;
    margin: 0 auto;
    top: -400px;
    animation: drop 0.7s ease forwards;
    width: 480px;
    @media only screen and (max-width: 471px) {
        width: 300px;
    }

    .app-modal {
      width: 100%;
      position: absolute;
      z-index: 50;
    }
  }
  .app-title-wrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    .app-title {
      display: flex;
      font-family: "Pacifico";
      font-size: 70px;
      color: $base-color;
      
      @media only screen and (max-width: 471px) {
        font-size: 45px;
        text-align: center;
      }
    }
    .app-title--small {
      font-family: "Pacifico";
      font-size: 23px;
      color: $base-color;
      @media only screen and (max-width: 471px) {
        font-size: 17px;
        text-align: center;
      }
    }
  }
  .app-button-wrapper {
    display: flex;
    justify-content: center;
    margin-top: 50px;
    .app-button__yes {
      margin-right: 15px;
      button {
        background-color: rgb(230, 82, 82);
        @extend %general-button;

        &:hover {
          background-color: rgb(214, 115, 115);
        }
      }
    }
    .app-button__no {
      margin-left: 15px;
      display: flex;
      button {
        background-color: rgb(22, 189, 175);
        @extend %general-button;

        &:hover {
          background-color: rgb(81, 197, 187);
        }
      }
    }
  }
  @keyframes drop {
    0% {
      opacity: 0;
    }
    70% {
      transform: translateY(600px);
    }
    100% {
      transform: translateY(550px);
      opacity: 1;
    }
  }
}
</style>
