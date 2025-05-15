<template>
    <div class="qr-wrapper">
        <h2>QR CODE to portfolio</h2>
        <canvas ref="canvas"></canvas>
        <p>Scan this QR Code to open it</p>
        <button class="visit-btn" @click="visitSite">Go on QR</button>
    </div>
</template>


<script>
import QRCode from 'qrcode'
export default{
    name: 'QRCode',
    data(){
        return{
            url: 'https://slukki.github.io/vue-robot/#/'//указываем нужную ссылку
        }
    },
    mounted(){
        const canvas = this.$refs.canvas
        if (canvas) {
            QRCode.toCanvas(canvas, this.url, {width: 180}, (error) =>{
                if (error) console.error(error)
            })
        }
    },
    methods: {
        visitSite(){
        window.open(this.url, '_blank')
    }
    }
}
</script>