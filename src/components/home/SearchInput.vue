<template>
  <div id="search">
    <input type="text" placeholder="기업명을 검색하세요." v-on:keyup.enter="updateinput" />
  </div>
</template>

<script>
import companyData from '../../assets/company.json';

export default {
  name: 'search-input',
  model: {
    prop: 'item',
    event: 'keyup.enter',
  },
  props: {
    item: String,
  },
  data() {
    return {
      companyData,
    };
  },
  watch: {
    item: function () {
      console.log(this.item);
    },
  },
  methods: {
    updateinput: function ($e) {
      if (!$e.target.value) return;
      if (!Object.keys(this.companyData).includes($e.target.value.toUpperCase())) {
        if ($e.target.value === '카카오') {
          this.$emit('keyup.enter', 'KAKAO');
        } else if ($e.target.value === '삼성') {
          this.$emit('keyup.enter', 'SAMSUNG');
        } else {
          alert('기업을 찾을 수 없습니다.');
        }
      } else {
        this.$emit('keyup.enter', $e.target.value.toUpperCase());
      }
      $e.target.value = '';
    },
  },
};
</script>

<style scoped>
#search {
  font-family: Noto Sans;
  padding: 20px 16px 18px 16px;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

#result {
  display: flex;
  justify-content: space-between;
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

input {
  width: 100%;
  box-sizing: border-box;
  outline: none;
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 12px 16px;
  height: 48px;
  background: #f8f8f8;
  border: 1px solid #f2f2f2;
  border-radius: 4px;
}

input::placeholder {
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 140%;
}
</style>
