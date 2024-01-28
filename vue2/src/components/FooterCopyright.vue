<template>
    <div class="container">
        <span>
            <a href="https://github.com/shiori2024/todolist/tree/vue2" target="_blank">源代码</a>&nbsp;
            &copy;{{ nowTime }}&nbsp;<a href="https://github.com/shiori2024" target="_blank">shiori2024</a>
        </span>
    </div>
</template>

<script>
export default {
    data() {
        return {
            nowTime: ''
        }
    },
    created() {
        this.getTime()
    },
    methods: {
        getTime() {
            // 获取当前年份
            this.nowTime = new Date().getFullYear()
            if (this.nowTime > 2024) {
                this.nowTime = '2024 - ' + this.nowTime
            }
        }
    }
}
</script>

<style scoped>
.container {
    text-align: center;
    background-color: #eee;
    padding: 20px;
    box-shadow: 0 0 10px #ccc;
    margin: 0 auto;
    width: 100%;
    position: fixed;
    bottom: 0px;
    display: flex;
    justify-content: center;
    align-items: center;
}

a {
    text-decoration: none;
    color: #e76d6d;

    &:hover {
        border-bottom: 2px solid #e76d6d;
    }
}
</style>