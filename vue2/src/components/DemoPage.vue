<template>
    <!-- 示例 -->
    <div id="main">
        <div class="title">
            <h1>TodoList</h1>
        </div>
        <div class="container">
            <div class="input">
                <input type="text" class="new-todo" placeholder="输入任务" v-model="newTodo" @keyup.enter="addTodo">
                <button class="add-todo" @click="addTodo">添加任务</button>
            </div>
            <div class="content">
                <ul class="todo-list">
                    <li class="todo-item" v-for="(item, index) in list" :key="index">
                        <div class="item">
                            <span class="index">{{ index + 1 }}.</span>
                            <span class="text">{{ item.text }}</span>
                        </div>
                        <button @click="delTodo(item.id)">x</button>
                    </li>
                </ul>
            </div>
            <div class="footer">
                <span>合计：<strong>{{ total }}</strong></span>
                <button class="clear-todo" @click="clear">清空任务</button>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    data() {
        return {
            list: [
                { "id": 1, "text": "吃饭" },
                { "id": 2, "text": "睡觉" },
                { "id": 3, "text": "打豆豆" }
            ],
            newTodo: ''
        }
    },
    computed: {
        total() {
            return this.list.length;
        }
    },
    methods: {
        addTodo() {
            if (this.newTodo.trim()) {
                this.list.push({
                    id: this.list.length + 1,
                    text: this.newTodo
                })
                this.newTodo = ''
            } else {
                alert('请输入任务')
            }
        },
        delTodo(id) {
            this.list = this.list.filter(item => item.id !== id)
        },
        clear() {
            this.list = []
        }
    }

}
</script>

<style scoped>
* {
    margin: 0px;
    padding: 0px;
    /* background-color: #eee; */
}

#main {
    width: 550px;
    margin: 0 auto;
}

.title {
    color: #e76d6d;
    text-align: center;
    margin-top: 30px;
    margin-bottom: 20px;
}

.container {
    background-color: #eee;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 20px;
    box-shadow: 0 0 10px #ccc;
}

.input {
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
    height: 34px;
    padding: 5px;
}

.content {
    margin-top: 10px;
    width: 400px;
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