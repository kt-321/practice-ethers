<template>
    <div class="page-index" title="PracticeEthers">
        <p style="font-size: 12px">wallet</p>
        <p>{{ this.connectedMetamask() }}</p>
        <button @click="connectedMetamask">wallet</button>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import { ethers } from 'ethers'

// @Component({})
export default class PageIndex extends Vue {
    connectedMetamask () {
        console.log("window.ethereum", window.ethereum)
        const provider = window.ethereum != null
        ? new ethers.providers.Web3Provider(window.ethereum, 'any')
        : ethers.getDefaultProvider();
        console.log("provider:", provider)
    }

    mounted () {
        this.connectedMetamask()
    }
}
</script>

<style lang="stylus"></style>
