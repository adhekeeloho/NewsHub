<template>
    <div class="home" >
        <div data-aos="fade-up-left"
    data-aos-offset="500"
     data-aos-easing="ease-in-sine">
            <v-carousel>
                <v-carousel-item v-for="(item,i) in items" :key="i" :src="item.src" reverse-transition="fade-transition" transition="fade-transition" style="height:auto; width: auto; "> </v-carousel-item>
            </v-carousel>
        </div>
        <div data-aos="fade-up"
    data-aos-offset="500"
     data-aos-easing="ease-in-sine" >
            <h1 class="do ma-5" align="center" justify="center"> <span class="an" style="font-family: 'Poppins', sans-serif;"><b>Daily News Ukraine</b></span></h1>
            <v-container fluid>
                <v-row dense>
                    <v-col v-for="result in news" :key="result" cols="12" sm="4" >
                        <v-card :elevation="hover ? 16 : 8" class="ma-2 rounded-l" color="yellow lighten-5" >
                            <v-col md="12">
                                <span v-if="result.images[0]"> 
                    <img
                      class="white--text align-end rounded"
                      gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
                      height="200px"
                      style="width: 100%; image: contain; border: none"
                      :src="result.images[0]"
                    /></span>
                                <span v-else> 
                    <v-img height="200px" contain
                      style="width: 100%; image: contain; border: none" src="../assets/news-on-go.jpg" >
                    </v-img> 
                    </span>
                            </v-col>
                            <v-col md="12" style="border: none; height: 400px" class="overflow-auto">
                                <h4 style="font-family: 'Poppins', sans-serif; color: #005BBB">
                                    {{ result.title }}
                                </h4>
                                <br />
                                <v-spacer></v-spacer>
                                <h6 style="font-family: 'Poppins', sans-serif" class="text-justify">
                                    {{ result.body[0] }}
                                </h6>
                                <br />
                                <h6 style="font-family: 'Poppins', sans-serif" class="text-justify">
                                    {{ result.body[1] }}
                                </h6>
                                <br />
                                <h6 style="font-family: 'Poppins', sans-serif" class="text-justify">
                                    {{ result.body[2] }}
                                </h6>
                                <br />
                                <h6 style="font-family: 'Poppins', sans-serif" class="text-justify">
                                    {{ result.body[3] }}
                                </h6>
                                <br />
                                <h6 style="font-family: 'Poppins', sans-serif" class="text-justify">
                                    {{ result.body[4] }}
                                </h6>
                                <br />
                                <h6 style="font-family: 'Poppins', sans-serif" class="text-justify">
                                    {{ result.body[5] }}
                                </h6>
                                <br />
                                <h6 style="font-family: 'Poppins', sans-serif" class="text-justify">
                                    {{ result.body[6] }}
                                </h6>
                                <br />
                                <h6 style="font-family: 'Poppins', sans-serif" class="text-justify">
                                    {{ result.body[7] }}
                                </h6>
                                <br />
                                <h6 style="font-family: 'Poppins', sans-serif" class="text-justify">
                                    {{ result.body[8] }}
                                </h6>
                                <br />
                                <h6 style="font-family: 'Poppins', sans-serif" class="text-justify">
                                    {{ result.body[9] }}
                                </h6>
                                <br />
                                <h6 style="font-family: 'Poppins', sans-serif" class="text-justify">
                                    {{ result.body[10] }}
                                </h6>
                                <br />
                                <v-spacer></v-spacer>
                                <h5 style="font-family: 'Poppins', sans-serif; color: #005BBB">
                                    {{ result.time }}
                                </h5>
                            </v-col>
                        </v-card>
                    </v-col>
                </v-row>
            </v-container>
        </div>
        <div class="pt-4 go" data-aos="fade-left" >
            <div align="center" justify="center" style="
              bottom: 0px;
             display: block;
             margin-left: auto;
             margin-right: auto; 
            " class="earth"></div>
            <div>
                <v-img style="display: block;
             margin-left: auto;
             margin-right: auto; " height="15%" width="15%" src="../assets/state-2727717_1920.png"></v-img>
            </div>
            <div class="mt-2" align="center" justify="center">
                <p class=" pb-5" style="font-family: 'Poppins', sans-serif">
                    News Hub
                    <v-icon>mdi-copyright</v-icon>
                    {{ new Date().getFullYear() }}
                    <br>
                    <span>Dedicated to the people of Ukraine</span>
                </p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data: () => ({
        name: "Home",
        news: [],
        show: false,
        items: [{
                src: require('../assets/flag-7036018_1920.jpg'),
            },
            {
                src: require('../assets/man-7036718_1920.jpg'),
            },
            {
                src: require('../assets/ukraine-7045136_1920.png'),
            },
        ],
    }),

    mounted() {
        this.getData();
    },
    methods: {
        getData() {
            fetch("https://russian-ukraine-news-feed.p.rapidapi.com/news", {
                    method: "GET",
                    headers: {
                        "X-RapidAPI-Host": "russian-ukraine-news-feed.p.rapidapi.com",
                        "X-RapidAPI-Key": "02b966095emshcbc7a3af74f3467p13c02djsn00b51e597cb1",
                    },
                })
                .then((response) => response.json())
                .then((response) => {
                    this.news = response;
                })
                .catch((err) => console.error(err));
        },
    },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins&display=swap");
.do {
    color: #005BBB;
}

.earth {
    width: 70px;
    height: 70px;
    background: url(../assets/704-7046315_global-background-check-services-world-map-hd-png.png);
    border-radius: 50%;
    background-size: 100px;
    box-shadow: inset 4px 12px 30px 3px, inset -6px 0 12px 4px;
    animation-name: rotate;
    animation-duration: 12s;
    animation-iteration-count: infinite;
    transform-style: preserve-3d;
    animation-timing-function: linear;
    -webkit-animation-name: rotate;
    -webkit-animation-duration: 12s;
    -webkit-animation-iteration-count: infinite;
    -webkit-animation-timing-function: linear;
}

@keyframes rotate {
    from {
        background-position: 0px 0px;
    }
    to {
        background-position: 200px 0px;
    }
}

@-webkit-keyframes rotate {
    from {
        background-position: 0px 0px;
    }
    to {
        background-position: 200px 0px;
    }
}

.an {
    padding: 0 2px;
    box-shadow: inset 0 -15px 0 0 #FFD500;
}

.go {
    background-image: url("../assets/heart-7051287_1920.jpg");
    background-size: contain;
}
</style>
