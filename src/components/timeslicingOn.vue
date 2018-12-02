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
            // 开启帧模式
            this.timeSlicing()
        }
    },
    methods: {
        timeSlicing() {
            cancelAnimationFrame(this.timer)
            let that = this
            this.timer = requestAnimationFrame(function demo() {
                if (that.txt == '结果改变了' + that.text) {
                    cancelAnimationFrame(timer)
                } else {
                    that.txt = '结果改变了' + that.text
                    this.timer = requestAnimationFrame(demo());
                }
            })
        }
    }
}
</script>

