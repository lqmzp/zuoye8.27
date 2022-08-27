<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" placeholder="名称" v-model="name" />
    </div>
    <div>
      <span>年龄:</span>
      <input type="number" placeholder="年龄" v-model.number="age" />
    </div>
    <div>
      <span>性别:</span>
      <select v-model="sex" :checkbox="0">
        <option value="男">男</option>
        <option value="女">女</option>
      </select>
    </div>
    <div>
      <button @click="add">添加/修改</button>
    </div>
    <div>
      <table border="1" cellpadding="10" cellspacing="0">
        <tr>
          <th>序号</th>
          <th>姓名</th>
          <th>年龄</th>
          <th>性别</th>
          <th>操作</th>
        </tr>
        <tr v-for="(obj, i) in list" :key="i">
          <td>{{ obj.id }}</td>
          <td>{{ obj.name }}</td>
          <td>{{ obj.age }}</td>
          <td>{{ obj.sex }}</td>
          <td>
            <button @click="del(obj.id)">删除</button>
            <button @click="gai(obj.id - 1)">编辑</button>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      list: [],
      name: "",
      age: 0,
      sex: "男",
      flag: false,
    };
  },
  methods: {
    add() {
      // 5. 判断是否为空
      if (this.name.trim().length === 0 || this.age === 0) {
        alert("不能为空");
        return;
      }
      if (this.flag) {
        const a = {
          id: this.flag,
          name: this.name,
          age: this.age,
          sex: this.sex,
        };
        this.$set(this.list, [this.flag], a);
        (this.flag = false),
          (this.name = ""),
          (this.age = 0),
          (this.sex = "男");

        return;
      }
      const a = {
        id: this.list.length ? this.list[this.list.length - 1].id + 1 : 1,
        name: this.name,
        age: this.age,
        sex: this.sex,
      };
      (this.name = ""), (this.age = 0), (this.sex = "男");
      this.list.push(a);
    },

    del(i) {
      let index = this.list.findIndex((obj) => obj.id === i);
      //   console.log(index);
      this.list.splice(index, 1);
    },
    gai(i) {
      this.flag = i;
      console.log(this.flag);
      (this.name = this.list[i].name),
        (this.age = this.list[i].age),
        (this.sex = this.list[i].sex);
    },
  },
};
</script>
