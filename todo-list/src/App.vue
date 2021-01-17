<template>
  <div id="app">
    <h1>ToDoリスト</h1>
    <div>
      <input type="radio" id="all" name="state" checked />
      <label for="all">すべて</label>
      <input type="radio" id="working" name="state" />
      <label for="working">作業中</label>
      <input type="radio" id="done" name="state" />
      <label for="done">完了</label>
    </div>
    <table>
      <thead>
        <th>ID</th>
        <th>コメント</th>
        <th align="left">状態</th>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" v-bind:key="task.id">
          <td>{{ index }}</td>
          <td>{{ task.task }}</td>
          <td>
            <button @click="chengStateNum(task)">{{ state[task.stateNum] }}</button
            ><button @click="deleatTask()">削除</button>
          </td>
        </tr>
      </tbody>
    </table>
    <h2>新規タスクの追加</h2>
    <input v-model.trim="content" type="text" name="task" />
    <button @click="addTask">追加</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      content: '',
      tasks: [],
      id: 0,
      stateNum: 1,
      state: ['完了','作業中']
    };
  },
  methods: {
    addTask: function() {
      this.tasks.push({
        id: this.id++,
        task: this.content,
        stateNum: this.stateNum
      });
      this.content = '';
    },
    deleatTask: function(index) {
      this.tasks.splice(index, 1);
    },
    chengStateNum: function(task) {
      task.stateNum = task.stateNum ? 0 : 1
    }
  },
};
</script>

<style></style>
