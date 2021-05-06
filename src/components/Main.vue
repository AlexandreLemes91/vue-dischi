<template>
    <main>
        <div class="container">
            <AlbumCard
            v-for="(album,index) in albumsList"
            :key="index"
            :details="album"/>
        </div>
    </main>
</template>

<script>
import axios from 'axios';
import AlbumCard from '@/components/AlbumCard'

export default {
    name: "Main",

    components:{
        AlbumCard
    },

    data(){
        return{
            apiURL: 'https://flynn.boolean.careers/exercises/api/array/music',
            albumsList: [],
        }
    },

    created() {
        this.getMusicInfo();
    },

    methods: {

        /**
         * @url url dell'api da chiamare
         * @spazio array dove inserire il dato chiamato
         */
        getMusicInfo(){
            axios.get(this.apiURL)
            .then( resp =>{
                console.log(resp.data.response);
                this.albumsList = resp.data.response;
                console.log(this.albumsList);
            })
        }
    }
}
</script>


<style lang='scss' scoped>
@import '@/components/scss/var';

main{
    margin-top: 140px;

    .container{
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    
    }
}


</style>