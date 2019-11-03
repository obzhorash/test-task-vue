<template>
    <div class="container">
        <div class="top-control">
            <button type="button"
                    @mousedown="goTop(true)"
                    @mouseup="goTop(false)"
                    @mouseout="goTop(false)">
                &#8593;
            </button>  
        </div>    
        <button type="button"
                @mousedown="goLeft(true)"
                @mouseup="goLeft(false)"
                @mouseout="goLeft(false)">
            &#8592;
        </button>
        <button type="button"
                @mousedown="goBottom(true)"
                @mouseup="goBottom(false)"
                @mouseout="goBottom(false)">
                &#8595;
        </button>
        <button type="button"
                @mousedown="goRight(true)"
                @mouseup="goRight(false)"
                @mouseout="goRight(false)">
            &#8594;
        </button>
        
    </div>
</template>

<script>
    import { bus } from '../main';

    export default {

        methods: {
            goTop(data) {
                bus.$emit('goTo',{name: 'resolvTop', value: data});
            },
            goBottom(data) {
                bus.$emit('goTo', {name: 'resolvBottom', value: data});
            },
            goRight(data) {
                bus.$emit('goTo',{name: 'resolvRight', value: data});
            },
            goLeft(data) {
                bus.$emit('goTo', {name: 'resolvLeft', value: data});
            }
        }
    }
</script>

<style>
    .container {
        width: 120px;
        margin-left: 10px;
    }
    
    .top-control {
        width: 40px;
        margin: 0 auto;
    }

    button[type="button"] {
        box-sizing: border-box;
        width: 40px;
        height: 40px;
    }
</style>