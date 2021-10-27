<template>
  <v-hover v-slot="{ hover }">
    <v-card style="width: 20vw; height:40vh">
      <v-img
        height="40vh"
        id="transition"
        :class="{ 'img-hover': hover }"
        :src="API + image"
      >
        <v-container
          fill-height
          class="p-5 text-center justify-center align-center hidden_div"
          :class="{ show_div: hover }"
          style="color: white"
        >
          <div>
            <h1>{{ title }}</h1>
            <p>{{ description }}</p>
          </div>
        </v-container>
      </v-img>
    </v-card>
  </v-hover>
</template>

<script>
export default {
  name: "Card",
  props: {
    API: String,
    title: String,
    image: String,
    description: String,
  },
  data() {
    return {
      hover: false,
    };
  },
};
</script>

<style>
#transition .v-image__image,
#transition .container {
  -webkit-transition: all 0.4s linear;
  -moz-transition: all 0.4s linear;
  -o-transition: all 0.4s linear;
  transition: all 0.4s linear;
}

.img-hover .v-image__image {
  filter: brightness(20%);
}

.hidden_div {
  opacity: 0 !important;
}
.show_div {
  opacity: 100 !important;
}
</style>