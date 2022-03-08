<template>
  <header id="header">
    <div id="left">
      <a class="icon" href="/">
        <div class="arrow"></div>
      </a>
      <span>진단결과</span>
    </div>
    <a href="/">다시 진단하기</a>
  </header>
</template>

<script>
export default {
  name: 'main-Header',
};
</script>

<style scoped>
header {
  font-family: Noto Sans;
  box-sizing: border-box;
  height: 72px;
  padding: 16px;
  width: 100%;
  display: flex;
  flex-direction: row;
  align-items: center;
  border-bottom: 1px solid lightgray;
  justify-content: space-between;
}

#left {
  display: flex;
  flex-direction: row;
}

.icon {
  position: relative;
  width: 28px;
  height: 28px;
  border-radius: 80px;
  border: 2px solid black;
  margin-right: 12px;
  cursor: pointer;
}

.icon::after {
  content: '';
  position: absolute;
  top: calc(50% - 2px);
  width: 10px;
  left: 9px;
  border-radius: 10px;
  border: 2px solid #121212;
}

.arrow::before {
  content: '';
  position: absolute;
  border: 2px solid #121212;
  border-radius: 80px 80px 0 80px;
  background-color: #121212;
  top: 34%;
  left: 5px;
  width: 7px;
  transform: rotate(135deg);
}

.arrow::after {
  content: '';
  position: absolute;
  border: 2px solid #121212;
  border-radius: 80px 80px 80px 0;
  background-color: #121212;
  top: 55%;
  left: 5px;
  width: 7px;
  transform: rotate(45deg);
}

span {
  height: 34px;
  font-weight: 700;
  font-size: 24px;
  line-height: 140%;
  color: #121212;
}

a {
  height: 22px;
  font-weight: 400;
  font-size: 16px;
  line-height: 22px;
  text-align: right;
  color: #6e3cf9;
  text-decoration: none;
}
</style>
