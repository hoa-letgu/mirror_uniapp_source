<template><view class="viewer"><web-view :src="url" @message="onMessage"/></view></template>
<script setup>import {ref} from 'vue';import {onLoad} from '@dcloudio/uni-app';const url=ref('/hybrid/html/rubik/index.html');onLoad((params)=>{if(params.id)url.value='/hybrid/html/rubik/index.html?id='+encodeURIComponent(params.id)});function onMessage(e){console.log('Rubik WebView:',e.detail.data)}</script>
<style scoped>.viewer{height:100vh}</style>
