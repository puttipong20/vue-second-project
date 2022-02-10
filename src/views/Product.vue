<template>
  <v-container class="container">
    <!-- router-View -->
    <router-view 
    :details="gunList"
    :detail="gunList[0]" > </router-view>
    <!-- Product -->
    <v-container class="d-flex flex-wrap">
      <v-card
        class="mx-auto Con"
        max-width="400px"
        v-for="(gun, index) in gunList"
        :key="index"
      >
        <v-img class="white--text align-end" height="200px" :src="gun.image">
        </v-img>

        <v-card-subtitle class="pb-0">{{ gun.price }} $</v-card-subtitle>

        <v-card-text class="text--primary">
          <div>{{ gun.name }}</div>

          <div>Caliber : {{ gun.detail }}</div>
        </v-card-text>

        <v-card-actions class="buy">
          <v-btn color="black" class="btn" :to="'/productList/'+gun.id" text> Add to cart </v-btn>
        </v-card-actions>
      </v-card>
    </v-container>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      gunList: [
        {
          id:1,
          image:
            "https://cb.lnwfile.com/pvsylj.jpg",
            name: "M-16",
          detail: "5.56x45mm",
          price: 5999 ,
        },
        {
          id:2,
          image:'https://cb.lnwfile.com/q8zzgt.jpg',
          name: "AK-M",
          detail: "5.56x45mm NATO",
          price: 6000 ,
        },
        {
          id:3,
          image:'https://hk-usa.com/wp-content/uploads/1-G36C-LEFT-stock-extended-AUG-20161.jpg',
          name: "Koch G36",
          detail: "5.56x45mm ",
          price: 5800,
        },
        {
          id:4,
          image:'https://photo.weaponsystems.net/image/s-carousel/n-fa_ar_g3_p03.jpg/--/img/ws/fa_ar_g3_p03.jpg',
          name: "Koch G3",
          detail: "7.62x51mm ",
          price: 6200 ,
        },
        {
          id:5,
          image:'https://previews.123rf.com/images/snak/snak1305/snak130500514/19950798-%E3%82%B9%E3%83%86%E3%82%A2%E3%83%BC-aug-%E3%82%A2%E3%82%B5%E3%83%AB%E3%83%88%E3%83%A9%E3%82%A4%E3%83%95%E3%83%AB%E7%99%BD%E3%81%84%E8%83%8C%E6%99%AF%E3%81%A7%E9%9A%94%E9%9B%A2.jpg',
          name: "Steyr AUG",
          detail: "5.56x45mm ",
          price: 5900 ,
        },
        {
          id:6,
          image:'https://cdn.rockislandauction.com/dev_cdn/75/792.jpg',
          name: "Galil",
          detail: "5.56x45mm NATO",
          price: 5500 ,
        },
        {
          id:7,
          image:'https://iwi.net/wp-content/uploads/2017/10/tavor-tar-integral-8932.jpg',
          name: "Tavor Tar-21",
          detail: "5.56x45mm ",
          price: 6200 ,
        },
        {
          id:8,
          image:'https://cb.lnwfile.com/3n203h.jpg',
          name: "Six SG 550",
          detail: "5.56x45mm ",
          price: 5900 ,
        },
        {
          id:9,
          image:'https://f.ptcdn.info/619/036/000/nwkmxa11wuSL2nviPxk-o.jpg',
          name: "Koch HK416",
          detail: "5.56x45mm ",
          price: 6500 ,
        },
        {
          id:10,
          image:'https://cb.lnwfile.com/ch216b.jpg',
          name: "FN Scar",
          detail: "5.56x45mm ",
          price: 6500 ,
        },
        
      ],
    };
  },
};
</script>

<style>
.btn {
  border: 1px solid black;
}
.Con{
  margin: 10px;
}
</style>
