<template>
    <div>
        <div>{{ txt }}</div>
    </div>

</template>

<script>


export default {
    props: ['text'],
    data() {
        return {
            txt: '',
            timer: null
        }
    },
    watch: {
        text() {
            //未开启帧模式
            this.noTimeSlicing()
        }
    },
    methods: {
        noTimeSlicing() {
            const s = performance.now()
            while (performance.now() - s < 1) {

            }
            this.txt = '结果改变了' + this.text
        }
    }
}
</script>

