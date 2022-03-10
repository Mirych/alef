<template>
  <div class="home">        
    <h2>Персональные данные</h2>
    <div class="text-field text-field_floating adult">
      <input type="text" id="name" v-model="profile.name" class="text-field__input">
      <label for="name" class="text-field__label">Имя</label>
    </div>
    <div class="text-field text-field_floating adult">
      <input type="number" id="age" v-model="profile.age" class="text-field__input">
      <label for="age" class="text-field__label">Возраст</label>
    </div>

    <div class="add-childrens">
      <h2>Дети (макс.5)</h2>
      <button v-show="profile.childrens.length < 5" @click="addChildren()">
        <img src="../assets/plus.svg" alt="plus">
        Добавить ребенка
        </button>    
    </div>
    <div v-for="(children, index) in profile.childrens" :key="index" class="childrens">   
      <div class="text-field text-field_floating">       
        <input type="text" v-model="children.name" required class="text-field__input">
        <label for="name" class="text-field__label">Имя</label>
      </div>
      <div class="text-field text-field_floating childrens">
        <input type="number" v-model="children.age" required class="text-field__input">
        <label for="age" class="text-field__label">Возраст</label>
      </div>
      <button @click="removeChildren(index)">Удалить</button>
    </div>

    <button type="submit" @click="saveProfile()" class="save-btn">Сохранить</button>
  </div>
</template>

<script>

export default {
  name: 'HomeView',
  data() {
    return {            
      profile: {
        name: '',
        age: null,        
        childrens: [] 
      }    
    }
  },
  methods: {    
    saveProfile() {
      let profileJson = JSON.stringify(this.profile);
      localStorage.setItem('profile', profileJson)
    },
    addChildren() { 
      let children = {
        name: '',
        age: null
      }        
      this.profile.childrens.push(children);               
    },
    removeChildren(index) {      
      this.profile.childrens.splice(index, 1);
      this.saveProfile();
    }
  },
  mounted() {
    if (localStorage.profile) {
      this.profile = JSON.parse(localStorage.profile)
    }    
  },
  watch: {
    profile(newProfile) {
      localStorage.profile = JSON.stringify(newProfile);
    }
  }
}
</script>
