<template>
    <div>
        <b-carousel>
            <b-carousel-item v-for="(food, i) in foodImages" :key="i">
                <div class="image_food" :style="{backgroundImage: `url(${food.image})`}"></div>
            </b-carousel-item>
        </b-carousel>
        <b-field label="Image URL: ">
            <b-input v-model="imageURL"></b-input>
            <b-button @click="onButtonClick" type="is-primary">Add to Carousel</b-button>
        </b-field>
        <div class="url-list">
            <span v-for="(food, i) in foodImages" :key="i" class='image-item'>{{i}}: {{food.image}}
                <b-button size="is-small" @click="onDeleteClick(i)">Delete</b-button>
            </span>
        </div>
    </div>
</template>

<script>
export default {
    name: "Gallery",
    data() {
        return {
            foodImages: [
                
            ],
            imageURL: ""
        }
    },
    methods: {
        onButtonClick() {
            // Code, what to do on button click
            this.foodImages.push({image: this.imageURL});
            this.imageURL = "";
        },
        onDeleteClick(index) {
            this.foodImages.splice(index,1);
        }
    }
}
</script>

<style scoped>
.image_food {
    background-repeat: none;
    background-size: cover;
    background-position: center;
    width: 100vw;
    height: 50vh;
}

.image-item {
    display: block;
    font-size: 10px;
    font-weight: bold;
}

</style>