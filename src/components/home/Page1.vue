<template>
  <div class="home-page page1">
    <div class="home-page-wrapper" id="page1-wrapper">
      <div class="page1-bg" style="transform: translate(0px, 200.953px);">Feature</div>
      <h2>What can <span>Pro</span> do for you </h2>
      <div class="title-line-wrapper page1-line"></div>
      <list :data-source="features" />
    </div>
  </div>
</template>

<script>
import List from '@/components/home/List'
import config from '@/config/default.config'
import { mixin } from '@/store/mixin'
const featuresCN = [
  {
    title: '优雅美观',
    content: '基于 Ant Design 体系精心设计',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/VriUmzNjDnjoFoFFZvuh.svg',
    color: '#13C2C2',
    shadowColor: 'rgba(19,194,194,.12)'
  },
  {
    title: '常见设计模式',
    content: '提炼自中后台应用的典型页面和场景',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/smwQOoxCjXVbNAKMqvWk.svg',
    color: '#2F54EB',
    shadowColor: 'rgba(47,84,235,.12)'
  },
  {
    title: '最新技术栈',
    content: '使用 Vue/vuex/antd 等前端前沿技术开发',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/hBbIHzUsSbSxrhoRFYzi.svg',
    color: '#F5222D',
    shadowColor: 'rgba(245,34,45,.12)'
  },
  {
    title: '响应式',
    content: '针对不同屏幕大小设计',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/BISfzKcCNCYFmTYcUygW.svg',
    color: '#1AC44D',
    shadowColor: 'rgba(26,196,77,.12)'
  },
  {
    title: '主题',
    content: '可配置的主题满足多样化的品牌诉求',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/XxqEexmShHOofjMYOCHi.svg',
    color: '#FAAD14',
    shadowColor: 'rgba(250,173,20,.12)'
  },
  {
    title: '国际化',
    content: '内建业界通用的国际化方案',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/JsixxWSViARJnQbAAPkI.svg',
    color: '#722ED1',
    shadowColor: 'rgba(114,46,209,.12)'
  },
  {
    title: '最佳实践',
    content: '良好的工程实践助你持续产出高质量代码',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/pbmKMSFpLurLALLNliUQ.svg',
    color: '#FA8C16',
    shadowColor: 'rgba(250,140,22,.12)'
  },
  {
    title: 'Mock 数据',
    content: '实用的本地数据调试方案',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/aLQyKyUyssIUhHTZqCIb.svg',
    color: '#EB2F96',
    shadowColor: 'rgba(235,45,150,.12)'
  },
  {
    title: 'UI 测试',
    content: '自动化测试保障前端产品质量',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/RpJIQitGbSCHwLMimybX.svg',
    color: '#1890FF',
    shadowColor: 'rgba(24,144,255,.12)'
  }
]

const featuresEN = [
  {
    title: ' Neat Design',
    content: 'Follow Ant Design specification',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/VriUmzNjDnjoFoFFZvuh.svg',
    color: '#13C2C2',
    shadowColor: 'rgba(19,194,194,.12)'
  },
  {
    title: 'Common Templates',
    content: 'Typical templates for enterprise applications',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/smwQOoxCjXVbNAKMqvWk.svg',
    color: '#2F54EB',
    shadowColor: 'rgba(47,84,235,.12)'
  },
  {
    title: 'Up-to-date Dev Stack',
    content: 'Newest development stack of Vue/vuex/antd',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/hBbIHzUsSbSxrhoRFYzi.svg',
    color: '#F5222D',
    shadowColor: 'rgba(245,34,45,.12)'
  },
  {
    title: 'Responsive',
    content: 'Designed for varies of screen size',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/BISfzKcCNCYFmTYcUygW.svg',
    color: '#1AC44D',
    shadowColor: 'rgba(26,196,77,.12)'
  },
  {
    title: 'Theming',
    content: 'Customizable theme with simple config',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/XxqEexmShHOofjMYOCHi.svg',
    color: '#FAAD14',
    shadowColor: 'rgba(250,173,20,.12)'
  },
  {
    title: 'International',
    content: 'Built-in i18n solution',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/JsixxWSViARJnQbAAPkI.svg',
    color: '#722ED1',
    shadowColor: 'rgba(114,46,209,.12)'
  },
  {
    title: 'Best Practice',
    content: 'Solid workflow make your code health',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/pbmKMSFpLurLALLNliUQ.svg',
    color: '#FA8C16',
    shadowColor: 'rgba(250,140,22,.12)'
  },
  {
    title: 'Mock Data',
    content: 'Easy to use mock development solution',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/aLQyKyUyssIUhHTZqCIb.svg',
    color: '#EB2F96',
    shadowColor: 'rgba(235,45,150,.12)'
  },
  {
    title: 'UI Test',
    content: 'Fly safely with unit test and e2e test',
    src: 'https://gw.alipayobjects.com/zos/rmsportal/RpJIQitGbSCHwLMimybX.svg',
    color: '#1890FF',
    shadowColor: 'rgba(24,144,255,.12)'
  }
]

export default {
  name: 'Page1',
  mixins: [mixin],
  components: {
    List
  },
  data () {
    return {
      features: []
    }
  },
  created () {
    this.updateFeatures()
  },
  methods: {
    updateFeatures () {
      const arr = (this.currentLang === config.defaultLang ? featuresEN : featuresCN)
      let newArr = [[], [], []]
      arr.forEach((item, index) => {
        newArr[Math.floor(index / 3)].push(item)
      })
      this.features = newArr
    }
  },
  watch: {
    currentLang (val) {
      console.log('currentLang:', val)
      this.updateFeatures()
    }
  }
}
</script>
