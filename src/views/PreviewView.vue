<template>
  <div class="about">    
    <h2>Персональные данные</h2>
    <p class="bold">{{ profile.name + ', ' + profile.age }}</p>
    
    <div class="preview-childrens">
      <h2>Дети</h2>
      <div v-for="children in profile.childrens" :key="children">
        <p class="child bold">
        {{ children.name + ', ' + children.age }}
        </p>
    </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      profile: {}
    }
  },
  mounted() {
    if (localStorage.profile) {
      this.profile = JSON.parse(localStorage.profile)
    }    
  },
}
</script>
<style>
.bold {
  font-weight: 700;
  font-size: 16px;
}
.preview-childrens {
  margin-top: 60px;
}
.child {
  display: inline-block;
  padding: 10px 20px;
  background-color: #F1F1F1;
  border-radius: 5px;
}
</style>
