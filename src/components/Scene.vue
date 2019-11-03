<template>
    <div class="canvas">
        <div class="circle" :style="styleObject"></div>
    </div>
</template>

<script>
    import { bus } from '../main.js';

    export default {
        created(){
            bus.$on('goTo', event => this[event.name] = event.value);
        },

        data(){
            return {
                resolvTop: false,
                resolvBottom: false,
                resolvLeft: false,
                resolvRight: false,
                curenLleft: 150,
                curenTop: 150
            }       
        },

        computed: {
			styleObject(){
				return {
                    left: this.curenLleft + 'px',
                    top: this.curenTop + 'px'
                }
			}
		},

        watch: {
            resolvTop(){
                const fn = () => {
                    if(this.resolvTop &&  this.curenTop > 0){
                     this.curenTop -= 1;
                        setTimeout(fn, 3)
                    }
                }

                setTimeout(fn, 0); 
            },
            resolvBottom(){
                const fn = () =>{
                    if(this.resolvBottom &&  this.curenTop < 300){
                     this.curenTop += 1;
                        setTimeout(fn, 3)
                    }
                }
                setTimeout(fn, 0); 
            },
            resolvLeft(){
                const fn = () =>{
                    if(this.resolvLeft &&  this.curenLleft > 0){
                     this.curenLleft -= 1;
                        setTimeout(fn,3 )
                    }
                }
                setTimeout(fn, 0); 
            },
            resolvRight(){
                const fn = () =>{
                    if(this.resolvRight &&  this.curenLleft < 300){
                     this.curenLleft += 1;
                        setTimeout(fn,3)
                    }
                }
                setTimeout(fn, 0); 
            }
        }
    }
</script>

<style>
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
</style>