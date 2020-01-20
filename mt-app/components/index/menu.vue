<template>
  <div class="m-menu">
    <dl class="nav" @mouseleave="mouseleave">
      <dt>全部分类</dt>
      <dd v-for="(item, idx) in menu" :key="idx" @mouseenter="mouseenter">
        <i :class="item.type" />{{ item.name }}<span class="arrow" />
      </dd>
    </dl>
    <div class="detail" v-if="kind" @mouseenter="sover" @mouseleave="sout">
      <template v-for="(item, idx) in curdetail.child">
        <h4 :key="idx">{{ item.title }}</h4>
        <span v-for="v in item.child" :key="v">{{ v }}</span>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      kind: "",
      menu: [
        {
          type: "food",
          name: "美食",
          child: [
            {
              title: "美食",
              child: ["代金券", "甜点", "自助餐"]
            }
          ]
        },
        {
          type: "takeout",
          name: "外卖",
          child: [
            {
              title: "外卖",
              child: ["美团外卖"]
            }
          ]
        },
        {
          type: "hotel",
          name: "酒店",
          child: [
            {
              title: "酒店星级",
              child: ["经济型", "舒适/三星", "高档/四星"]
            }
          ]
        }
      ]
    };
  },
  methods: {
    mouseleave: function() {
      this._timer = setTimeout(() => {
        this.kind = "";
      }, 150);
    },
    mouseenter: function(e) {
      this.kind = e.target.querySelector("i").className;
    },
    sover: function(e) {
      clearTimeout(this._timer);
    },
    sout: function(e) {
      this.kind = "";
    }
  },
  computed: {
    curdetail: function() {
      console.log(this.menu);
      console.log(this.kind);
      //   this.menu.filter(item => {
      //     return item.type === this.kind;

      //   });
      return this.menu.filter(item => {
        return item.type === this.kind;
      })[0];
    }
  }
};
</script>

<style></style>
