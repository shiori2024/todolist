<template>
    <div class="title">
        <h1>{{ title }}</h1>
    </div>
</template>
  
<script>
export default {
    props: ['title']
}
</script>
  
<style scoped>
.title {
    color: #e76d6d;
    text-align: center;
    margin-top: 30px;
    margin-bottom: 20px;
}
</style>
  