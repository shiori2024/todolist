<template>
    <div class="container">
        <span>
            <a href="https://github.com/shiori2024/todolist/tree/vue2">源代码</a>&nbsp;
            &copy;2024&nbsp;<a href="https://github.com/shiori2024">shiori2024</a>
        </span>
    </div>
</template>

<script>

</script>

<style scoped>
.container {
    text-align: center;
    background-color: #eee;
    padding: 20px;
    box-shadow: 0 0 10px #ccc;
    margin: 0 auto;
    width: 100%;
    position: absolute;
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