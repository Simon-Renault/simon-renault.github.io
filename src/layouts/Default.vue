<template>
  <div class="layout">
        <Header />
        <main class="main">
            <slot/>
          
            <section class="section">
                <div class="section__inner">
                    <div class="tile loading v-3 h-3" >
                        <g-image class="cover" src="https://images.unsplash.com/photo-1558980664-769d59546b3d?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2250&q=80"></g-image>
                    </div>
                    <div class="tile loading"></div>
                    <div class="tile loading"></div>
                    <div class="tile loading"></div>
                </div>
            </section>

             <section class="section">
                <header class="section__header">
                    <h2>What I bluit</h2>
                    <p class="desc">
                        I recently started to express myself trough writing. I have always liked to share knowledge and to teach, Medium is a place where I write about daily thoughts but also build courses.
                    </p>
                </header>
                <div class="section__inner">
                    <div class="tile loading v-3 h-3" ></div>
                    <div class="tile loading"></div>
                    <div class="tile loading v-2"></div>
                   
                </div>
            </section>
        
        </main>
        <Footer />
        <div class="lines">
            <span></span>
            <span></span>
            <span></span>
        </div>

        
    </div>
    
</template>

<script>
import Header from "@/components/Header"
import Footer from "@/components/Footer"

export default {
  components: {
    Header,
    Footer
  }
}
</script>


<style lang="scss">


.h{
    &-1{
        grid-column: span 1;
    }
    &-2{
        grid-column: span 2;
    }
    &-3{
        grid-column: span 2;
    }
}
.v{
    &-1{
        grid-row: span 1;
    }
    &-2{
        grid-row: span 2;
    }
    &-3{
        grid-row: span 3;
    }
}

.g-image{
    &.cover{
        position: absolute;
        object-fit: cover;
    }
}

h2{
    font-size: 45px;
}
p{
    font-size: 22;
    color: #7A8284;
    line-height: 1.6;
    font-weight: 300;
    margin: 20px 0 10px;
    max-width: 70%;
}


.section{
    position: relative;
    margin: 10vh auto 0;
    flex-direction: column;
    align-items: center;
    height: 90vh;
    justify-content: center;
    width: 78vw;
    display: grid;
    grid-template-columns: 1fr;
    grid-gap: 20px;
    &__header{

    }
    &__inner{
        width: 100%;
        display: grid;
        grid-gap: 20px;
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-rows: 440px 200px 70px;
        grid-auto-flow: dense;
    }
}
.tile{
    position: relative;
    background:#F3F3F4;
    border-radius: 2px;
    overflow: hidden;
    &.loading:before {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        animation-name: shimmer;
        animation-duration: 1.5s;
        animation-fill-mode: forwards;
        animation-iteration-count: infinite;
        animation-timing-function: linear;
        background-size: 100vw 100%;
        background-repeat: no-repeat;
        z-index: 0;
        background-image: linear-gradient(90deg,rgba(235,238,240,0),#cdd6db);
    }
}

@keyframes shimmer {
    0% {
        transform: translateX(-100%)
    }

    to {
        transform: translateX(100%)
    }
}

*,*::before,*::after {
  box-sizing: border-box;
  margin:0;
  padding: 0;
}
a{
    text-decoration: none;
    color: inherit
}
#app{
    position: relative;
    overflow: hidden;
}
.lines{
    position: absolute;
    z-index: -1;
    top:0;
    left:0;
    right:0;
    bottom:0;
    display: flex;
    justify-content: space-around;
    padding: 0 10%;
    span{
        display: block;
        background: #E0E0E0;
        height: 100%;
        width:1px;
        animation-name: show_lines;
        animation-duration: 2s;
    }
}

@keyframes show_lines {
  0% {height: 0px;}
  99% {height: 110vh;}
  100% {height: 100%;}
}


main{
    z-index: 1;
    min-height: 100vh;
}

body {
  --color-base: rgb(255, 255, 255);
  --color-base-1: rgb(243, 243, 243);
  --color-contrast: rgb(0, 0, 0);
  --color-contrast-1: rgb(43, 43, 43);
  font-family: -apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  font-size: 16px;
  background: var(--color-base);
  color: var(--color-contrast);
  transition: background 0.5s ease;
}

body.dark {
  --color-base: rgb(0, 0, 0);
  --color-base-1: rgb(43, 43, 43);
  --color-contrast: rgb(255, 255, 255);
  --color-contrast-1: rgb(243, 243, 243);
}


img {
  max-width: 100%;
}


</style>
