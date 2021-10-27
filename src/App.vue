<template>
  <v-app>
    <v-app-bar app color="white">
      <v-container class="d-flex align-center" style="width:50vw;">
        <div>
          <h1 class="text-h4">Le meilleur blog</h1>
        </div>
        <v-spacer></v-spacer>
        <a
          v-for="icon in icons"
          :key="icon.name"
          :href="icon.url"
          class="text-decoration-none mx-2"
          ><v-icon color="rgba(0,0,0,0.9)" size="3rem"
            >mdi-{{ icon.name }}</v-icon
          ></a
        >
      </v-container>
    </v-app-bar>

    <v-main>
      <Home />
    </v-main>
  </v-app>
</template>

<script>
import Home from "./views/Home.vue";

export default {
  name: "App",

  components: {
    Home,
  },
  mounted() {},
  data() {
    return {
      icons: [
        {
          name: "facebook",
          url: "#",
        },
        {
          name: "linkedin",
          url: "#",
        },
        {
          name: "youtube",
          url: "#",
        },
        {
          name: "twitter",
          url: "#",
        },
      ],
    };
  },
};
</script>
