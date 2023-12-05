<template>
    <div>
        Выберете валюту:
        <select name="" id="" v-model="valuta">
            <option>₽</option>
            <option>$</option>
            <option>¥</option>
        </select>
        <br>
        <br>
        <div v-for="profuct in products" :key="profuct.id">
            <br>
            <p>Название: {{ profuct.name }}</p>
            <p>Цена: {{ formattedPrice(profuct.price) }}</p>
            <p v-if="profuct.available">Статус: Available</p>
            <p v-else>Статус: Out of stock</p>
        </div>

    </div>
</template>

<script>
export default {
    name: 'ProductDetails',

    data() {
        return {
            price: '',
            valuta: '',
            products: [
                {
                    id: 1,
                    name: 'Personal Computer',
                    price: 220000,
                    available: true,
                },
                {
                    id: 2,
                    name: 'PS 5',
                    price: 120000,
                    available: true,
                },
                {
                    id: 3,
                    name: 'X-BOX',
                    price: 100000,
                    available: false,
                },

            ]
        };
    },

    mounted() {

    },

    methods: {

    },
    computed: {
        formattedPrice() {
            if (this.valuta === '₽') {
                return price => `${price} рублей`
            } else if
                (this.valuta === '$') {
                return price => `$ ${(price / 94.35).toFixed(2)} на 05.12.2023`
            }
            else {
                return price => `¥ ${(price / 12.95).toFixed(2)} на 05.12.2023`
            }
        }
    }
}
    ;
</script>

<style lang="scss" scoped></style>