<template>
    <div class="content">
        <ul class="todo-list">
            <li class="todo-item" v-for="(item, index) in list" :key="index">
                <div>
                    <span class="index">{{ index + 1 }}.</span>
                    <span class="text">{{ item.text }}</span>
                </div>
                <button @click="delTodo(item.id)">x</button>
            </li>
        </ul>
    </div>
</template>
  
<script>
export default {
    props: ['list'],
    methods: {
        delTodo(id) {
            // 将id传给父组件
            this.$emit('delTodo', id)
        }
    }
}
</script>
  
<style scoped>
* {
    margin: 0;
    padding: 0;
}

.content {
    width: 420px;
    margin-top: 10px;
    font-size: 20px;
}

.todo-list {
    list-style: none;
}

.todo-item {
    border-bottom: 1px solid #dad8d8;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.todo-item button {
    border: none;
    cursor: pointer;
    color: rgb(207, 51, 51);
}
</style>
  