<template>
    <header class="header fixed" :class="{'cool':isFixed}" >
      
           <img src="/img/logo.svg" alt="">
           <nav>
                <g-link to="" >Projets</g-link>
                <g-link to="" >Projets</g-link>
                <g-link to="" >Projets</g-link>
                <g-link to="" >Projets</g-link>
           </nav>
            <g-link to="/about" >Contact me</g-link>
      
      
    </header>
</template>

<script>
import { debounce,throttle } from 'lodash';

export default {
  data() {
    return {
        logo: require("../../static/logo.svg"),
        settings: require("../../data/theme.json"),
        isFixed: false
    }
  },
  mounted(){
    const scroll_container = document.body

    window.addEventListener('scroll', debounce((e)=>{
        let dist =  window.pageYOffset;
        let header_height = 50
        if(dist > header_height &&  this.isFixed === false){
            this.isFixed = true
        }
        if(dist < header_height && this.isFixed === true){
             this.isFixed = false
        }
    },50));
  }
}
</script>

<style lang="scss" scoped>
.header {
    height: 6rem;
    z-index: 10;
    display:flex;
    justify-content: space-between;
    align-items: baseline;
    padding: 30px 5%;
    opacity: 0;
    animation-name: appear;
    animation-duration: .5s;
    animation-fill-mode: forwards;
    &.fixed{
        position: fixed;
        top:0;
        left:0;
        right:0;
    }
    &.cool{
        opacity: 1;
        animation-name: disappear;
        animation-duration: .5s;
        animation-fill-mode: forwards;
    }
    nav{

    }
    a{
        margin:10px;

        font-weight: 600;
    }
}



@keyframes appear {
  0% {opacity:0;}
  100% {opacity:1;}
}
@keyframes disappear {
  0% {opacity:1;}
  100% {opacity:0;}
}

</style>
