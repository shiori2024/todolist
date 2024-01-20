<template>
    <div class="footer">
        <span>合计：<strong>{{ total }}</strong></span>
        <button class="clear-todo" @click="clear">清空任务</button>
    </div>
</template>

<script>
export default {
    props: ['list'],
    computed: {
        total() {
            return this.list.length
        }
    },
    methods: {
        clear() {
            this.$emit('clear')
        }
    }
}
</script>

<style scoped>
.footer {
    width: 350px;
    margin-top: 5px;
    font-size: 14px;
    color: #a5a2a2;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.clear-todo {
    border: none;
    cursor: pointer;
    color: #a5a2a2;
}
</style>