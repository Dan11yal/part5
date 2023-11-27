<template>
  <div class="main">
      <form action="" @submit.prevent class="form">
        <h4>Add Task</h4>
        <input type="text" @input="title=$event.target.value" v-bind:value="title" placeholder="Write any data">
        <button @click="addItem">ADD</button>
      </form>

      <div class="tasks">
        <ul>
            <li v-for="(list,index) in lists" :key="index" >
                <div :class="{completed:list.completed}">{{ list.title }}</div>
                <div class="s">
                <label for="select">compleeted</label>
                <input @click="update(index)" type="checkbox" value="completed" id="select">
                <button @click="dropPost(index)">Delete</button>
              </div>
            </li>
        </ul>
      </div>
  </div>
</template>

<script>
export default{
    data(){
        return{
            lists:[
                {title:'Daniyal',completed:false}
            ],
            title:'',
            completed:false

        }
    },
    methods:{
        addItem(){
          const item = {title:this.title,compleeted:this.compleeted};
           if(this.title.trim()!==''){
            this.lists.push(item);
            this.title='';
           }
        },
        update(index){
          this.lists[index].completed = !this.lists[index].completed;
        },
        dropPost(index){
            this.lists.splice(index,1);
      }

    }

}
</script>

<style>
.completed{
  text-decoration: line-through;
}

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  background-color: teal;
      text-align: center;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      padding: auto;
}
.main{
  width: 700px;
}
.form h4{
  font-size: 25px;
  color: azure;
  margin-bottom: 15px;
}
.form input{
  padding: 10px;
  outline: none;
  border: none;
  border-radius: 10px;
  margin-right: 10px;
  width: 500px;
}
.form button{
  padding: 10px;
  outline: none;
  border: none;
  border-radius: 10px;
  color: aliceblue;
  background-color:hotpink ;
}
.tasks ul{
  align-items: center;
  text-decoration: none;
  list-style: none;
}
.tasks li{
  background-color: aliceblue;
  margin: 15px 0;
  padding: 15px;
  border-radius: 15px;
  display: flex;
  justify-content: space-between;
  font-size: 20px;
  word-wrap:break-word;
  align-items: center;
}
.tasks button{
  background-color: hotpink;
  color: aliceblue;
  padding: 5px 8px;
  outline: none;
  border: none;
  border-radius: 3px;
}
#select{
  width: 30px;
  height: 20px;
}

</style>