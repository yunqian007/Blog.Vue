<!-- 父组件 parent.vue -->

<template>
    <div class="parent">
        <h3>问卷调查</h3>
        <child ></child><!-- 注意： 这里已经没有 .sync 了 -->
        <div class="">
            <br>
            <br>
            <p>数据：{{_fatherData}}</p>
        </div>
    </div>
</template>

<script>
import child from "../components/dialogVuex.vue";

export default {
  components: {
    child
  },
  data: function() {
    return {
      form: {
        name: "",
        namePla: "姓名不能为空",
        address: "",
        age: ""
      }
    };
  },
  computed: {//挂载完成后
    _fatherData() {//获取全局 store 仓库中的 formDatas 值
      // 读取store里面的值，这里是重点
      return this.$store.state.formDatas;
    }
  }
};
</script>