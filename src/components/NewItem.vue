<template>
    <!-- Add new item -->
    <div class="new-item">
      <h3 class="new-item__heading">Add a new item</h3>
      <label for="">Name</label>
      <input type="text" v-model="name">
      <label>Quantity</label>
      <input type="text" v-model="qty" class="new-item__qty">
      <!--<label>Expiration Date</label>
      <input type="date" v-model="expirationDate">-->
      <button v-on:click="addItem(name, qty)">Add item</button>
    </div>
</template>

<script>
export default {
  name: 'NewItem'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.new-item {
    background: #ffffff;
    margin: 15px;
    width: 400px;
    text-align: center;
    box-shadow: 0px 5px 15px 0px rgba(50, 50, 50, 0.9);
    display: flex;
    flex-direction: column;
    align-items: center;
}
.new-item__heading {
    font-size: 18px;
    margin-top: 0;
    width: 100%;
    background: #AA471F;
    color: white;
    padding: 15px 0;
}
.new-item input {
    width: 250px;
    height: 32px;
    line-height: 32px;
    font-size: 28px;
}
input.new-item__qty {
    width: 63px;
    text-align: center;
}
</style>
