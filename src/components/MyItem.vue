<template>
  <li>
    <label>
      <input
        type="checkbox"
        :checked="TodoObj.done"
        @change="handleCheck(TodoObj.id)"
      />
      <span v-show="!TodoObj.isEdit">{{ TodoObj.title }}</span>
      <input  
         type="text" 
        v-show="TodoObj.isEdit"
        :value="TodoObj.title"
        @blur="handleBlur(TodoObj,$event)"  
        >
    </label>
    <button class="btn btn-danger" @click="handleDelete(TodoObj.id)">
      删除
    </button>
    <button  v-show="!TodoObj.isEdit" class="btn btn-edit" @click="handleEdit(TodoObj)">
      编辑
    </button>
  </li>
</template>

<script>
export default {
  name: "MyItem",
  //声明接收TodoObj对象
  props: ["TodoObj"],
  methods: {
    //勾选or取消勾选
    handleCheck(id) {
      //通知App组件将对应的todo对象的done值取反
      //事件总线
      this.$bus.$emit('checkTodo',id)
    },
    // todo 删除
    handleDelete(id) {
      if (confirm("确定删除吗？")) {
        //通知App组件将对应的todo对象删除
        //this.deleteIodo(id);
        this.$bus.$emit('deleteTodo',id)
      }
    },
    //编辑
    handleEdit(todo){
      if(todo.hasOwnProperty('isEdit')){
        todo.isEdit=true
      }else{
        this.$set(todo,'isEdit',true)
      }
    },
    //失去焦点回调（真正执行修改逻辑）
    handleBlur(todo,e){
      todo.isEdit=false
      if(!e.target.value.trim()) return alert('输入不能为空')
      this.$bus.$emit('updateTodo',todo.id,e.target.value)
    }
  },
};
</script>

<style scoped>
/*item*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}

li:hover {
  background: #ddd;
}

li:hover button {
  display: block;
}
</style>