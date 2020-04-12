<template>
    <footer class="footer">
       <g-link class="contact">Work with me !</g-link>
       <p class="copyright">Copyright simon renault 2020</p>
    </footer>
</template>

<script>
export default {
    data() {
        return {
            settings: require("../../data/theme.json")
        }
    }
}
</script>

<style lang="scss" scoped>
.footer {
    z-index: 1;
    height: 400px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    .contact{
        margin: 30px 10px 100px;
        font-weight: 600;
    }
    .copyright{
        color: #818181;
        font-size: 14px;
        font-weight: 300;
    }
}
</style>
