<template>
    <div class="movie text-center">
        <ul>
            <li>
                <div class="cardMovie">
                    <div class="image_first prima">
                        <div class="box_uno">
                            <img 
                            class="img-fluid mb-3"
                            v-if="film.poster_path!=null"
                            :src="'https://image.tmdb.org/t/p/w342' 
                            + film.poster_path"
                            :alt="film.name"
                            >
                            <img 
                                v-else src="../assets/placeholder.png"
                            >
                        </div>
                    </div>
                    <div class="image_second prima">
                        <div class="box_due">
                            <h2> Title: {{ film.title }} </h2>
                            <h3> Original title: {{ film.original_title }} </h3>
                            <h4> language: {{ film.original_language }} </h4>
                            <h5> vote: {{ film.vote_average }}
                                <img 
                                class=" flag img-fluid mb-3"
                                :src="'https://www.countryflags.io/gb/flat/64.png'"
                                :alt="film.name"
                            >
                            </h5>
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
  props: ['film']
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
            //display: flex;
            position: relative;

            li {
                position: relative;
                display: flex;

                .cardMovie {
                    background-color: #49515f;
                    width: 100%;
                    height: 200px;
                    position: relative;
                    padding: 10px 10px;
                    display:inline-block;

                    .image_first {
                        display: inline-block;
                        cursor: pointer;

                        &:hover,
                        &:active {
                            display: none;
                        }
                    }

                    .image_second {
                        display: inline-block;
                        cursor: pointer;

                        &:hover,
                        &:active {
                            display: inline-block;
                        }
                    }

                    img {
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