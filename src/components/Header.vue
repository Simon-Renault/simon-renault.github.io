<template>
    <header class="header " :class="{'fixed':isFixed,'absolute':!isFixed}" >
      
           <img src="/img/logo.svg" alt="">
           <nav>
                <g-link to="/"  class="link" >Design</g-link>
                <g-link to="/x" class="link" >Blog</g-link>
                <g-link to="/x" class="link" >Experiments</g-link>
                <g-link to="/x" class="link" >Projets</g-link>
                <g-link to="/x" class="link" >About</g-link>
           </nav>
            <g-link to="/about" class="link" >Contact me</g-link>
      
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
        let header_height = 3
        if(dist > header_height &&  this.isFixed === false){
            this.isFixed = true
        }
        if(dist < header_height && this.isFixed === true){
             this.isFixed = false
        }
    },10));
  }
}
</script>

<style lang="scss" scoped>
.header {
    position: fixed;
    top:0;
    left:0;
    right:0;
    z-index: 10;
    display:flex;
    padding: 0 4%;
    justify-content: space-between;
    background-color: transparent;
    align-items: center;
    height:7rem;
    transition: height .4s ease, box-shadow .5s ease , background-color .3s ease,backdrop-filter .3s ease;
    //backdrop-filter: blur(0px);
    &.fixed{
        height: 4rem;
        //backdrop-filter: blur(30px);
        background-color: rgba(255,255,255,0.5);
        box-shadow: 0 0 10px 0px rgba(0,0,0,0.03) , 0 0 30px 0px rgba(0,0,0,0.02);
        animation-name: slide;
        animation-duration: .5s;
        animation-fill-mode: forwards;
    }
    .link{
        margin: 0 17px;
        font-weight: 600;
        position: relative;
        &::before{
            content:'';
            position: absolute;
            height: 2px;
            width:0%;
            background: #000;
            bottom: -5px;
            transition: width .3s ease;
        }
        &:hover::before{
            width:70%;
        }
        &.active::before{
            width:70%;
        }
    }
}



</style>
