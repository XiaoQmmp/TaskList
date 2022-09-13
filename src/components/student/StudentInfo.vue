<template>
    <div>
        <h1>学生信息</h1>
        <h2>学生性名：{{name}}</h2>
        <h2>学生性别：{{sex}}</h2>
        <h2>学生年龄：{{age}}</h2>
    </div>
</template>

<script>
export default {
    name:'StudentInfo',
    data() {
        return {
            name:'xiaoQ',
            sex:'男',
            age:'20'
        }
    },
}
</script>

<style>

</style>