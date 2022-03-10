<template>
  <div class="home">    
    <HelloWorld msg="Welcome to Your Vue.js App"/>

    <h2>Персональные данные</h2>
    <div class="text-field text-field_floating adult">
      <input type="text" id="name" v-model="data.name" class="text-field__input">
      <label for="name" class="text-field__label">Имя</label>
    </div>
    <div class="text-field text-field_floating adult">
      <input type="text" id="age" v-model="data.age" class="text-field__input">
      <label for="age" class="text-field__label">Возраст</label>
    </div>

    <div class="add-childrens">
      <h2>Дети (макс.5)</h2>
      <button v-show="data.childrens.length < 5" @click="addChildren()">
        <img src="../assets/plus.svg" alt="plus">
        Добавить ребенка
        </button>    
    </div>
    <div v-for="(children, index) in data.childrens" :key="index" class="childrens">   
      <div class="text-field text-field_floating">       
        <input type="text" v-model="children.name" required class="text-field__input">
        <label for="name" class="text-field__label">Имя</label>
      </div>
      <div class="text-field text-field_floating childrens">
        <input type="text" v-model="children.age" required class="text-field__input">
        <label for="age" class="text-field__label">Возраст</label>
      </div>
      <button @click="removeChildren(index)">Удалить</button>
    </div>

    <button type="submit" @click="saveData()" class="save-btn">Сохранить</button>
  </div>
</template>

<script>
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  },
  data() {
    return {            
      data: {
        name: '',
        age: null,        
        childrens: [] 
      }    
    }
  },
  methods: {    
    saveData() {
      let parsed = JSON.stringify(this.data);
      localStorage.setItem('data', parsed)
    },
    addChildren() { 
      let children = {
        name: '',
        age: null
      }        
      this.data.childrens.push(children);               
    },
    removeChildren(index) {      
      this.data.childrens.splice(index, 1);
      this.saveData();
    }
  },
  mounted() {
    if (localStorage.data) {
      this.data = JSON.parse(localStorage.data)
    }    
  },
  watch: {
    data(newData) {
      localStorage.data = JSON.stringify(newData);
    }
  }
}
</script>
