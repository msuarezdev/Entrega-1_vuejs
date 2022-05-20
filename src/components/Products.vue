<template>
    <div>
        <b-container fluid class="bv-example-row mt-4">
            <b-row>
                <b-col cols="3" v-for="(food,index) in foods" :key="index">
                    <b-card
                    :title=food.name
                    :img-src="require(`@/assets/img/foods/food${index+1}.jpg`)"
                    img-alt="Image"
                    img-top
                    tag="article"
                    class="mb-4"
                    >
                    <b-card-text>
                        <h5>Precio: ${{food.price}}.00</h5>
                        <b-icon variant="warning" class="h1" icon="star-fill"></b-icon>
                        <b-icon variant="warning" class="h1" icon="star-fill"></b-icon>
                        <b-icon variant="warning" class="h1" icon="star-fill"></b-icon>
                        <b-icon variant="warning" class="h1" icon="star-fill"></b-icon>
                        <b-icon variant="warning" class="h1" icon="star-fill"></b-icon>
                    </b-card-text>

                    <b-button v-if="!food.cart" :disabled="food.cart" @click="food.cart=true,
                    addtocart(JSON.parse(JSON.stringify(food)))" block href="#" variant="info">
                    Agregar al carrito</b-button>
                    <b-button v-if="food.cart" :disabled="food.cart" block href="#" variant="success">
                    Su producto fue agregado
                    </b-button>                    
                    </b-card>
                </b-col>
            </b-row>
        </b-container>
    </div>
</template>

<script>
export default {
    data() {
        return{
            foods:[
                {
                    id:1,
                    quantity:1,
                    name:'Hamburguesa',
                    price:800,
                    img:'@/assets/foods/food1.jpg',
                    cart:false
                },
                {
                    id:2,
                    quantity:1,
                    name:'Pizza',
                    price:1200,
                    img:'@/assets/foods/food2.jpg',
                    cart:false
                },
                {
                    id:3,
                    quantity:1,
                    name:'Empanadas',
                    price:1500,
                    img:'@/assets/img/foods/food3.jpg',
                    cart:false
                },
                {
                    id:4,
                    quantity:1,
                    name:'Papas',
                    price:600,
                    img:'@/assets/foods/food4.jpg',
                    cart:false
                },
                {
                    id:5,
                    quantity:1,
                    name:'Sushi',
                    price:2000,
                    img:'@/assets/foods/food5.jpg',
                    cart:false
                },
                {
                    id:6,
                    quantity:1,
                    name:'Chow Mein',
                    price:1265,
                    img:'@/assets/foods/food6.jpg',
                    cart:false
                },
                {
                    id:7,
                    quantity:1,
                    name:'Gyozas',
                    price:1200,
                    img:'@/assets/foods/food7.jpg',
                    cart:false
                },
                {
                    id:8,
                    quantity:1,
                    name:'Tacos',
                    price:2240,
                    img:'@/assets/foods/food8.jpg',
                    cart:false
                },
            ]
        }
    },
    methods:{
        addtocart(product){
            let cart= []
            if (JSON.parse(localStorage.getItem('products'))){
                cart= JSON.parse(localStorage.getItem('products'))
            }else{
                cart = []
            }
            cart.push(product);
            localStorage.setItem('products',JSON.stringify(cart))
        }
    },
    created(){
        let cart = []
        if (JSON.parse(localStorage.getItem('products'))){
            cart= JSON.parse(localStorage.getItem('products'))
        }else{
            cart = []
        }
        for (let index = 0; index < cart.length; index++) {
            for (let index2 = 0; index2 < this.foods.length; index2++) {
                if (cart[index].id == this.foods[index2].id){
                    this.foods[index2].cart=true
                }
            }
        }
    }
}
</script>

<style>

</style>

