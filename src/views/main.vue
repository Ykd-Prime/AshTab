<template>
  <div id="ash">
    <div class="main" :class="{'active':active}" :style="{'background-image':'url('+bg+')'}">
      <div class="link" style="fontSize:30px">
        <a :href="link[0].link">{{link[0].name}}</a>
      </div>
      <div class="content">
        <div class="middle">
          <sh-time></sh-time>
        </div>
        <sh-search></sh-search>
      </div>
    </div>
    <sh-menu :status="active" @status="status"></sh-menu>
  </div>
</template>

<script>
import shMenu from './menu.vue'
import shTime from '../components/shtime.vue'
import shSearch from '../components/shsearch.vue'
export default {
  data () {
    return {
      active: false,
      link: [//需要放入外部json
        {name:'bibilili', link:'https://www.bilibili.com'}
      ],
      bg: require('../assets/59289921_p0.jpg')
    };
  },
  methods: {
    status(i) {
      this.active = i.active
    },

    cn(i) {
      console.log(i)
    },


  },
  computed: {

  },
  components: {
    shMenu,shTime,shSearch
  },



  mounted() {
    this.cn(this.bg)
  }
}

</script>
<style lang="scss" scoped>
%flexjc {
  display: flex;
  justify-content: center
}

.main {
  position: relative;
  width: 100vw;
  height: 100vh;
  @extend %flexjc;
  flex-direction: column;
  align-items: center;
  overflow: hidden;
  background-position:center center;
  transform: translateX(0px)
}

.link {
  position: absolute;
  top: 0;
  right: 0;
  left: 0;
  text-align: center;
  a {
    text-decoration: none;
    color: rgba(250, 250, 250, 0.705);
    &:hover {
      color: rgba(250, 250, 250, 1)
    }
  }
}

.content {
  justify-content: center;

  .middle {
    @extend %flexjc;

  }
}

.main.active {
  transform: translateX(-280px)
}

@media (max-width: 800px) {
  .main.active {
    transform: translateX(-101vw)
  }
}


</style>