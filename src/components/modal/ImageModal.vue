<template>
  <div class="hello-modal-container">
    <div class="hello-modal-wrapper">
      <div class="hello-modal__image">
        <img
          src="https://i.pinimg.com/750x/18/7c/2f/187c2feb5ca88bab9925a3b6799e2e8e.jpg"
        />
      </div>
      <div class="hello-modal__title">
        <h2>Hee Luu Cậu !</h2>
      </div>
      <div class="hello-modal__content">
        Tớ có điều này muốn hỏi cậu, cậu trả lời thật lòng nha &#128150; &#128150; &#128150;
      </div>
      <div class="hello-modal__button">
        <button @click.prevent="clickModal">Oke</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloModal",

  methods: {
    clickModal() {
      console.log("clicked");
      this.$emit("close-modal");
    },
  },
};
</script>

<style scoped lang="scss">
.hello-modal-container {
  width: 100%;
  .hello-modal-wrapper {
    background-image: linear-gradient(#ffafbd, #ffc3a0);
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 4px;

    .hello-modal__image {
      margin-top: 40px;
      display: flex;
      width: 260px;
      height: 280px;
      img {
        width: 100%;
        height: 100%;
      }
      @media only screen and (max-width: 376px) {
        width: 200px;
        height: 200px;
      }
    }
    .hello-modal__title {
      font-weight: bold;

      h2 {
        color: white;
      }
    }

    .hello-modal__content {
      color: white;
      margin-bottom: 15px;
      font-size: 20px;
      text-align: center;
      padding: 0px 10px;
      @media only screen and (max-width: 376px) {
        font-size: 16px;
      }
    }

    .hello-modal__button {
      margin-bottom: 15px;
      button {
        width: 90px;
        border: 2px solid white;
        color: white;
        font-weight: bold;
        font-size: 17px;
        background-color: rgb(228, 153, 222);
        border-radius: 3px;
        padding: 6px;
        cursor: pointer;
        outline: none;
        &:active {
          transform: scale(0.98);
        }
        @media only screen and (max-width: 376px) {
        font-size: 14px;
      }
      }
    }
  }
}
</style>
