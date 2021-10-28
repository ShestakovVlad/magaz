<template>
    <div class="products">
        <ul>
            <li class="cart-item" v-for="(cartItem, index) in productsFromCart" v-bind:key="index">{{cartItem.item}}</li>
        </ul>
    </div>
</template>
<script>
    import products from '../data/products.js'

    export default {
        data: function () {
            return {
                items: [],
                search: '',
                searchResult: [],
                productsFromCart:[],
            };
        },
        mounted: function(){
            this.items = products;
            this.productsFromCart = this.$store.getters.getCart;
                        console.log(this.productsFromCart);
        },
        computed: {
            filteredItems: function() {
                console.log(this);
                if (!this.search) {
                    return this.items;
                }
                return this.items.filter(element => {
                    return element.item.toUpperCase().includes(this.search.toUpperCase());
                });
            },
        }
    }
</script>
