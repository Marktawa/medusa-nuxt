<template>
    <div>
      <nuxt-link :to="`/products/${item.id}`">
        <div
          class="group relative"
        >
          <div class="w-full min-h-auto bg-gray-200 aspect-w-1 aspect-h-1 rounded-md overflow-hidden group-hover:opacity-75 lg:h-80 lg:aspect-none">
            <div class="w-auto h-full object-center object-cover bg-gray-100">
              <img
                alt=""
                :src="item.thumbnail"
              >
            </div>
          </div>
          <div class="mt-4 flex justify-between">
            <h3 class="text-sm text-gray-700 font-normal">
              {{ item.title }}
            </h3>
            <p class="text-sm font-semibold text-gray-900">
              from {{ lowestPrice.amount/100 }} {{ lowestPrice.currency_code.toUpperCase() }}
            </p>
          </div>
        </div>
      </nuxt-link>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ProductCard',
    props: {
      item: {
        type: Object,
        default () {
          return {
            id: 1,
            title: 'Kitchen Table',
            thumbnail: 'https://picsum.photos/600/600',
            variants: [{ prices: [{ amount: 0 }] }]
          }
        }
      }
    },
    computed: {
      lowestPrice () {
        const lowestPrice = this.item.variants.reduce((acc, curr) => {
          return curr.prices.reduce((lowest, current) => {
            if (lowest.amount > current.amount) {
              return current
            }
            return lowest
          })
        }, { amount: 0 })
  
        return lowestPrice || { amount: 10, currency_code: 'usd' }
      }
    }
  }
  </script>