# wxc-lottery-rain
      
> Weex 版本的红包雨游戏

- 规则
  - 一般在营销活动中使用，类似于捉猫猫、打地鼠这种场景
  - 元素图片、容器样式可以配置中成当前活动氛围一致，记得处理config中的图片高宽
   
-----

## [Demo预览](https://h5.m.taobao.com/trip/wxc-lottery-rain/index.html?_wx_tpl=https%3A%2F%2Fh5.m.taobao.com%2Ftrip%2Fwxc-lottery-rain%2Fdemo%2Findex.native-min.js)
<img src="https://gw.alipayobjects.com/zos/rmsportal/vYUYcbOmIaxTEvRWcOis.gif" width="240"/>&nbsp;&nbsp;&nbsp;&nbsp;<img src="http://gtms04.alicdn.com/tfs/TB1MciTdwMPMeJjy1XbXXcwxVXa-200-200.png" width="160"/>

## 安装

```
tnpm install weex-ui --save
```

## 使用方法

```
<template>
  <wxc-lottery-rain :config="config"
                    :pic-list="images"
                    ref="wxc-lottery-rain"
                    :wrap-style="wrapStyle"
                    @wxcLotteryRainCaught="wxcLotteryRainCaught"></wxc-lottery-rain>
</template>

<style scoped>

</style>

<script>
  import { WxcLotteryRain } from 'weex-ui';
  export default {
    components: { WxcLotteryRain },
    data: () => ({
      images: [
       'http://gtms03.alicdn.com/tfs/TB1sZPlb5IRMeJjy0FbXXbnqXXa-241-206.png',
       'http://gtms03.alicdn.com/tfs/TB1eCbwb3MPMeJjy1XcXXXpppXa-241-206.png',
       'http://gtms02.alicdn.com/tfs/TB1rDTjb3MPMeJjy1XdXXasrXXa-241-206.png',
       'http://gtms04.alicdn.com/tfs/TB1Nw2sb3MPMeJjy1XbXXcwxVXa-241-206.png',
       'http://gtms04.alicdn.com/tfs/TB1hCbwb3MPMeJjy1XcXXXpppXa-241-206.png'
      ],
      config: {
        intervalTime: 450,
        hideAniTime: 300,
        showAniTime: 300,
        showTime: 450,
        randomTime: 300,
        width: 241,
        height: 206
      },
      wrapStyle: {
        backgroundColor: 'rgba(133, 11, 11, .7)'
      }
    }),
    methods: {
      wxcLotteryRainCaught (e) {
        // console.log(e.rainId)
      }
    }
  }
</script>

```

### 可配置参数

| 名称      | 类型     | 默认值   | 备注  |
|-------------|------------|--------|-----|
| pic-list | `Array` | `[]` |定制化图片配置|
| config | `Object` | `{}` | 红包雨相关配置，默认为[config] |
| wrap-style | `Object` | `{}` | 红包雨容器样式自定义 |

### 事件回调

```
//被抓住时候的一个回调
@wxcLotteryRainCaught="wxcLotteryRainCaught"
同时e.rainId为被抓住的id
```

### 销毁api
- 我们在游戏结束或者用户切走时候建议销毁`红包雨`动画、定时器等影响性能的东西，此处提供方法为：

```
//绑定wxc-lottery-rain组件的 ref="wxc-lottery-rain"
//调用内部方法destroy进行销毁
this.$refs['wxc-lottery-rain'].destroy();
```
