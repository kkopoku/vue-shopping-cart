<template>
    <div class="min-vh-100 bg-dark px-5">
        <div class="py-5">
            <h1 class="text-white text-center mb-5">Product List</h1>
            <div class="max-h-35rem overflow-auto">
                <div v-for="product in sortedProducts" :key="product.name"
                    class="d-flex justify-content-between align-items-center p-4 rounded">
                    <div>
                        <h2 class="text-white">{{ product.name }}</h2>
                        <p class="text-white">{{ product.description }}</p>
                    </div>
                    <button class="btn btn-primary" @click="openPopup(product)">View</button>
                </div>
            </div>
        </div>
        <transition name="fade">
            <div v-if="showHistory" class="fixed-top d-flex justify-content-center align-items-center">
                <div class="bg-white p-4 rounded w-50">
                    <h2 class="text-white mb-4">Product History</h2>

                    <div class="mb-3">
                        <div v-if="!editing">
                            <p class="text-gray-300">Product: {{ selectedProduct.name }}</p>
                        </div>
                        <div v-else>
                            <label class="text-gray-300 text-sm mb-1">Product:</label>
                            <input type="text" class="form-control bg-dark text-white" v-model="selectedProduct.name">
                        </div>
                    </div>

                    <div class="mb-3">
                        <div v-if="!editing">
                            <p class="text-gray-300">Description: {{ selectedProduct.description }}</p>
                        </div>
                        <div v-else>
                            <label class="text-gray-300 text-sm mb-1">Description:</label>
                            <input type="text" class="form-control bg-dark text-white"
                                v-model="selectedProduct.description">
                        </div>
                    </div>

                    <div class="mb-3">
                        <div v-if="!editing">
                            <p class="text-gray-300">Current quantity: {{ selectedProduct.quantity }}</p>
                        </div>
                        <div v-else>
                            <label class="text-gray-300 text-sm mb-1">New quantity:</label>
                            <input type="number" class="form-control bg-dark text-white" v-model="selectedProduct.quantity">
                        </div>
                    </div>

                    <div class="mb-3">
                        <div v-if="!editing">
                            <p class="text-gray-300">Current Price: {{ selectedProduct.CP }}</p>
                        </div>
                        <div v-else>
                            <label class="text-gray-300 text-sm mb-1">New Price:</label>
                            <input type="text" class="form-control bg-dark text-white" v-model="selectedProduct.CP">
                        </div>
                    </div>

                    <div class="d-flex justify-content-end">
                        <div v-if="editing">
                            <button class="btn btn-success" @click="editing = false">Submit</button>
                        </div>
                        <div v-else>
                            <button class="btn btn-success" @click="editing = true">Edit</button>
                        </div>
                        <div>
                            &nbsp;
                            &nbsp;
                        </div>
                        <button class="btn btn-primary" @click="() => { editing = false; showHistory = false }">Close</button>
                    </div>

                </div>
            </div>
        </transition>
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
</script>
  
<style>
.overlay {
    background-color: rgba(0, 0, 0, 0.75);
    z-index: 999;
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.3s;
}

.fade-enter,
.fade-leave-to {
    opacity: 0;
}
</style>
  