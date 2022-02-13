<template>
  <v-container>
    <center><h2>-</h2></center>
    <center><h1>Product Page</h1></center>
    <v-container class="d-flex flex-wrap">
      <v-card
        class="mx-auto mb-5"
        max-width="400"
        v-for="(i, index) in productlist"
        :key="index"
      >
        <v-img class="white--text align-end" height="200px" :src="i.imageurl">
          <v-card-title>{{ i.name }}</v-card-title>
        </v-img>

        <v-card-subtitle class="pb-0">{{ i.rightText }}</v-card-subtitle>

        <v-card-text class="text--primary">
          <div>{{ i.leftText }}</div>
        </v-card-text>

        <v-card-actions>
          <v-btn color="info" text :to="'/detail/'+i.name">detail</v-btn>
          <v-btn color="orange" text> Add </v-btn>
          <div class="card-footer">
            <input type="checkbox" class="form-control" @change="selected(i)">
          </div>
        </v-card-actions>        
      </v-card>
    </v-container>
    <v-container><h4>ยอดชำระเงิน {{total()}} บาท </h4></v-container>
    <v-container grid-list-xs class="yellow">
      <router-view :key="$route.path"></router-view>
    </v-container>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      productlist: [
        {
          name: "KITO Move TwoTone AH81 (white&red)",
          imageurl:
            "https://www.kito.co.th/wp-content/uploads/2020/09/Kito-Move-TWOTONE-A-scaled.jpg",
          rightText: "price : 199",
          leftText: "Size : EU 31-45",
          producturl:
            "https://www.kito.co.th/product/move-twotone-ah81/",
          rightUrl: "https://www.kito.co.th/product-category/women/women-sandals/",
          ctaText: "Shop Now",
          active:false,
          price:199,
        },

        {
          name: "KITO Move TwoTone AH81 (purple&white)",
          imageurl:
            "https://www.kito.co.th/wp-content/uploads/2021/07/Kito-MoveTwoTone-Ultra-Violet.jpg",
          rightText: "price : 199",
          leftText: "Size : EU 31-45",
          producturl:
            "https://www.kito.co.th/product/move-twotone-ah81/",
          rightUrl: "https://www.kito.co.th/product-category/women/women-sandals/",
          ctaText: "Shop Now",
          active:false,
          price:199,
        },

        {
          name: "KITO Move TwoTone AH81 (pink&black)",
          imageurl:
            "https://www.kito.co.th/wp-content/uploads/2020/09/Kito-MoveTwoTone-AH81-Pink-A-1024x1024.jpg",
          rightText: "price : 199",
          leftText: "Size : EU 31-45",
          producturl:
            "https://www.kito.co.th/product/move-twotone-ah81/",
          rightUrl:"https://www.kito.co.th/product-category/women/women-sandals/",
          ctaText: "Shop Now",
          active:false,
          price:199,
        },

        {
          name: "KITO Move TwoTone AH81 (bule&yellow)",
          imageurl:
            "https://www.kito.co.th/wp-content/uploads/2021/01/Kito-Move-TwoTone-AH81-BlueYellow-A-1024x1024.jpg",
          rightText: "price : 199",
          leftText: "Size : EU 31-45",
          producturl:
            "https://www.kito.co.th/product/move-twotone-ah81/",
          rightUrl: "https://www.kito.co.th/product-category/women/women-sandals/",
          ctaText: "Shop Now",
          active:false,
          price:199,
        },

        {
          name: "KITO Move TwoTone AH81 (grey&yellow)",
          imageurl:
            "https://www.kito.co.th/wp-content/uploads/2020/09/Kito-MoveTwoTone-AH81-Ultimate-Gray-illuminating-1024x1024.jpg",
          rightText: "price : 199",
          leftText: "Size : EU 31-45",
          producturl:
            "https://www.kito.co.th/product/move-twotone-ah81/",
          rightUrl: "https://www.kito.co.th/product-category/women/women-sandals/",
          ctaText: "Shop Now",
          active:false,
          price:199,
        },

        {
          name: "KITO Move TwoTone AH81 (black&white)",
          imageurl:
            "https://www.kito.co.th/wp-content/uploads/2020/09/Kito-Move-TWOTONE-E-1024x1024.jpg",
          rightText: "price : 199",
          leftText: "Size : EU 31-45",
          producturl:
            "https://www.kito.co.th/product/move-twotone-ah81/",
          rightUrl: "https://www.kito.co.th/product-category/women/women-sandals/",
          ctaText: "Shop Now",
          active:false,
          price:199,
        },

        {
          name: "KITO Move TwoTone AH81 (yellow&black)",
          imageurl:
            "https://www.kito.co.th/wp-content/uploads/2020/09/Kito-Move-TWOTONE-D-1024x1024.jpg",
          rightText: "price : 199",
          leftText: "Size : EU 31-45",
          producturl:
            "https://www.kito.co.th/product/move-twotone-ah81/",
          rightUrl: "https://www.kito.co.th/product-category/women/women-sandals/",
          ctaText: "Shop Now",
          active:false,
          price:199,
        },

        {
          name: "KITO Move TwoTone AH81 (white&red)",
          imageurl:
            "https://www.kito.co.th/wp-content/uploads/2020/09/Kito-Move-TWOTONE-A-scaled.jpg",
          rightText: "price : 199",
          leftText: "Size : EU 31-45",
          producturl:
            "https://www.kito.co.th/product/move-twotone-ah81/",
          rightUrl: "https://www.kito.co.th/product-category/women/women-sandals/",
          ctaText: "Shop Now",
          active:false,
          price:199,
        },

        {
          name: "KITO Move TwoTone AH81 (green&yellow)",
          imageurl:
            "https://www.kito.co.th/wp-content/uploads/2020/09/Kito-Move-TwoTone-AH81-Green-1000x1000.jpg",
          rightText: "price : 199",
          leftText: "Size : EU 31-45",
          producturl:
            "https://www.kito.co.th/product/move-twotone-ah81/",
          rightUrl: "https://www.kito.co.th/product-category/women/women-sandals/",
          ctaText: "Shop Now",
          active:false,
          price:199,
        },

        {
          name: "KITO Move TwoTone AH81 (red&white)",
          imageurl:
            "https://www.kito.co.th/wp-content/uploads/2020/09/Kito-Move-TWOTONE-B-1024x1024.jpg",
          rightText: "price : 199",
          leftText: "Size : EU 31-45",
          producturl:
            "https://www.kito.co.th/product/move-twotone-ah81/",
          rightUrl: "https://www.kito.co.th/product-category/women/women-sandals/",
          ctaText: "Shop Now",
          active:false,
          price:199,
        },

        {
          name: "KITO Move TwoTone AH81 (blue&white)",
          imageurl:
            "https://www.kito.co.th/wp-content/uploads/2020/09/Kito-Move-TwoTone-AH81-Blue-1024x1024.jpg",
          rightText: "price : 199",
          leftText: "Size : EU 31-45",
          producturl:
            "https://www.kito.co.th/product/move-twotone-ah81/",
          rightUrl: "https://www.kito.co.th/product-category/women/women-sandals/",
          ctaText: "Shop Now",
          active:false,
          price:199,
        },

        {
          name: "KITO Move TwoTone AH81 (blue&red)",
          imageurl:
            "https://www.kito.co.th/wp-content/uploads/2020/09/Kito-Move-TWOTONE-C-1024x1024.jpg",
          rightText: "price : 199",
          leftText: "Size : EU 31-45",
          producturl:
            "https://www.kito.co.th/product/move-twotone-ah81/",
          rightUrl: "https://www.kito.co.th/product-category/women/women-sandals/",
          ctaText: "Shop Now",
          active:false,
          price:199,
        },

        {
          name: "KITO Move TwoTone AH81 (brown&white)",
          imageurl:
            "https://www.kito.co.th/wp-content/uploads/2020/09/Kito-Move-TwoTone-AH81-Cocoa-1024x1024.jpg",
          rightText: "price : 199",
          leftText: "Size : EU 31-45",
          producturl:
            "https://www.kito.co.th/product/move-twotone-ah81/",
          rightUrl: "https://www.kito.co.th/product-category/women/women-sandals/",
          ctaText: "Shop Now",
          active:false,
          price:199,
        },

        {
          name: "KITO Move TwoTone AH81 (orange&black)",
          imageurl:
            "https://www.kito.co.th/wp-content/uploads/2020/09/Kito-Move-TwoTone-Orange.jpeg",
          rightText: "price : 199",
          leftText: "Size : EU 31-45",
          producturl:
            "https://www.kito.co.th/product/move-twotone-ah81/",
          rightUrl: "https://www.kito.co.th/product-category/women/women-sandals/",
          ctaText: "Shop Now",
          active:false,
          price:199,
        },
      ],
    };
  },
  methods:{
    selected:function(i){
        i.active = !i.active
    },
    total:function(){
        var sum=0;
        this.productlist.forEach(function(i){
              if(i.active){
                  sum+=i.price; 
              }
        });
        return sum;
    }
  }
};
</script>

<style>
h2{
  color: white;
}
</style>
