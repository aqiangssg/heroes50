<template>
  <div>
    <h2 class="sub-header">英雄列表</h2>
    <a class="btn btn-success" href="add.html">Add</a>
    <div class="table-responsive">
      <table class="table table-striped">
        <thead>
          <tr>
            <th>#</th>
            <th>姓名</th>
            <th>性别</th>
            <th>操作</th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="(item, index) in list"
            :key="item.id">
            <td>{{ index + 1 }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.gender }}</td>
            <td>
              <a href="edit.html">edit</a>
              &nbsp;&nbsp;
              <a href="javascript:window.confirm('Are you sure?')">delete</a>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
// 导入axios
import axios from 'axios';
export default {
  data() {
    return {
      // 英雄列表
      list: []
    };
  },
  mounted() {
    // 调用loadData
    this.loadData();
  },
  methods: {
    // 加载数据
    loadData() {
      axios
        .get('http://localhost:3001/heroes')
        .then((response) => {
          if (response.status === 200) {
            this.list = response.data;
          }
        })
        .catch((err) => {
          console.log(err);
        });
    }
  }
};
</script>

<style>

</style>
