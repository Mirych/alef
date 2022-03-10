<template>
  <div class="about">    
    <h2>Персональные данные</h2>
    <p class="bold">{{ data.name + ',' + data.age }}</p>
    
    <div class="preview-childrens">
      <h2>Дети</h2>
      <div v-for="children in data.childrens" :key="children">
        <p class="child bold">
        {{ children.name + ',' + children.age }}
        </p>
    </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: {}
    }
  },
  mounted() {
    if (localStorage.data) {
      this.data = JSON.parse(localStorage.data)
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
