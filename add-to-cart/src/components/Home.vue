<template>
<div class="wrapper">
    <MainHeader />
    <div class="content">
        <div class="container mb-5">
            <!-- Top Rated -->
            <h4 class="my-4 fw-600 d-blue">Top Rated</h4>
            <div class="row">
                <div @click="foodDetails(items)" v-for="items in topRated" :key="items.id" class="col-md-4 pointer">
                    <img :src="items.url" width="300px" height="300px" style="border-radius:15px;" alt="images">
                    <h5 class="fw-600 black">{{items.name}}</h5>
                </div>
            </div>

            <!-- All Categories -->
            <h4 class="my-4 fw-600 d-blue">All Categories</h4>
            <div class="row">
                <div @click="foodDetails(items)" v-for="items in allCategories" :key="items.id" class="col-md-4 pointer">
                    <img :src="items.url" width="300px" height="300px" style="border-radius:15px;" alt="images">
                    <h5 class="fw-600 black">{{items.name}}</h5>
                </div>
            </div>

            <!-- Dishes Near You -->
            <h4 class="my-4 fw-600 d-blue">Dishes Near You</h4>
            <div class="row">
                <div @click="foodDetails(items)" v-for="items in dishesNearYou" :key="items.id" class="col-md-4 pointer">
                    <img :src="items.url" width="300px" height="300px" style="border-radius:15px;" alt="images">
                    <h5 class="fw-600 black">{{items.name}}</h5>
                </div>

            </div>

        </div>
    </div>
    <Footer />
</div>
</template>

<script>
import MainHeader from "./common/MainHeader.vue";
import Footer from "./common/Footer.vue";
export default {
    name: "Home",
    components: {
        Footer,
        MainHeader,
    },
    computed: {
        topRated() {
            return this.$store.state.topRated;
        },
        allCategories() {
            return this.$store.state.allCategories;
        },
        dishesNearYou() {
            return this.$store.state.dishesNearYou;
        },
    },
     methods: {
          foodDetails(items){
            this.$router.push({ name : 'food-details', params: items })
          }
        },
};
</script>

<style scoped>
.wrapper {
    display: flex;
    flex-direction: column;
    height: 100vh;
}

.content {
    background: #efe9e2;
    flex: 1;
    overflow-y: auto;
}

.fw-600 {
    font-weight: 600;
}

.d-blue {
    color: dodgerblue;
    ;
}

.black {
    color: black;
}

.pointer {
    cursor: pointer;
}
</style>
