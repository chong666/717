<template>
    <div class="mask" :class="{'active':isActive}">
        <img src="../imgs/timg.gif" alt="">
      
    </div>
</template>
<script>
export default {
    name: 'mask-view',
    props: ['isActive'],
    mounted() {
        //this.isActive = this.$store.state.mask_active
    },
    methods: {

    }
}
</script>
<style>
.mask {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, .8);
    color: #fff;
    display: none;
    justify-content: center;
    align-items: center;
}
.mask img{
    width: 100px;
    height:100px;
    border-radius: 50%;
}
.active {
    display: flex;
}

</style>
