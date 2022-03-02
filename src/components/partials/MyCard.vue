<template>
    <li class="flip-container">

        <div class="card">
            <!-- Parte frontale Card -->
            <div
            v-if="info.poster_path"
            class="front"
            :style="{
                        backgroundImage: `url(https://image.tmdb.org/t/p/w342${info.poster_path})`
                    }">
            </div>

            <div
            class="front"
            v-else
            :style="{
                        'background-image': 'url(' + require('../../assets/ciak.jpg') + ')'
                    }">
            </div>
            <!-- Fine parte frontale Card -->

            <!-- <img v-if="info.poster_path" :src="`https://image.tmdb.org/t/p/w342${info.poster_path}`"> -->
            <!-- <img class="ciak" v-else :src="require('../../assets/ciak.jpg')"> -->

            <!-- Parte posteriore Card -->
            <div class="back">

                <!-- Titolo -->
                <h2>{{info.original_title ? info.original_title : info.original_name}}</h2>
                <!-- <p>{{info.}}</p> -->
                <!-- Fine titolo -->

                <!-- Lingua originale -->
                <div> 
                    <h4>Lingua originale</h4>
                    <img class="flag" v-if="languages.includes(info.original_language)" :src="require('../../assets/flags/' + info.original_language + '.png')">
                    <span v-else>{{info.original_language}}</span>
                </div>
                <!-- Fine lingua originale -->

                <!-- Voto -->
                <div>
                    <p>Voto {{Math.ceil(info.vote_average / 2)}}</p>
                    <i v-for="i in 5" :key="i" class="fa-star" :class="(i <= getStar) ? 'fa-solid' : 'fa-regular'"></i>
                </div>
                <!-- Fine voto -->

                <!-- Trama -->
                <div v-if="info.overview">
                    <h3>Trama</h3>
                    <p>{{info.overview}}</p>
                </div>
                <div v-else>
                    <p>Trama: not avaiable</p>
                </div>
                <!-- Fine trama -->

            </div>
            <!-- Fine parte posteriore Card -->
        </div>
    </li>
</template>

<script>
export default {
    name: 'MyCard',
    props: {
        'info': Object
    },
    data() {
        return {
            languages: ['de', 'en', 'es', 'fr', 'hi', 'it', 'ja', 'ko', 'sv', 'tr', 'zh'],
        }
    },
    computed: {
        getStar() {
            return Math.ceil(this.info.vote_average / 2);
        }
    },
}
</script>

<style lang="scss" scoped>
    .flag {
        vertical-align: middle;
        width: 1.5rem;
    }
    .ciak {
        width: 342px;
        height: 513px;
        object-position: center;
        object-fit: contain;
    }
    .flip-container {
        perspective: 1000;
        list-style: none;
    }

    .flip-container:hover .card {
        transform: rotateY(180deg);
    }

    .card, .front, .back {
        width: 342px;
        height: 513px;
    }
    
    .card {
        position: relative;
        text-align: center;
        list-style: none;
        color: white;
        transition: 0.5s;
        transform-style: preserve-3d;

        .front, .back {
            
            overflow:hidden;
            backface-visibility:hidden;
            position:absolute;
        }

        .front {
            background-repeat: no-repeat;
            background-size: cover;
            background-position: center;
        }

        .back {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            justify-content: space-around;
            background-color: black;
            transform: rotateY(180deg);
        }
    }
</style>