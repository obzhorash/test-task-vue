<template>
    <div class="controls">
        <div class="top-control">
            <button type="button"
                    :disabled="isEnabled.top"
                    @mousedown="goTop(true)"
                    @mouseup="goTop(false)"
                    @mouseout="goTop(false)">
                &#8593;
            </button>  
        </div>    
        <button type="button"
                :disabled="isEnabled.left"
                @mousedown="goLeft(true)"
                @mouseup="goLeft(false)"
                @mouseout="goLeft(false)">
            &#8592;
        </button>
        <button type="button"
                :disabled="isEnabled.bottom"
                @mousedown="goBottom(true)"
                @mouseup="goBottom(false)"
                @mouseout="goBottom(false)">
                &#8595;
        </button>
        <button type="button"
                :disabled="isEnabled.right"
                @mousedown="goRight(true)"
                @mouseup="goRight(false)"
                @mouseout="goRight(false)">
            &#8594;
        </button>
        
    </div>
</template>

<script>
    export default {
        props: {
            isEnabled: {
                default: () => ({
                    top: false,
                    bottom: false,
                    right: false,
                    left: false
                }),
                type: Object 
            }
        },
        methods: {
            goTop(data) {
                this.$emit('goTo',{name: 'resolvTop', value: data});
            },
            goBottom(data) {
                this.$emit('goTo', {name: 'resolvBottom', value: data});
            },
            goRight(data) {
                this.$emit('goTo', {name: 'resolvRight', value: data});
            },
            goLeft(data) {
                this.$emit('goTo', {name: 'resolvLeft', value: data});
            }
        }
    }
</script>

<style scoped>
    .controls {
        margin-left: 10px;
    }
    
    .top-control {
        width: 40px;
        margin: 0 auto;
    }

    button[type="button"] {
        disable: true;
        box-sizing: border-box;
        width: 40px;
        height: 40px;
    }

    button[disabled] {
        background-color: #cecece;
    }
</style>