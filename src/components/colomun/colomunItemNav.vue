<template>
  <div class="colomun-Item-Nav"  >
    <ul class="Item-ul" @mouseleave="MouseOut">
      <li v-for="(item,index) in items" :key="index" @mouseover="MouseOver(index)"  :class="{'active':currentIndex===index}">
        <a href="">{{item}}
          <i class="fas fa-angle-right"></i>
        </a>
      </li>
      <colomun-item-menu :good="goods[currentIndex]" v-if="currentIndex!==-1" ></colomun-item-menu>
    </ul>
  </div>
</template>

<script>
import colomunItemMenu from "@/components/colomun/colomunItemMenu";
export default {
  name: "colomunItemNav",
  props:{
    isOut:false
  },
  data(){
    return {
      items:['手机 电话卡','电视 盒子','笔记本 平板','家电 插线板','出行 穿戴','智能 路由器','电源 配件','健康 儿童','耳机 音箱','生活 箱包'],
      currentIndex:-1,
      goods:[
        [
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},

        ],
        [
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
        ],
        [
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
        ],
        [
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},


        ],
        [
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},

        ],
        [
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
        ],
        [
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},

        ],
        [
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},


        ],
        [
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
        ],
        [
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'  },
          {name:'Xiaomi MIX FOLD',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab345272bf9894bb8269d4901344b068.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi 11 Ultra',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1241b5a94ba1739e85f72d46592af0e.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 Pro 系列",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a95d59ec8c9c6ae7061f314eb4901e7c.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:"Note 11 4G",url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e2c570b7cd666114a7d351a1dd10a527.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Note 11 5G',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ca3caca774dc8be0a453c90d1fa58e13.png?thumb=1&w=50&h=50&f=webp&q=90',},
          {name:'Redmi K40',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/92fdd051100722d25323e9bd188befc5.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi Civi',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f33903e1162959f500360a39896f2306.png?thumb=1&w=50&h=50&f=webp&q=90'},
          {name:'Xiaomi MIX 4',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/fa2bae1f43611e80a8e4877719c76bdb.png?thumb=1&w=50&h=50&f=webp&q=90'},

        ]
      ],
      isShow:false,
      isMouseOut:true,
    }
  },
  methods:{
    MouseOver(index){
      this.currentIndex=index
      this.isShow=true
    },
    MouseOut() {
      // console.log('out')
      this.currentIndex=-1
    },
  },
  components:{
    colomunItemMenu
  }
}
</script>

<style scoped>
 .colomun-Item-Nav{
   padding:20px 0;
   background-color:rgba(0,0,0,.6);
   color:white;
   height: 460px;
   width: 234px;
 }
 .active{
   background-color: #FF6700;
 }
 .Item-ul li{
   line-height: 42px;
   height: 42px;
   padding:0 30px;
   position: relative;
 }
 .Item-ul a{
   display: block;
   color:white;
 }
 .Item-ul i{
      position: absolute;
      right: 32px;
      top: 14px;
 }
</style>