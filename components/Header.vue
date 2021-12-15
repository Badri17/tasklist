

<template>
    <view class="header"> 
        <text class="title">{{title}}</text>
    </view>
</template>

<script>
export default {
    props: ['title']
}
</script>

<style>
.header {
    height: 67px;
    background-color: rgb(30, 114, 139);
    justify-content: center;
    align-items: center;
   
}

.title {
    color: rgb(255, 255, 255);
    font-size: 40px;
    font-weight: 900;
}
</style>