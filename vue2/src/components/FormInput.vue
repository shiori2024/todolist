<template>
    <div class="form">
        <input type="text" class="new-todo" placeholder="输入任务" v-model="newTodo" @keyup.enter="addTodo">
        <button class="add-todo" @click="addTodo">添加任务</button>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            newTodo: '',
            newlist: []
        }
    },
    methods: {
        addTodo() {
            if (this.newTodo.trim()) {
                this.$emit('addTodo', this.newTodo)
                this.newTodo = ''
            } else {
                alert('请输入任务')
            }
        }
    },
    mounted() {
        // 页面加载后，自动获取焦点
        document.querySelector(".new-todo").focus()
    }
}
</script>
  
<style scoped>
.form {
    display: flex;
    justify-content: center;
    align-items: center;
    background: #eee;
}

.new-todo {
    width: 350px;
    outline: none;
    border: 2px solid #e76d6d;
    border-radius: 5px 0px 0px 5px;
    height: 30px;
    padding-left: 5px;
    background: #eee;
}

.add-todo {
    outline: none;
    border: none;
    border-radius: 0px 5px 5px 0px;
    cursor: pointer;
    color: white;
    background: #e76d6d;
    height: 36px;
    padding: 5px;
}
</style>
  