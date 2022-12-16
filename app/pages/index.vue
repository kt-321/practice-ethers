<template>
    <div class="page-index" title="PracticeEthers">
        <p style="font-size: 12px">wallet</p>
        <button @click="handleMetamaskConnection">ウォレット接続</button>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import { ethers } from 'ethers'

export default class PageIndex extends Vue {
    async handleMetamaskConnection() {
        if (!window.ethereum) {
            console.log('!window.ethereum')
            window.open('https://metamask.app.link/dapp/', '_blank', 'noopener noreferrer');
        } else {
            console.log('window.ethereum')

            const provider = new ethers.providers.Web3Provider(window.ethereum)
            const account = await provider.send('eth_requestAccounts', [])
            console.log("account:", account)

            const signer = await provider.getSigner()
            console.log("signer:", signer)

            const address = await signer.getAddress()
            console.log("address:", address)
            // const balance = await signer.getBalance()
            // console.log("balance:", balance)

            // TODO message
            // const message = 'message'
        }
    }
}
</script>

<style lang="stylus"></style>
