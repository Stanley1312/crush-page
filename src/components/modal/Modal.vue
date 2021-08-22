<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container" :style="style">
          <div class="modal-header">
            <slot name="header">header</slot>
          </div>

          <div class="modal-body">
            <slot name="body">body</slot>
          </div>

          <div class="modal-footer">
            <slot name="footer">
              footer
              <button class="modal-default-button" @click="$emit('close')">OK</button>
            </slot>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "Modal",
  props: {
    style: {}
  }
};
</script>

<style scoped>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  transition: opacity 0.3s ease;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-wrapper {
  /* display: table-cell;
  vertical-align: middle; */
}

.modal-container {
  font-family:courier,helvetica,arial;
  margin: 0px auto;
  padding: 20px 30px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  border-radius: 10px;
  border: none;
}

.modal-header {
  margin-top: 0px;
}

.modal-body {
  /* margin: 20px 0; */
  margin-top: 20px;
}

.modal-footer {
  margin-top: 20px;
}

.modal-default-button {
  float: right;
}

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}

</style>