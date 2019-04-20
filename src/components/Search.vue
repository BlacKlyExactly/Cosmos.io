<template>
    <div class="search">
      <div class="title">Search your favorite cosmic thing</div>
        <input type="text" v-model="inputValue">
         <button @click="apiCall">Check</button>
          <div class="window" v-if="isSearched">
            <div class="button" @click="hide">Back</div>
            <div class="error" v-if="error" >ERROR</div>
            <ul style="list-style: none">
            <li v-for="item in images" :key="item.data.nasa_id">
              <img alt="" v-bind:src="item.links[0].href">
            </li>
          </ul>
          </div>

    </div>
</template>

<script>
  const API = 'https://images-api.nasa.gov/search';
  import  axios from "axios";
    export default {
        name: "Search",
        data(){
          return {
            inputValue: "",
            images:[],
            isSearched:false,
            error:false
          };
        },
      methods:{
         apiCall(){
           axios.get(`${API}?q=${this.inputValue}&media_type=image`)
             .then(response => {
               this.images = response.data.collection.items;
               this.isSearched=true
             })
             .catch(error=>{
               this.isSearched=true
               this.error = true;
             })
         },
        hide(){
          this.isSearched=false;
        },
      }
    }
</script>

<style scoped lang="scss">
.title{
  font-size: 4.5vmin;
  color: #FE0090;
  margin-bottom: 10vw;
  width: 40vw;
}
.search{
  display: flex;
  flex-direction: column;
  justify-content: center;
  ul{
    display: inline-block;
  }
  input[type="text"]{
    border-bottom: .2vw solid #FE0090;
    border-top: none;
    border-left: none;
    border-right: none;
    width: 80vw;
    font-size: 2vw;
    color: #FE0090;
  }
  button{
    position: relative;
    width:15vw;
    height: 5vw;
    display: flex;
    align-items: center;
    justify-content: center;
    background: transparent;
    border: .2vw solid #FE0090;
    border-radius: 25vw;
    margin-top: 5vw;
    color: #FE0090;
    font-size: 1.5vw;
    display: flex;
    transition: .2s;
    cursor: pointer;
    &:hover{
      color: white;
      background: #FE0090;
    }
  }
}
.window{
  background: white;
  position: fixed;
  z-index: 150;
  height:100vh;
  width: 100vw;
  top: 0;
  left: 0;
  overflow: scroll;
  /* width */
  ::-webkit-scrollbar {
    width: 10px;
  }

  /* Track */
  ::-webkit-scrollbar-track {
    background: #f1f1f1;
  }

  /* Handle */
  ::-webkit-scrollbar-thumb {
    background: #888;
  }

  /* Handle on hover */
  ::-webkit-scrollbar-thumb:hover {
    background: #555;
  }
}
 .error{
   font-size: 8vw;
   color: red;
   position: fixed;
   top: 0;
   left: 0;
 }
  .button{
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>
