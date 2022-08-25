<template>
  <div>
    <h1>第一题</h1>
    <h4 class="center"  >欢迎光临_vue开发的收银系统_水果店</h4>
    <table class="center" border="1">
      <th>
        <td>苹果10￥/斤，折扣8折</td>
      </th>
      <tr>
        <td>确认你要购买的斤数<input type="text" v-model.number="weight"></td>
      </tr>
      <tr>
        <button @click="sumPrice">结账买单~</button>
      </tr>
      <tr>
        结账单：总价{{price}}￥元 省了：{{dPrice}}￥元
      </tr>
    </table>
    <br><br><br>
    <h1>第二题</h1>
     <input type="checkbox" value="科幻" v-model="arr">科幻
     <input type="checkbox" value="喜剧" v-model="arr">喜剧
     <input type="checkbox" value="动漫" v-model="arr">动漫
     <input type="checkbox" value="冒险" v-model="arr">冒险
     <input type="checkbox" value="科技" v-model="arr">科技
     <input type="checkbox" value="军事" v-model="arr">军事
     <input type="checkbox" value="娱乐" v-model="arr">娱乐
     <input type="checkbox" value="奇闻" v-model="arr">奇闻
     <ul>
      <li v-for="item,index in arr" :key="index">{{item}}</li>
     </ul>
    <br><br><br>
    <h1>第三题</h1>
    <div>
    <p>请选择你要购买的书籍</p>
    <ul>
      <li v-for="item,index in bookArr" :key="index">
        {{item.name}}<button @click="numchange(index)">买书</button>
      </li>
    </ul>
    <table border="1" width="500" cellspacing="0">
      <tr>
        <th>序号</th>
        <th>书名</th>
        <th>单价</th>
        <th>数量</th>
        <th>合计</th>
      </tr>
      <tr v-for="item,index in bookArr" :key="index">
        <td>{{index+1}}</td><td>{{item.name}}</td><td>{{item.price}}</td>
        <td>{{item.count}}</td>
        <td>{{item.count*item.price}}</td>
      </tr>
    </table>
    <p>总价格为: {{bookSumprice}}</p>
  </div>
  <br><br><br>
  <h1>第四题</h1>
  <input type="checkbox" value="9" v-model="sum">9
  <input type="checkbox" value="15" v-model="sum">15
  <input type="checkbox" value="19" v-model="sum">19
  <input type="checkbox" value="25" v-model="sum">25
  <input type="checkbox" value="29" v-model="sum">29
  <input type="checkbox" value="31" v-model="sum">31
  <input type="checkbox" value="48" v-model="sum">48
  <input type="checkbox" value="57" v-model="sum">57
  <input type="checkbox" value="62" v-model="sum">62
  <input type="checkbox" value="79" v-model="sum">79
  <input type="checkbox" value="87" v-model="sum">87
  <h4>你选中的元素累加和为{{sumArr}}</h4>
  </div>
</template>

<script>
export default {
  data() {
    return {
      //水果初识斤数
      weight:'',
      //水果初识总额
      price:'',
      //水果折扣省钱数
      dPrice:'',
      //每种书本初识总额数据
      a:0,
      //第二题空数组数据
      arr:[],
      // 买点书练习数据
      bookArr: [
        {
          name: "水浒传",
          price: 107,
          count: 0,
        },
        {
          name: "西游记",
          price: 192,
          count: 0,
        },
        {
          name: "三国演义",
          price: 219,
          count: 0,
        },
        {
          name: "红楼梦",
          price: 178,
          count: 0,
        },
      ],
      //点你爱我求和数据
      sum: []
    };
  },
  computed:{
    //书本总额计算
   bookSumprice(){
      return this.bookArr.reduce((sum, obj) => {
        return (sum += obj["price"] * obj["count"]);
      }, 0);
    },
    //点你爱我求和计算
    sumArr(){
      if(this.sum.length !== 0) return this.sum.map(Number).reduce((sum, obj) => sum + obj)
      if(this.sum.length === 0) return 0
    }
  },
  methods:{
    //水果价格方法
    sumPrice(){
        this.price= this.weight*10*0.8
        this.dPrice= this.weight*10*0.2
    },
    //每种书本总计价格方法
    numchange(index){
        this.bookArr[index].count++
        this.a=this.bookArr[index]*(this.bookArr[index].count)
    }
  }
};
</script>
<style scoped>
.center{
  text-align: center;
  margin: 0 auto;
}
</style>
