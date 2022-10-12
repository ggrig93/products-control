<template>
  <div id="app">
    <div class="selected-row">
      <div class="selected-wrapper">
        <div class="selected">
          <div
              v-for="(item, i) in leftSelected"
              :key="item.id"
              class="product-item"
              @click="unSelect(i)"
          >{{item.name}}</div>
        </div>
        <div class="limit">selected: {{leftSelected.length}} / {{limit}}</div>
      </div>
      <div v-if="rightSelected.name" class="selected-product">{{rightSelected.name}}</div>
    </div>
    <div class="products-wrapper">
      <div class="products">
        <button
            v-for="item in leftData"
            :key="item.id"
            class="product-item"
            :class="{'product-item_active': isActive(item)}"
            @click="leftSelect(item)"
        >{{item.name}}</button>
      </div>

      <div class="products">
        <button
            v-for="item in rightData"
            :key="item.id"
            class="product-item"
            @click="rightSelect(item)"
        >{{item.name}}</button>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data: () => ({
    limit: 6,
    leftSelected: [],
    rightSelected: {},
    leftData: [
      {
        id: 1,
        name: "Shoes 1"
      },
      {
        id: 2,
        name: "Shoes 2"
      },
      {
        id: 3,
        name: "Shoes 3"
      },
      {
        id: 4,
        name: "Shoes 4"
      },
      {
        id: 5,
        name: "T-shirt 1"
      },
      {
        id: 6,
        name: "T-shirt 2"
      },
      {
        id: 7,
        name: "T-shirt 3"
      },
      {
        id: 8,
        name: "T-shirt 4"
      }
    ],
    rightData: [
      {
        id: 11,
        name: "Jacket 1"
      },
      {
        id: 12,
        name: "Jacket 2"
      },
      {
        id: 13,
        name: "Jacket 3"
      },
      {
        id: 14,
        name: "Jacket 4"
      },
      {
        id: 15,
        name: "Hoodie 1"
      },
      {
        id: 16,
        name: "Hoodie 2"
      },
      {
        id: 17,
        name: "Hoodie 3"
      },
      {
        id: 18,
        name: "Hoodie 4"
      }
    ]
  }),
  methods: {
    leftSelect(item) {
      if(this.leftSelected.find(el => el.id === item.id)) {
        this.leftSelected = this.leftSelected.filter(el => el.id !== item.id)
      } else if (this.leftSelected.length !== this.limit){
        this.leftSelected.push(item)
      }
    },
    rightSelect(item) {
      this.rightSelected = item
    },
    unSelect(i) {
      this.leftSelected.splice(i,1)
    },
    isActive(item) {
      return this.leftSelected.find(el => el.id === item.id)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
.products-wrapper {
  display: flex;
}
.products {
  border: 1px solid black;
  display: flex;
  flex-wrap: wrap;
  margin-right: 20px;
}
.product-item {
  text-align: center;
  margin: 5px;
  width: 70px;
  height: 50px;
  border: 1px solid black;
  cursor: pointer;
}
.product-item_active {
  border: 1px solid green;
}
.selected-row {
  display: flex;
  justify-content: space-between;
  margin-bottom: 40px;
}
.selected-product {
  margin-right: 20px;
  text-align: center;
  width: 100px;
  height: 70px;
  border: 1px solid black;
}
.selected-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  border: 1px solid black;
  margin-right: 20px;
}
.selected {
  display: flex;
}
.limit {
  margin-top: 20px;
}
</style>
