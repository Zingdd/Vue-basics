<template>
  <div>
    <h3>常用指令</h3>
    <!-- 绑定一段 html 元素，v-html 能识别这段 HTML 文本，一下是一个 button -->
    <p v-html="html"></p>
    <!-- 绑定一段 txt 文本，字符串，不能识别 html 元素  -->
    <p v-text="text"></p>
    <!-- v-for 遍历数组 arr， item 子元素，index 是索引，也叫作下标， -->
    <p v-for="(item,index) in arr" :key="index">
      <span>{{item}}</span>
    </p>
    <!-- v-model 双向绑定 这里用作输入框-->
    <input type="text" v-model="inputTxt">
    <p>输入了：{{inputTxt}}</p>
    <!-- v-bind 绑定，简写 :bind  这里距离绑定class , 取决于 isActive 为 true 还是 false -->
    <p v-bind:class={active:isActive}>注意文字颜色。点击下边按钮添加了类</p>
    <!-- v-on 触发事件，简写 @  ，绑定各种事件，这里是点击事件，切换上边 isActive 的状态-->
    <button @click="click"> 切换class </button>
    <!-- v-show 我们通过点击上边的按钮 来切换 isActive 的状态，控制是否显示-->
    <p v-show="isActive">我要显示 show</p>
    <!-- 这里通过 isactive 状态 来渲染if或者elese, else只有跟着if才能使用-->
    <p v-if="isActive">我是 v-if </p>
    <p v-else>我是 v-else </p>
    <!-- 全局变量 color 使用 -->
    <p :style="{color:this.Glo.globalColor}"
       :class="{isBg:this.Glo.activeBg}"
    >
      我是全局变量style属性color的值：{{this.Glo.globalColor}}
    </p>
    <!-- 全局方法的使用，细节查看 configGlobal  -->
    <button @click="this.Glo.setColor">点击调用全局方法,控制台查看</button>
    <hr>
  </div>
</template>

<script>
  export default {
    name: 'Normal',
    data() {
      return {
        html:'<button> 按钮  v-html 渲染一段 HTML文本</button>',
        text:"渲染一段字符串文本，",
        arr:[
          '数字1','数字2','数字3',
        ],
        inputTxt:'',
        isActive:false,
      }
    },
    methods:{
      click () {
        this.isActive = !this.isActive
      }
    }
  }
</script>

<style scoped>
  .active{
    color:red;
  }
</style>
