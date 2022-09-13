<template>
    <div>
        <SchoolInfo/>
        <StudentInfo/>
    </div>
</template>

<script>
    import SchoolInfo from './components/school/SchoolInfo'
    import StudentInfo from './components/student/StudentInfo'

export default {
    name:'App',
    components:{
        SchoolInfo,
        StudentInfo
    }
}
</script>