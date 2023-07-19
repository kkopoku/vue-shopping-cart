<template>
    <div class="flex flex-col min-h-screen bg-gray-900 px-20">
        <div class="container mx-auto pt-10">
            <h1 class="text-3xl font-bold text-white mb-12">Product List</h1>
            <div class="max-h-[35rem] overflow-y-auto custom-scrollbar">
                <div v-for="product in sortedProducts" :key="product.name"
                    class="flex items-center justify-between p-4 rounded-md">
                    <div>
                        <h2 class="text-lg font-semibold text-white">{{ product.name }}</h2>
                        <p class="text-sm text-gray-300">{{ product.description }}</p>
                    </div>
                    <button class="bg-blue-500 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded"
                        @click="openPopup(product)">View
                    </button>
                </div>
            </div>
        </div>
        <div v-if="showHistory" class="fixed inset-0 flex items-center justify-center bg-gray-800 bg-opacity-75">
            <div class="bg-gray-900 bg-opacity-60 p-6 w-96 rounded-md h-fit transition">
                <h2 class="text-lg font-semibold mb-5 text-white">Product History</h2>

                <div class="flex flex-col">

                    <div v-if="!editing" class="flex mt-2">
                        <p class="text-gray-300">Product: {{ selectedProduct.name }}</p>
                    </div>
                    <div v-else class="flex flex-col mt-5">
                        <label class="text-gray-300 text-xs mb-1">Product:</label>
                        <input type="text" class="bg-gray-800 text-white rounded-md p-2" v-model="selectedProduct.name">
                    </div>

                    <div v-if="!editing" class="flex mt-2">
                        <p class="text-gray-300">Description: {{ selectedProduct.description }}</p>
                    </div>
                    <div v-else class="flex flex-col mt-5">
                        <label class="text-gray-300 text-xs mb-1">Description:</label>
                        <input type="text" class="bg-gray-800 text-white rounded-md p-2"
                            v-model="selectedProduct.description">
                    </div>
                </div>

                <div class="flex flex-col mt-2 gap-2">
                    <div v-if="!editing" class="basis-1/2">
                        <p class="text-gray-300">Current quantity: {{ selectedProduct.quantity }}</p>
                    </div>
                    <div v-else class="flex flex-col mt-5">
                        <label class="text-gray-300 text-xs mb-1">New quantity:</label>
                        <input type="number" class="bg-gray-800 text-white rounded-md p-2"
                            v-model="selectedProduct.quantity">
                    </div>

                    <div v-if="!editing" class="basis-1/2">
                        <p class="text-gray-300">Current Price: {{ selectedProduct.CP }}</p>
                    </div>
                    <div v-else class="flex flex-col mt-5">
                        <label class="text-gray-300 text-xs mb-1">New Price:</label>
                        <input type="text" class="bg-gray-800 text-white rounded-md p-2" v-model="selectedProduct.CP">
                    </div>
                </div>

                <div class="flex flex-row gap-3 justify-end mt-5">
                    <div v-if="editing">
                        <button class="bg-green-500 hover:bg-green-700 text-white font-semibold py-2 px-4 rounded mt-4"
                            @click="() => {
                                editing = false;
                            }">Submit
                        </button>
                    </div>
                    <div v-else>
                        <button class="bg-green-500 hover:bg-green-700 text-white font-semibold py-2 px-4 rounded mt-4"
                            @click="() => {
                                editing = true;
                            }">Edit
                        </button>
                    </div>
                    <button class="bg-blue-500 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded mt-4" @click="() => {
                        editing = false;
                        showHistory = false
                    }">Close
                    </button>
                </div>

            </div>
        </div>
    </div>
</template>
  
  
  
<script>
export default {
    data() {
        return {
            products: [
                { name: 'Samsung 50" TV', description: 'Samsung 50" TV description', quantity: 10, CP: '100 USD', SP: '120USD' },
                { name: 'iPhone XR', description: 'iPhone XR Description', quantity: 5, CP: '100 USD', SP: '120USD' },
                { name: 'iPhone 11', description: 'Product 3 description', quantity: 8, CP: '100 USD', SP: '120USD' },
                { name: 'iPhone 14', description: 'Product 1 description', quantity: 13, CP: '100 USD', SP: '120USD' },
                { name: 'iPhone XR', description: 'Product 2 description', quantity: 51, CP: '100 USD', SP: '120USD' },
                { name: 'iPhone 12 Pro Max', description: 'Product 3 description', quantity: 833, CP: '100 USD', SP: '120USD' },
                { name: 'MacBook Pro 2018', description: 'Product 1 description', quantity: 0, CP: '100 USD', SP: '120USD' },
                { name: 'HP Desktop 24"', description: 'Product 2 description', quantity: 25, CP: '100 USD', SP: '120USD' },
                { name: 'Samsung Home Theatre Speaker', description: 'Product 3 description', quantity: 84, CP: '100 USD', SP: '120USD' },
                { name: 'Nasco Headphones', description: 'Product 1 description', quantity: 31, CP: '100 USD', SP: '120USD' },
                { name: 'Airpods Max', description: 'Product 2 description', quantity: 51, CP: '100 USD', SP: '120USD' },
                { name: '1 TB HDD', description: 'Product 3 description', quantity: 87, CP: '100 USD', SP: '120USD' },
            ],
            selectedProduct: {},
            showHistory: false,
            editing: false,
        };
    },
    methods: {
        openPopup(product) {
            this.selectedProduct = product;
            this.showHistory = true;
        },
    },
    computed: {
        sortedProducts() {
            return this.products.sort((a, b) => {
                return a.name.localeCompare(b.name);
            });
        },
    }
};

document.title = 'Product-Details'

</script>

<style>
/* Custom Scrollbar Styling */
.custom-scrollbar::-webkit-scrollbar {
    width: 8px;
    /* Adjust the width as needed */
}

.custom-scrollbar::-webkit-scrollbar-track {
    background-color: transparent;
    /* Adjust the track color */
}

.custom-scrollbar::-webkit-scrollbar-thumb {
    background-color: #888;
    /* Adjust the thumb color */
    border-radius: 4px;
}
</style>