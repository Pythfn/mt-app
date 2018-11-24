<template>
  <div class="m-menu">
    <dl class="nav">
      <dt>全部分类</dt>
      <dd
        v-for="(item, index) of menu"
        :key="index"
        @mouseenter="menter"
        @mouseleave="mleave"
      >
      <i :class="item.type"/>{{ item.name }}<span class="arrow"/></dd>
    </dl>
    <div
      v-if="kind"
      class="detail"
      @mouseenter="mdenter"
      @mouseleave="mleave">
      <template
        v-for="(child, index) of handleMenu.child">
        <h4 :key="index">{{ child.title }}</h4>
        <span
          v-for="list of child.child"
          :key="list">{{ list }}</span>
      </template>

    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      kind:'',
      timer:'',
      menu: [{
        type: 'food',
        name: '美食',
        child: [{
          title: '美食',
          child: ['代金券', '甜点饮品', '火锅', '自助餐', '小吃快餐']
        }]
      }, {
        type: 'takeout',
        name: '外卖',
        child: [{
          title: '外卖',
          child: ['美团外卖']
        }]
      }, {
        type: 'hotel',
        name: '酒店',
        child: [{
          title: '酒店星级',
          child: ['经济型', '舒适/三星', '高档/四星', '豪华/五星']
        },
        ]
      },{
        type: 'movie',
        name: '猫眼电影',
        child: [{
          title: '热映电影',
          child: ['无敌破坏王2','毒液：致命守护者','憨豆特工3','神奇动物：格林德沃之罪']
        },{
          title: '热门影院',
          child: ['耀莱成龙国际影城','保利国际影城大地影院','万达影城博纳国际影城','CGV影城橙天嘉禾影城']
        }
        ]
      }]

    }
  },
  computed:{
    handleMenu(){
      const temp = this.menu.filter((e) => {return e.type == this.kind});
      //filter json筛选器返回的是数组，所以需要用下标定位
      return temp[0];
    }

  },
  methods:{
    menter(e){
      clearTimeout(this.timer)
      this.kind = e.target.querySelector('i').className;
      //console.log(this.kind);
    },
    mleave(){
      this.timer = setTimeout(() => {
        this.kind = ''
      },200)
    },
    mdenter(){
      clearTimeout(this.timer)
    }

  }
}

</script>
