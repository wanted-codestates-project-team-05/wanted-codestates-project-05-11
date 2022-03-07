<template>
  <div id="result">
    <span id="text">검색 결과</span>
    <div v-if="item">
      <span id="item">{{ item }}</span>
      <button v-on:click="deleteInput">x</button>
    </div>
  </div>
</template>
<script>
export default {
  name: 'search-info',
  model: {
    prop: 'item',
    event: 'click',
  },
  props: {
    item: String,
  },
  methods: {
    deleteInput: function () {
      this.$emit('click', '');
    },
  },
};
</script>
<style>
#result {
  display: flex;
  justify-content: space-between;
  padding: 20px 16px 0 16px;
}

#result #text {
  position: relative;
  font-weight: bold;
  font-size: 16px;
  line-height: 140%;
  color: #727272;
}

#result #text::after {
  content: '';
  position: absolute;
  border: 2px solid #727272;
  background-color: #727272;
  top: 54%;
  right: -15px;
  border-radius: 10px;
  width: 7px;
  transform: rotate(135deg);
}

#result #text::before {
  content: '';
  position: absolute;
  border: 2px solid #727272;
  background-color: #727272;
  top: 30%;
  right: -15px;
  border-radius: 10px;
  width: 7px;
  transform: rotate(45deg);
}

#result div {
  display: flex;
  gap: 12px;
  align-items: center;
  justify-content: space-between;
}

#result button {
  width: 16px;
  height: 16px;
  border: none;
  border-radius: 9999px;
  background: #d2d2d2;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
}

#item {
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 20px;
  text-align: right;
  color: #727272;
}
</style>
