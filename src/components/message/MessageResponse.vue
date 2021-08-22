<template>
    <modal v-if="show" :style="style">
        <template v-slot:header>
            <div class="message__header">
                Tớ biết mà &#128525;, tớ cũng yêu cậu &#128522;
            </div>
        </template>
        <template v-slot:body>
            <div class="message__body">
                Tớ chờ tin nhắn từ cậu &lt;3
            </div>
        </template>
        <template v-slot:footer>
            <div class="message__footer">
                <button @click="onOK">&#10084;</button>
            </div>
        </template>
    </modal>
</template>

<script>
import Modal from "@/components/modal/Modal.vue"
export default {
    name: "MessageResponse",
    components: {
        Modal
    },
    props: {
        show: Boolean
    },
    data() {
        return {
            style: {
                'background-image': 'linear-gradient(#ff93a5, #ffc3a0)'
            }
        }
    },
    methods: {
        onOK() {
            this.$emit('response-message')
        },
    }
}
</script>

<style lang="scss" scoped>
.message__header {
    display: flex;
    justify-content: center;
    font-weight: bold;
    font-size: 20px;
    color: white;
}
.message__body {
    display: flex;
    justify-content: center;
    font-size: 18px;
    color: white;
}
.message__footer {
    display: flex;
    justify-content: center;
    button {
        font-family:courier,helvetica,arial;
        font-weight: bold;
        font-size: 20px;
        outline: none;
        border: none;
        color: white;
        background: #ff1e56;
        border-radius: 5px;
        padding: 6px 15px;
        &:hover {
            cursor: pointer;
        }
        &:active {
            transform: scale(0.98);
        }
    }
}
</style>