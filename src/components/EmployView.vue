<template>
  <div id="employ">
    <fieldset>
      <legend>指令綜合小練習</legend>
      <div>
        <span>姓名: </span>
        <input type="text" placeholder="請輸入姓名" v-model="newPerson.name">
      </div>
      <div>
        <span>年齡: </span>
        <input type="text" placeholder="請輸入年齡" v-model="newPerson.age">
      </div>
      <div>
        <span>性別: </span>
        <select v-model="newPerson.sex">
          <option value="男">男</option>
          <option value="女">女</option>
        </select>
      </div>
      <div>
        <span>手機: </span>
        <input type="text" placeholder="請輸入手機" v-model="newPerson.phone">
      </div>
      <button @click="add">創建新用戶</button>
    </fieldset>
    <table>
      <thead>
      <tr>
        <td>姓名</td>
        <td>性別</td>
        <td>年齡</td>
        <td>手機</td>
        <td>刪除</td>
      </tr>
      </thead>
      <tbody>
         <tr v-for="(person, i) in persons" :key="person.phone">
          <td>{{person.name}}</td>
          <td>{{person.sex}}</td>
          <td>{{person.age}}</td>
          <td v-text="person.phone"></td>
          <td>
            <button @click="del(i)">刪除</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name:'EmployView',
  data() {
    return{
      persons:[
        {name:'張三', age:18, sex:'男', phone:'0911112304'},
        {name:'李四', age:28, sex:'女', phone:'0912112314'},
        {name:'王五', age:38, sex:'男', phone:'0911312324'},
        {name:'趙六', age:48, sex:'女', phone:'0914112344'},
        {name:'李七', age:58, sex:'男', phone:'0911512354'},
      ],
      newPerson:{name:'', age:0, sex:'男', phone:''}
    }
  },
  methods: {
    add(){
      const { name, age, sex, phone } = this.newPerson
      console.log(name, age, sex, phone) // 有空再篩選手機格式
      if(!name || !age || !phone){
        alert('請勿新增空資料')
        return
      }
      this.persons.unshift({...this.newPerson})
      this.newPerson = { name: '', age: 0, sex: '男', phone: '' };
    },
    del(index){
      this.persons.splice(index, 1)
    }
  }
}
</script>

<style scoped lang="css">
#employ {
  margin: 50px auto; width: 600px;
}
fieldset {
  border: 1px solid orangered;
  margin-bottom: 20px;
}
fieldset  input {
  width: 200px;
  height: 30px;
  margin: 10px 0;
}
table {
  width: 600px;
  border: 2px solid orangered;
  text-align: center;
}
thead {
  background-color: orangered;
}
</style>
