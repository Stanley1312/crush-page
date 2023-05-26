<template>
    <modal v-if="show" :style="style">
        <template v-slot:header>
            <div class="message__header">
                Tớ biết mà &#128525;, tớ cũng yêu cậu &#128522;
            </div>
        </template>
        <template v-slot:body>
            <div class="message__body">
                <!-- HiHi, Hello cô nak &#128536;, hmmm thật ra thì lâu ni dịch quá hăm gặp cô được, cũng chả đi đâu được nên cũng ít tâm sự với cô được,
                em làm cái này vì muốn làm gì đó chọc cho cô vui tí thui nak, với lại cho cô thấy dân IT tỏ tính thì như răn hen haha, mấy cái câu nớ
                cô đừng để ý cũng được haha, em như răn với cô thì cô cũng biết rùi mà hì hehe, bây giờ chỉ làm bạn cô như ri cũng vui rùi, 
                chỉ luôn mong cô luôn luôn vui vẻ và hạnh phúc nhá, Cô có gì muốn nói thì click vào hính trái tim bên dưới nha hehe. Pai Pai cô nak &#128541; -->
                Hé lô hơ sờ ly ly &lt;3 &lt;3 &lt;3
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
    max-width: 700px;
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