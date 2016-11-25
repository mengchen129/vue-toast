<template>
    <transition name="toast-fade">
        <div class="toast-wrap" v-show="showing">{{text}}</div>
    </transition>
</template>

<script>
    const DEFAULT_DURATION = 3000;
    import Utils from './Utils';
    export default {
        name: 'toast',
        data() {
            return {
                text: '',
                showing: false,
                timer: null
            };
        },
        mounted: function() {
            console.log('toast mounted...');
            // 将公共方法注册到Utils中
            Utils.register('toast', this.show);
        },
        methods: {
            show: function(text, duration) {
                this.text = text;
                this.showing = true;
                if (this.timer) {
                    clearInterval(this.timer);
                }
                this.timer = setTimeout(() => {
                    this.showing = false;
                }, duration || DEFAULT_DURATION);
            }
        }
    }
</script>

<style>
    .toast-wrap {
        position: fixed;
        bottom: 50px;
        left: 0;
        right: 0;
        width: 50%;
        margin-left: auto;
        margin-right: auto;
        background-color: rgba(0, 0, 0, 0.7);
        color: #ffffff;
        text-align: center;
        padding: 5px;
        font-size: 12px;
        border-radius: 5px;
    }
    .toast-fade-enter-active, .toast-fade-leave-active {
        transition: opacity .5s;
    }
    .toast-fade-enter, .toast-fade-leave-active {
        opacity: 0
    }
</style>