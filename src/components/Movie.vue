<template>
    <div class="movie text-center">
        <ul>
            <li>
                <div class="cardMovie">
                    <!-- <img class="img-fluid mb-3" :src="film.poster_path" :alt="film.name"> -->
                    <h2> Title: {{ film.title }} </h2>
                    <h3> Original title: {{ film.original_title }} </h3>
                    <h4> language: {{ film.original_language }} </h4>
                    <h5> vote: {{ film.vote_average }} </h5>
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
                    width: 250px;
                    height: 250px;
                    position: relative;
                    //padding: 15px 10px;

                    img {
                        width: 100px;
                        object-fit: contain;
                        vertical-align: middle;
                    }
                    h2 {
                        color: white;
                        font-size: 15px;
                    }
                    h3 {
                        color: red;
                        font-size: 15px;
                    }
                    h4 {
                        color: lightblue;
                        font-size: 12px;
                    }
                    h5 {
                        color: white;
                        font-size: 12px;
                    }
                }
            }
        }
    }
</style>