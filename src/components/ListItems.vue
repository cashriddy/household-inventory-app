<template>
    <!-- Item inventory -->
    <div class="items">
        <div class="item" v-for="(item, index) in items" :key="index">
            <div class="not-editing" v-if="!item.editing">
                <h3 class="item__heading"><i v-bind:class="item.icon"></i> {{ item.name }}</h3>
                <div v-if="item.qty === 0">
                    <span class="item__qty item__qty-none">{{ item.qty }}</span>
                    <p>Out of {{ item.name }}!</p>
                </div>
                <div v-else-if="item.qty === 1">
                    <span class="item__qty item__qty-low">{{ item.qty }}</span>
                    <p>Low on {{ item.name }}!</p>
                </div>
                <div v-else>
                    <span class="item__qty item__qty-good">{{ item.qty }}</span>
                </div>
                <!-- <div>Expiration Date - {{ item.expirationDate }}</div> -->
                <div class="action_buttons">
                    <button class="item__edit" v-on:click="enableEditing(index)">Edit</button>
                    <button class="item__remove" v-on:click="removeItem(index)">Remove</button>
                </div>
            </div>

            <div class="editing" v-if="item.editing">
                <h3 class="item__heading">{{ item.name }}</h3>
                <input type="text" v-model="item.name" placeholder="Name" class="item__name-edit">
                <input type="text" v-model="item.qty" placeholder="Quantity" class="item__qty-edit">
                <div class="action_buttons">
                    <button @click="disableEditing(index)"> Cancel </button>
                    <button @click="saveEdit(index)"> Save </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'ListItems',
  data: () => ({
            items: [
                { id: 1, name: 'Eggs', qty: 12, expirationDate: '10-23-20', editing: false, icon: 'fas fa-egg' },
                { id: 2, name: 'Bacon', qty: 12, expirationDate: '10-27-19', editing: false, icon: 'fas fa-bacon' }, 
                { id: 3, name: 'Bread', qty: 0, expirationDate: '11-23-20', editing: false, icon: 'fas fa-bread-slice' },
                { id: 4, name: 'Dog Treats', qty: 50, expirationDate: '1-17-20', editing: false, icon: 'fas fa-bone' },
                { id: 5, name: 'Apples', qty: 3, expirationDate: '7-13-19', editing: false, icon: 'fas fa-apple-alt'},
                { id: 6, name: 'Toilet Paper', qty: 1, expirationDate: '7-13-19', editing: false, icon: 'fas fa-toilet'},
                { id: 7, name: 'Frozen Pizza', qty: 3, expirationDate: '7-13-19', editing: false, icon: 'fas fa-pizza-slice'},
            ],
            tempValue: null
    }),
    methods: {
        addItem: function(name, qty, expirationDate) {
            this.items.push({
                name: name,
                qty: qty,
                expirationDate: expirationDate
            })
        },
        removeItem: function(index) {
            this.items.splice(index, 1)
        },
        enableEditing: function(index) {
            this.items[index].editing = true;
            console.log(this.items[index]);
        },
        disableEditing: function(index) {
            this.items[index].editing = false;
        },
        saveEdit: function(index, name, qty) {
            // However we want to save it to the database
            //alert(this.items[index].name);
            //alert(this.items[index].qty);
            this.items.splice(index, 1, {
                name: this.items[index].name,
                qty: this.items[index].qty
            })
            this.disableEditing();
          }
    },
    computed: {
        
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.items {
    display: flex;
    flex-wrap: wrap;
}
.item {
    background: #ffffff;
    margin: 15px;
    width: 220px;
    height: auto;
    text-align: center;
    box-shadow: 0px 5px 15px 0px rgba(50, 50, 50, 0.9);
    display: flex;
    flex-direction: column;
}
.item__heading {
    font-size: 18px;
    margin-top: 0;
    width: 100%;
    background: #AA471F;
    color: white;
    padding: 15px 0;
}
.item__qty {
    font-size: 36px;
}
.item__qty-low {
    background: #F2E880;
    padding: 8px;
    border-radius: 3px;
}
.item__qty-none {
    background: #ff2d08;
    padding: 8px;
    border-radius: 3px;
}
.item__name-edit {
    width: 170px;
    height: 22px;
    font-size: 18px;
    margin-bottom: 15px;
    text-align: center;
}
.item__qty-edit {
    width: 63px;
    height: 36px;
    font-size: 36px;
    text-align: center;
}
</style>
