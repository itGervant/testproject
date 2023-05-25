<template>
  <div class="main">
    <div class="personal">
      <h2>Персональные данные</h2>
      <div class="parent">
        <div class="parent-input">
          <input type="text" id="name-input" v-model="parentName" class="name-input" />
          <div class="input-span">Имя</div>
        </div>
        <div class="parent-input">
          <input type="text" id="name-input" v-model.number="parentAge" class="name-input" />
          <div class="input-span">Возраст</div>
        </div>
      </div>
    </div>

    <div class="children">
      <div class="child-title">
        <h2>Дети (макс. 5)</h2>
        <button class="addBtn" @click="addChild" v-if="children.length < 5"><img src="../assets/plus.svg"><span
            class="childBtn">Добавить ребенка</span></button>
      </div>

      <div class="child-inputs" v-for="(child, index) in children" :key="index">
        <div class="child-input">
          <input type="text" v-model="child.name" class="child" />
          <div class="input-span">Имя</div>
        </div>
        <div class="child-input">
          <input type="text" v-model.number="child.age" class="child" />
          <div class="input-span">Возраст</div>
        </div>
        <a class="deleteBtn" @click="removeChild(index)">Удалить</a>
      </div>
    </div>
    <div class="button">
      <a class="saveBtn" @click="saveData"><span>Сохранить</span></a>
    </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      parentName: '',
      parentAge: null,
      children: []
    };
  },
  methods: {
    addChild() {
      this.children.push({ name: '', age: null });
      console.log(this.children.length)
    },
    removeChild(index) {
      this.children.splice(index, 1);
    },
    saveData() {
      const data = {
        parentName: this.parentName,
        parentAge: this.parentAge,
        children: this.children
      };

      localStorage.setItem('parentData', JSON.stringify(data));

      this.parentName = '';
      this.parentAge = null;
      this.children = [];
    }
  }
};
</script>

<style>
.main {
  flex: 1 1 auto;
}

.personal {
  padding-top: 30px;
  margin: 0 auto;
  width: 616px;
}

.parent .parent-input {
  width: 616px;
  height: 56px;
  background: #FFFFFF;
  border: 1px solid #F1F1F1;
  border-radius: 4px;
  margin-top: 10px;
}

.parent-input:focus-within {
  border: 1px solid blue;
}

.children {
  padding-top: 30px;
  width: 616px;
  margin: 0 auto;
}

.child-title {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.child-inputs {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.child-input {
  width: 260px;
  height: 56px;
  background: #FFFFFF;
  border: 1px solid #F1F1F1;
  border-radius: 4px;
  margin-top: 10px;
}

.child-input:focus-within {
  border: 1px solid blue;
}

.addBtn {
  box-sizing: border-box;
  display: flex;
  align-items: center;
  padding: 10px 20px;
  width: 204px;
  height: 44px;
  background-color: transparent;
  color: #01A7FD;
  border: 2px solid #01A7FD;
  border-radius: 100px;
  cursor: pointer;
}

.deleteBtn {
  color: #01A7FD;
  cursor: pointer;
  margin-top: 10px;
}

.saveBtn {
  margin-top: 30px;
  display: flex;
  align-items: center;
  justify-content: center;


  width: 118px;
  height: 44px;
  color: #FFFFFF;
  background: #01A7FD;
  border-radius: 100px;
}

span {
  font-size: 14px;
}

.button {
  display: flex;
  width: 616px;
  margin: auto;
  justify-content: start;
}

.input-container {
  position: relative;
  width: 616px;
  height: 56px;
  background: #FFFFFF;
  border: 1px solid #F1F1F1;
  border-radius: 4px;
  margin-top: 10px;
}

.name-input {
  position: relative;
  width: 580px;
  height: 20px;
  margin-top: 30px;
  border: none;
  outline: none;
  bottom: 0;
}

.input-span {
  position: relative;
  top: -48px;
  margin-left: 16px;
  text-align: left;
  font-family: 'Montserrat';
  font-style: normal;
  font-weight: 400;
  font-size: 13px;
  line-height: 16px;
  color: rgba(17, 17, 17, 0.48);

}

.child {
  width: 228px;
  position: relative;
  height: 20px;
  margin-top: 30px;
  border: none;
  outline: none;
  bottom: 0;
}

h2 {
  text-align: left;
  font-family: 'Montserrat';
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 24px;
  margin: 0;
}

img {
  margin-right: 8px;
}

input {
  font-family: 'Montserrat';
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 24px;
  color: #111111;
}
</style>

