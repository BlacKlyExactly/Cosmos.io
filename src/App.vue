<template>
  <div id="app">
      <div class="navbar">
        <ul>
          <li class="select">Cosmos.io</li>
          <li class="select" @click="slideSearch">Search</li>
          <li class="select" @click="slideBug">Bug?</li>
        </ul>
      </div>
      <div class="header">
        <parallax class="parallax">
          <img src="https://images.pexels.com/photos/132037/pexels-photo-132037.jpeg">
        </parallax>
        <div class="headerTitle">
            Cosmos.io
            <div class="headerSubtitle">
              Learn everything about <br/> <span>COSMOS</span>
            </div>
        </div>
        <div class="next">
          LET'S START
          <button class="button" @click="slideSearch">NEXT</button>
        </div>
      </div>
      <div class="content">
        <Search></Search>
      </div>
    <FindBug></FindBug>
  </div>
</template>

<script>
  import Search from "./components/Search.vue"
  import Parallax from "vue-parallaxy";
  import FindBug from "./components/FindBug.vue"
export default {
  name: 'app',
  components: {
    Parallax,
    Search,
    FindBug,
  },
  beforeMount(){
    this.navbarScroll();
  },
  methods:{
    navbarScroll(){

      document.addEventListener('scroll' , ()=> {
        if(window.scrollY==0){
          document.querySelector('.navbar').style.background="transparent";
          document.querySelectorAll('.select').forEach(select => {
            select.style.color="white";
          })
        }else{
          document.querySelector('.navbar').style.background="white";
          document.querySelectorAll('.select').forEach(select => {
            select.style.color="#FE0090";
          })
        }
      })
    },
    slideSearch(){
      window.scroll(0, document.querySelector('.search').offsetTop)
    },
    slideBug(){
      window.scroll(0, document.querySelector('.bug').offsetTop)
    }
  }
};
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Montserrat');

  #app {
position: absolute;
margin: 0;
padding: 0;
  left: 0;
  top: 0;
 width: 100vw;
overflow-x: hidden;
    font-family: 'Montserrat', sans-serif;
    font-weight: 900;
  }
  *{
    scroll-behavior: smooth;
  }
.header{
  position: relative;
  margin: 0;
  padding: 0;
  display: flex;
  left: 0;
  top: 0;
  overflow: hidden;
  width: 100vw;
  background:url("assets/Image1.png");
  background-size: cover;
  z-index: 1;
  &:after, &:before{
    content: "";
    position: absolute;
    left: 31vw;
    height: 103vh;
    width: 70vw;
    overflow:hidden;
  }
  &:after{
    background:url("assets/Path1@2x.png");
    background-size: cover;
    z-index: 2;
  }
  &:before{
    background:url("assets/Path2@2x.png");
    background-size: cover;
    top: 4vw;
    z-index: 3;
  }
}
.headerTitle{
  color: white;
  font-size: 8vmax;
  align-self: center;
  margin-top: -18vw;
  margin-left: 8vw;
  text-shadow: 0vw .2vw 2vw black;
  font-weight: bold;
}
.headerSubtitle{
  font-size: 3vmax;
  font-weight: 800;
  span{
    color: #FE0090;
    font-weight: 900;
  }
}
.next{
  color: #FE0090;
  position: relative;
  align-self: center;
  top:8vw;
  margin: 20vw 5vw 0vw 12vw;
  z-index: 5;
  font-size: 5vmax;
  font-weight: 900 !important;
}
.button{
  border: .15vw solid #FE0090;
  width: 24vw;
  font-size: 2.5vw;
  height: 6vw;
  margin-top: 5vw;
  background: transparent;
  color: #FE0090;
  font-family: 'Montserrat', sans-serif;
  font-weight: 900;
  border-radius: 25vw;
  transition: 0.25s;
  &:hover{
    color: white;
    background: #FE0090;
    cursor: pointer;
  }
}
.navbar{
  position: fixed;
  top: 0;
  left: 0;
  transition: 0.2s;
  z-index: 100;
  width: 99vw;
  ul{
    position: relative;
    display: flex;
    justify-content: flex-end;
    list-style: none;
    .select{
      color:white;
    }
    li{
      font-weight: 900;
      font-size: 1.7vmax;
      padding: 1vw;
      transition: 0.2s;
      &:hover{
        background: #FE0090;
        cursor: pointer;
        box-shadow: 0vw 0vw 2vw .2vw #FE0090;
      }
      &:first-child{
        position: relative;
        margin-right: auto;
      }
      &:nth-child(2), &:nth-child(3){
        margin-right: 3vw;
      }
    }
  }
}
.content{
  height: 80vw;
  display: flex;
  align-items: center;
  justify-content: center;
}
.title{

}
</style>
