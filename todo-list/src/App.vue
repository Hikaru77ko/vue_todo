<template>
    <div id="app">
        <h1>ToDoリスト</h1>
        <div>
            <input type="radio" id="all" name="state" checked>
            <label for="all">すべて</label>
            <input type="radio" id="working" name="state">
            <label for="working">作業中</label>
            <input type="radio" id="done" name="state">
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
                    <td><button>{{ task.state }}</button><button>{{ task.delete }}</button></td>
                </tr>
            </tbody>
        </table>
        <h2>新規タスクの追加</h2>
        <input v-model.trim="addText" type="text" name="task">
        <button @click="addTask">追加</button>
    </div>
</template>

<script>

export default {
    data (){
      return {
          addText: "",
          tasks: []
      }
    },
    methods: {
      addTask: function() {
          this.tasks.push({task:this.addText, state:"作業中", delete:"削除"});
          this.addText = "";
      }
    }
}
</script>

<style>

</style>
