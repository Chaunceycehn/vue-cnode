<template>
    <div    class="Pagination">
        <button @click="changebtn"> 首页</button>
        <button @click="changebtn"> 上一页</button>
        <button @click="changebtn" v-if="jduge"> ...</button>
        <button v-for=" (btn,index) in pagebtn" 
        @click="changebtn(btn)"
        :key="index" 
        :class="[{'currentpage':btn==currentpage},'pagebtn']">{{btn}}</button>
        <button @click="changebtn"> 下一页</button>
    </div>
</template>

<script>
import $ from "jquery";

export default {
  name: "Pagination",
  data() {
    return {
      pagebtn: [1, 2, 3, 4, 5, "..."],
      currentpage: 1,
      jduge: false
    };
  },
  methods: {
    changebtn(page) {
      //d点击上一页，下一页
      if (typeof page != "number") {
        switch (page.target.innerText) {
          case "上一页":
            $("button.currentpage")
              .prev()
              .click();
            break;
          case "下一页":
            $("button.currentpage")
              .next()
              .click();
            break;
          case "首页":
            (this.pagebtn = [1, 2, 3, 4, 5, "..."]), this.changebtn(1);
            break;
          default:
            break;
        }
        return;
      }
      this.currentpage = page;
      if (page > 4) {
        this.jduge = true;
      } else {
        this.jduge = false;
      }
      if (page === this.pagebtn[4]) {
        this.pagebtn.shift();
        this.pagebtn.splice(4, 0, this.pagebtn[3] + 1);
      } else if (page === this.pagebtn[0] && page != 1) {
        this.pagebtn.unshift(this.pagebtn[0] - 1);
        this.pagebtn.splice(5, 1);
      }
    this.$emit('handlelist',this.currentpage);

    },
  }
};
</script>

<style scoped>
.pagination {
  margin-top: 5px;
  margin-bottom: 20px;
  background-color: white;
  padding: 6px 20px;
  border-radius: 5px;
  /*box-shadow: 0px 2px 9px #888888;*/
  border: 1px solid #888888;
}

button {
  background-color: #fff;
  border: 1px solid #ddd;
  color: #778087;
  border-radius: 3px;
  outline: none;
  height: 21px;
  cursor: pointer;
  padding: 0 2px;
  width: 55px;
  height: 29px;
}

.pagebtn {
  position: relative;
  bottom: 1px;
  width: 40px;
  margin: 0 4px;
}

.currentpage {
  color: white;
  background-color: #1f1b1b;
}
</style>
