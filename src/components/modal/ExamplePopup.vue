<template>
    <modal v-if="show">
        <template v-slot:header>ABC</template>
        <template v-slot:body>
            <div class="popup-body">
                HEHE
            </div>
        </template>
        <template v-slot:footer>
            <button class="ok-button" @click="onOK">OK</button>
        </template>
    </modal>
</template>

<script>
import Modal from "./Modal.vue"
export default {
    name: "ExamplePopup",
    components: {
        Modal
    },
    props: {
        show: Boolean
    },
    methods: {
        onOK() {
            this.$emit('close-modal')
        }
    }
}
</script>

<style scoped>

</style>