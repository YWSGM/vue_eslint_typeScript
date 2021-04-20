<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{ name }}</h2>
    <h3>{{ text }}</h3>
    <button @click="add">哈哈</button>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Provide, Vue, Watch } from 'vue-property-decorator';

@Component
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;

  @Provide() name = 'vue';

  @Provide() count = 0;

  @Provide() text = '';

  @Provide() object = {
    age: 3
  };

  @Watch('count')
  computedCount(val: number, oldVal: number): void{
    this.text = '哈哈哈' + val + oldVal;
  }

  @Watch('object.age')
  watchAge(val: number, oldVal: number): void{
    this.text = '哈哈哈' + val + oldVal + '监视 年龄';
  }

  // method
  add(): void {
    console.log(this);
    this.count++;
    this.object.age++;
    console.log(this.count);
    this.changeName();
  }

  changeName(): void {
    this.name = '哈哈哈' + this.count;
  }

  // 生命周期
  mounted(): void {
    // alert('bbb');
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
