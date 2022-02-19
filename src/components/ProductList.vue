<template>
  <v-container class="container1">
    <v-card class="parent" flat color="transparent">
      <v-subheader class="Contain" v-for="(product, index) in Bill" :key="index"
        >{{ product.name }}
        <div>Quantity x {{ product.quantity }}</div>
        <div>Price : {{ product.price }} $</div>
        <div>Sum : {{ product.sum }} $</div>
        <v-btn color="#D40B0B" class="del" @click="Del(index)"
          >Delete</v-btn
        ></v-subheader
      >
      <div>
        All : {{ check }} $.<v-btn class="btn1" @click="buy" color="#FA460D"
          >BUY</v-btn
        >
      </div>
      <div class="buy">
        <strong
          >{{ this.details[id - 1].name }} ---- Quantity :
          {{ quantity }}</strong
        >
      </div>
      <v-card-text>
        <v-row>
          <v-col class="pr-4">
            <v-slider
              v-model="quantity"
              class="align-center"
              :max="max"
              :min="min"
              hide-details
            >
              <template v-slot:append>
                <v-text-field
                  v-model="quantity"
                  class="mt-0 pt-0"
                  hide-details
                  single-line
                  type="number"
                  style="width: 60%"
                ></v-text-field>
              </template>
            </v-slider>
          </v-col>
        </v-row>
      </v-card-text>
    </v-card>
    <v-btn rounded class="Btn" color="primary" @click="Add()" dark>Add</v-btn>
    <hr />
  </v-container>
</template>

<script>
export default {
  props: {
    details: Array,
  },
  data() {
    return {
      id: this.$route.params.id,
      min: 1,
      max: 10,
      quantity: 1,
      price: 0,
      sum: 0,
      Bill: [],
      i: 0,
      j: 0,
      check: 0,
    };
  },
  methods: {
    Add() {
      this.id = this.$route.params.id;
      for (this.i in this.details) {
        if (this.id == this.details[this.i].id) {
          this.sum = this.quantity * this.details[this.i].price;
          this.Bill.push({
            name: this.details[this.i].name,
            price: this.details[this.i].price,
            quantity: this.quantity,
            sum: this.sum,
          });
        }
      }
      this.check += this.sum;
      this.sum = 0;
      this.quantity = 1;
    },
    Del(m) {
      this.Bill.splice(m, 1);
    },
    buy() {
      this.Bill = [];
      this.check = 0;
    },
  },
};
</script>

<style>
.btn {
  border: 1px solid black;
}
.Btn {
  margin-bottom: 5px;
}
.Contain {
  display: flex;
  justify-content: space-between;
}
.parent {
  text-align: center;
}
.buy {
  text-align: left;
}
.container1 {
  border: 2px solid black;
}
.btn1 {
  margin-left: 20px;
}
</style>
