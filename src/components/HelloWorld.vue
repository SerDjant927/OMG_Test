<template>
  <div class="app">
    <div class="vertical-list">
      <div v-for="(item, index) in verticalItems" :key="index" class="vertical-item">
        <div v-for="(number, numberIndex) in item.numbers" :key="numberIndex" class="square" >
          <div class="content">
            {{ number }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      verticalItems: []
    };
  },
  mounted() {
    this.initializeVerticalList();
  },
  methods: {
    initializeVerticalList() {
      const verticalItemCount = Math.max(Math.floor(Math.random() * 100) + 1, 100);
      for (let i = 0; i < verticalItemCount; i++) {
        const horizontalItemCount = Math.floor(Math.random() * 10) + 11;
        const radius = Math.floor(Math.random() * 10) + 1;
        const numbers = Array.from({ length: horizontalItemCount }, () => Math.floor(Math.random() * 100));
        this.verticalItems.push({ numbers, radius });
      }
    },
    shrinkSquare(numberIndex) {
      const square = document.getElementsByClassName('square')[numberIndex];
      square.classList.add('shrink');
    },
    resetSquare(numberIndex) {
      const square = document.getElementsByClassName('square')[numberIndex];
      square.classList.remove('shrink');
    }
  }
};
</script>

<style>
*{
  transition: all 0.5s;
}
.app {
  display: flex;
  justify-content: center;
  align-items: center;
}

.vertical-list {
  display: flex;
  flex-direction: column;
}

.vertical-item {
  display: flex;
}

.square {
  width: 50px;
  height: 50px;
  border: 1px solid black;
  border-radius: 8px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 5px;
}

.square:hover{
  transform: scale(0.8);
}

.content {
  transition: transform 0.5s;
}


</style>