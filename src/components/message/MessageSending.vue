<template>
    <modal v-if="show" :style="style">
        <template v-slot:header>
            <div class="message__header">
                Cậu nhắn điều gì đó cho tớ đi :)
            </div>
        </template>
        <template v-slot:body>
            <div class="message__body">
                <input type="text"
                class=""
                @input="onKeyPress"
                ref="inputMessageRef"
                >
            </div>
        </template>
        <template v-slot:footer>
            <div class="message__footer">
                <button @click="onOK">Gửi &lt;3</button>
            </div>
        </template>
    </modal>
</template>

<script>
import Modal from "@/components/modal/Modal.vue"
export default {
    name: "MessageSending",
    components: {
        Modal
    },
    props: {
        show: Boolean
    },
    data() {
        return {
            message: "Khoa là 1 thằng mập :D",
            count: 0,
            style: {
                'background-image': 'linear-gradient(#ff93a5, #ffc3a0)'
            }
        }
    },
    methods: {
        onOK() {
            this.$emit('send-message')
        },
        onKeyPress(e) {
            if (e.data) this.count += 1; else this.count-= 1
            if (this.count < 0) {
                this.count = 0
            } else if (this.count > this.message.length) this.count = this.message.length

            this.$refs.inputMessageRef.value = this.message.slice(0, [this.count])
        }
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
    input {
        font-family:courier,helvetica,arial;
        width: 100%;
        padding: 5px;
        font-size: 15px;
        border-radius: 5px;
        border: solid 2px #00000000;
        &:focus {
           outline: none;
           border: solid 2px #ffafc3;
        }
    }
}
.message__footer {
    display: flex;
    justify-content: center;
    button {
        font-family:courier,helvetica,arial;
        font-weight: bold;
        font-size: 16px;
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