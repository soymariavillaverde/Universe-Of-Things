<template>
  <v-card class="mx-auto" min-width="163" max-width="243" elevation="15">
    <v-img
      :src="fixImageUrl()"
      lazy-src="https://yt3.ggpht.com/ytc/AKedOLTvdyXx_BMV1NliJxVqzs5kzn6XtGmYlEXb1_rmIA=s900-c-k-c0x00ffffff-no-rj"
      height="200"
      min-width="163"
      max-width="243"
      position="top"
    ></v-img>

    <v-card-title
      style="
        font-size: 1em;
        display: inline-block;
        overflow: hidden;
        text-overflow: ellipsis;
        max-width: 204px;
      "
      class="text-no-wrap"
    >
      {{ title }}
    </v-card-title>

    <v-card-actions>
      <v-btn @click="show = !show" color="orange lighten-2" text>
        More info
      </v-btn>

      <v-spacer></v-spacer>

      <v-btn icon @click="show = !show">
        <v-icon>{{ show ? "mdi-chevron-up" : "mdi-chevron-down" }}</v-icon>
      </v-btn>

      <v-btn icon @click="favourite = !favourite">
        <v-icon color="red">{{
          favourite ? "mdi-heart" : "mdi-heart-outline"
        }}</v-icon>
      </v-btn>
    </v-card-actions>
    <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>

        <v-card-text style="max-width: 14em" class="more-info-text">
          <v-card>
            <v-list-item v-if="checkArrayLenght(movies)">
              <v-list-item-content>
                <v-list-item-title>Movies:</v-list-item-title>
                <v-list-item-subtitle
                  v-for="movie of movies"
                  :key="movie"
                  style="font-size: 0.9em"
                  class="text-wrap"
                  >- {{ movie }}</v-list-item-subtitle
                >
              </v-list-item-content>
            </v-list-item>
            <v-list-item v-if="checkArrayLenght(shortFilms)">
              <v-list-item-content>
                <v-list-item-title>Short Films:</v-list-item-title>
                <v-list-item-subtitle
                  v-for="shortFilm of shortFilms"
                  :key="shortFilm"
                  style="font-size: 0.9em"
                  class="text-wrap"
                  >- {{ shortFilm }}</v-list-item-subtitle
                >
              </v-list-item-content>
            </v-list-item>
            <v-list-item v-if="checkArrayLenght(tvShows)">
              <v-list-item-content>
                <v-list-item-title>TV Shows:</v-list-item-title>
                <v-list-item-subtitle
                  v-for="tvShow of tvShows"
                  :key="tvShow"
                  style="font-size: 0.9em"
                  class="text-wrap"
                  >- {{ tvShow }}</v-list-item-subtitle
                >
              </v-list-item-content>
            </v-list-item>
            <v-list-item v-if="checkArrayLenght(videoGames)">
              <v-list-item-content>
                <v-list-item-title>Video Games:</v-list-item-title>
                <v-list-item-subtitle
                  v-for="videoGame of videoGames"
                  :key="videoGame"
                  style="font-size: 0.9em"
                  class="text-wrap"
                  >- {{ videoGame }}</v-list-item-subtitle
                >
              </v-list-item-content>
            </v-list-item>
            <v-list-item v-if="checkArrayLenght(parkAttractions)">
              <v-list-item-content>
                <v-list-item-title>Park Attractions:</v-list-item-title>
                <v-list-item-subtitle
                  v-for="parkAttraction of parkAttractions"
                  :key="parkAttraction"
                  style="font-size: 0.9em"
                  class="text-wrap"
                  >- {{ parkAttraction }}</v-list-item-subtitle
                >
              </v-list-item-content>
            </v-list-item>
          </v-card>
        </v-card-text>
      </div>
    </v-expand-transition>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    show: false,
    favourite: false,
  }),
  props: {
    title: {
      type: String,
      required: true,
    },
    imageUrl: {
      type: String,
      required: true,
    },
    movies: {
      type: Array,
    },
    shortFilms: {
      type: Array,
    },
    tvShows: {
      type: Array,
    },
    videoGames: {
      type: Array,
    },
    parkAttractions: {
      type: Array,
    },
  },
  computed: {
    getImageURL() {
      return this.imageUrl;
    },
  },
  methods: {
    fixImageUrl() {
      var indexPng = this.imageUrl.search("/revision");
      var stringFixed = this.imageUrl.slice(0, indexPng);
      return stringFixed;
    },
    checkArrayLenght(something) {
      if (something.length >= 1) {
        return true;
      } else {
        return false;
      }
    },
  },
};
</script>
