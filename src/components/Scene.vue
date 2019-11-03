<template>
    <div class="container">
        <div class="canvas">
            <div class="circle" :style="styleObject"></div>
        </div>
        <keyboard @goTo="goTo($event)" :isEnabled="isEnabled"></keyboard>
    </div>
</template>

<script>
    import Keyboard from './Keyboard.vue'

    export default {
        data(){
            return {
                resolvTop: false,
                resolvBottom: false,
                resolvLeft: false,
                resolvRight: false,
                curenLleft: 150,
                curenTop: 150,
                isEnabled: {
                    top: false,
                    bottom: false,
                    right: false,
                    left: false
                }
            }       
        },

        computed: {
			styleObject() {
				return {
                    left: this.curenLleft + 'px',
                    top: this.curenTop + 'px'
                }
			}
		},

        watch: {
            resolvTop() {
                const fn = () => {
                    if(this.resolvTop){
                        this.isEnabled.bottom = false;
                        if(this.curenTop > 0){
                            this.curenTop -= 1;
                            setTimeout(fn, 3)
                        } else{
                            this.isEnabled.top = true;
                            this.resolvTop = false;
                        }
                    }
                }
                setTimeout(fn, 0); 
            },
            resolvBottom() {
                const fn = () =>{
                    if(this.resolvBottom){
                        this.isEnabled.top = false;
                        if(this.curenTop < 300){
                            this.curenTop += 1;
                            setTimeout(fn, 3)
                        } else{
                            this.isEnabled.bottom = true;
                            this.resolvBottom = false;
                        }

                    }
                }
                setTimeout(fn, 0); 
            },
            resolvLeft() {
                const fn = () =>{
                    if(this.resolvLeft){
                        if(this.curenLleft > 0){
                            this.isEnabled.right = false;
                            this.curenLleft -= 1;
                            setTimeout(fn,3 )
                        } else{
                            this.isEnabled.left = true;
                            this.resolvLeft = false;
                        }
                    }
                }
                setTimeout(fn, 0); 
            },
            resolvRight() {
                const fn = () =>{
                    if(this.resolvRight){
                        if(this.curenLleft < 300){
                            this.isEnabled.left = false;
                            this.curenLleft += 1;
                            setTimeout(fn,3)
                        } else{
                            this.isEnabled.right = true;
                            this.resolvRight = false;
                        }
                    }
                }
                setTimeout(fn, 0); 
            }
        },

        methods: {
            goTo(event) {
                 this[event.name] = event.value
            }
        },

        components: {
            Keyboard
        }
    }
</script>

<style scoped>
    .canvas {
        width: 400px;
        height: 400px;
        position: relative;
        background-color: #bbe7f0;
        border: 1px solid #000;
    }
    .circle {
        box-sizing: border-box;
        width: 100px;
        height: 100px;
        position: absolute;
        border-radius: 50px;
        border: 1px solid #000;
    }

    .container {
      display: flex;
      align-items: center;
      justify-content: center;
    }
    
</style>