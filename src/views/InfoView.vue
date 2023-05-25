<template>
  <div class="container">
    <h2>Персональные данные</h2>
    <div v-if="parentData">
      <p class="name">{{ parentData.parentName }}, {{ parentData.parentAge }} лет</p>
      <h2 v-if="parentData.children.length > 0">Дети</h2>
      <div v-if="parentData.children.length > 0">
        <p class="turtle" v-for="(child, index) in parentData.children" :key="index">
          <span class="child-info">
            {{ child.name }}, {{ child.age }} лет
          </span>
        </p>
      </div>
    </div>
    <div v-else>
      <p>Нет сохраненных данных о родителе и детях.</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      parentData: null
    };
  },
  mounted() {
    const savedData = localStorage.getItem('parentData');
    if (savedData) {
      this.parentData = JSON.parse(savedData);
    }
  }
};
</script>

<style scoped>
.container {
  width: 616px;
  margin: 0 auto;
  padding-top: 30px;
}

P {
  text-align: left;
  font-family: 'Montserrat';
  font-style: normal;
  font-weight: 700;
  font-size: 16px;
  line-height: 24px;
}

.child-info {
  background: #F1F1F1;
  border-radius: 10px;
  padding: 10px 20px;

}

.turtle {
  margin-top: 30px;
}
</style>

