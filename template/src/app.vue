<template>
    <div v-if="show" class="mask" @click="click" :style="style">
        <slot></slot>
    </div>
</template>

<script>
    export default {
        props: {
            show: {
                default: true
            },

            opacity: {
                type: [Number, String],
                default: 0.6
            },

            zIndex: {
                type: [Number, String],
                default: 998
            }
        },

        computed: {
            style () {
                let style = {};

                if (this.width) {
                    style.width = this.width;
                }
                if (this.opacity) {
                    style['background-color'] = `rgba(0, 0, 0, ${this.opacity})`;
                }
                if (this.zIndex) {
                    style['zIndex'] = this.zIndex;
                }
                style.marginTop = this.top;
                return style;
            }
        },

        methods: {
            click: function() {
                this.$emit('click');
            }
        }
    }
</script>

<style>
    .mask {
        position: fixed;
        top: -80%;
        left: 0;
        width: 100%;
        height: 200%;
        padding-bottom: 2px;
        z-index: 998;
    }
</style>
