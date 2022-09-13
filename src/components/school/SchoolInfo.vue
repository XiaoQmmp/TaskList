<template>
    <div>
        <h1>学校信息</h1>
        <h2>学校名称：{{name}}</h2>
        <h2>学校地址：{{address}}</h2>
    </div>
</template>

<script>
export default {
        name:'SchoolInfo',
        data() {
            return {
               name:'咸宁职业技术学院' ,
               address:'咸宁'
            }
        },
    }
</script>

<style>

</style>