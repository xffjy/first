<template>
  <div>
    <table>
      <tr>
        <th>商品名称</th>
        <th>商品单价</th>
        <th>商品个数</th>
        <th>小计</th>
        <th>操作</th>
      </tr>
      <tr v-for="(item, index) in arr" :key="item.id">
        <td>{{ item.name }}</td>
        <td>{{ item.price }}</td>
        <td>
          <button :disabled="item.num == 1" @click="item.num--">-</button>
          <span>{{ item.num }}</span>
          <button @click="item.num++">+</button>
        </td>
        <td>{{ item.price * item.num }}</td>
        <td><button @click="clickdel(index)">删除</button></td>
      </tr>
      <h2>总价：{{ total() }}元</h2>
      <h3>总价：{{a}}</h3>
    </table>
  </div>
  <div>你是猪</div>
</template>

<script>
export default {
  data() {
    return {
      arr: [
        { id: 1, name: "电视", price: 2000, num: 1 },
        { id: 2, name: "洗衣机", price: 500, num: 2 },
        { id: 3, name: "空调", price: 3000, num: 1 },
        { id: 4, name: "自行车", price: 200, num: 3 },
        { id: 5, name: "小车", price: 10000, num: 1 },
        { id: 6, name: "电脑", price: 50000, num: 5 },
      ],
    };
  },
  methods: {
    // 删除每一条数据
    clickdel(val) {
      this.arr.splice(val, 1);
    },
     total() {
      let tota = 0;
      for (let obj of this.arr) {
        tota += obj.price * obj.num;
        console.log(obj.price)
      }
      return tota;
    },
  },
  computed:{
    a(){
      let tota = 0;
      for (let obj of this.arr) {
        tota += obj.price * obj.num;
        console.log(obj.price)
      }
      return tota;
    }
  }
};
</script> 

<style scoped>
</style>