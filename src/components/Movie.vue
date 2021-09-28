<template>
    <div class="movie text-center">
        <ul>
            <li>
                <div class="cardMovie">
                    <div class="container-image">
                        <div class="box_uno">
                            <img 
                                class="img-fluid mb-3 copertina"
                                v-if="film.poster_path"
                                :src="`https://image.tmdb.org/t/p/w342${film.poster_path}`"
                                :alt="film.title ? film.title : film.name" 
                            >
                            <img 
                                v-else
                                src="../assets/flag/placeholder.png"
                                class="img-fluid mb-3 copertina"
                                :alt="`Copertina${film.title ? film.title : film.name}`"
                                
                            >
                        </div>
                        <div class="box_due">
                            <ul>
                                <li>
                                    <h2> Title: {{ film.title ? film.title : film.name}} </h2>
                                    <h3> Original title: {{ film.original_title }} </h3>
                                    <img 
                                        class="flag"
                                        v-if="availableFlags.includes(film.original_language)"
                                        :src="require(`../assets/flag/${film.original_language}.png`)" alt=""
                                    >
                                    <p v-else> {{ film.original_language }}</p>
                                    <!-- <h5> vote: {{ film.vote_average }}</h5> -->
                                    <div>
                                        <i v-for="n in 5" :key="n" class="fa-star" :class="(n <= getVote()) ? 'fas' : 'far'"></i>
                                    </div>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
  name: 'Movie',
    data: function() {
        return {
            availableFlags: ['it' , 'en', 'cn', 'es', 'pt', 'fr', 'ja', 'pl' ]
        }
    },
    methods: {
        getVote() {
            return Math.ceil(this.film.vote_average / 2)
        }
    },
props: ['film'],
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    .movie {
        width: 100%;
        height: 100%;
        position: relative;
        padding: 10px;
        //display: flex;
        //justify-content: center;
        //align-items: center;
        
        ul {
            display: flex;
            justify-content: space-around;
            position: relative;

            li {
                position: relative;
                //display: flex;

                .cardMovie {
                    //background-color: transparent;
                    width: 300px;
                    height: 300px;
                    perspective: 1000px;
                    background-color: #49515f;
                    
                    .container-image {
                        position: relative;
                        width: 100%;
                        height: 100%;
                        text-align: center;
                        transition: transform 0.6s;
                        transform-style: preserve-3d;
                        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
                    }

                    .container-image {
                        &:hover
                    {
                        transform: rotateY(180deg);
                    }
                    }
                    

                    .box_uno, .box_due {
                        position: absolute;
                        width: 100%;
                        height: 100%;
                        -webkit-backface-visibility: hidden;
                        backface-visibility: hidden;
                    }

                    .box_uno {
                        background-color: #49515f;
                    }

                    .box_due {
                        background-color: #49515f;
                        color: white;
                        transform: rotateY(180deg);
                        // display: flex;
                        // justify-content: center;
                        // align-items:center;

                        ul {
                           display: flex;
                            justify-items: center;
                            align-content: space-around;
                            padding: 50px;
                        }
                        
                    }
                    
                    .copertina {
                        width: 100%;
                        object-fit: contain;
                        vertical-align: middle;
                    }
                    
                    .flag {
                        width: 30px;
                        object-fit: contain;
                    }
                    
                    h2 {
                        color: white;
                        font-size: 10px;
                    }
                    h3 {
                        color: red;
                        font-size: 10px;
                    }
                    h4 {
                        color: lightblue;
                        font-size: 10px;
                    }
                    h5 {
                        color: white;
                        font-size: 10px;
                    }
                }
            }
        }
    }
</style>