<template>
    <div class="flex flex-col min-h-screen bg-gray-900 px-20">
        <div class="container mx-auto p-4">
            <h1 class="text-3xl font-bold text-gray-900 dark:text-white mb-12">Product List</h1>
            <div class="max-h-[35rem] overflow-y-auto custom-scrollbar">
                <div v-for="product in sortedProducts" :key="product.name"
                    class="flex items-center justify-between p-4 rounded-md">
                    <div>
                        <h2 class="text-lg font-semibold text-gray-900 dark:text-white">{{ product.name }}</h2>
                        <p class="text-sm text-gray-700 dark:text-gray-300">{{ product.description }}</p>
                    </div>
                    <button class="bg-blue-500 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded"
                        @click="openPopup(product)">View</button>
                </div>
            </div>
        </div>
        <div v-if="showHistory" class="fixed inset-0 flex items-center justify-center bg-gray-800 bg-opacity-75">
            <div class="bg-gray-900 bg-opacity-60 p-6 w-96 h-96 rounded-md">
                <h2 class="text-lg font-semibold mb-2 text-white">Product History</h2>
                <div class="flex flex-row">
                    <div class="basis-1/2">
                        <p class="text-gray-300">Current quantity: {{ selectedProduct.quantity }}</p>
                    </div>
                    <div class="basis-1/2">
                        <p class="text-gray-300">Current Price: {{ selectedProduct.CP }}</p>
                    </div>
                </div>
                <button class="bg-blue-500 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded mt-4"
                    @click="showHistory = false">Close</button>
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
                const nameA = a.name.toLowerCase();
                const nameB = b.name.toLowerCase();

                if (nameA < nameB) {
                    return -1; // a should come before b
                }
                if (nameA > nameB) {
                    return 1; // a should come after b
                }
                return 0; // a and b are equal in terms of sorting
            });
        },
    }
};
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