<template>
    <transition name="fade">
        <div v-if="display" class="lightbox-wrapper">
            <div class="lightbox-toolbar">
                <button id="close-button" class="mdl-button mdl-button--icon mdl-js-button mdl-js-ripple-effect" tag="button" @click="close">
                    <i class="material-icons material-icons-white">cancel</i>
                </button>
                <button id="download-button" class="menu_icon add mdl-button mdl-button--icon mdl-js-button mdl-js-ripple-effect" @click="download">
                    <i class="material-icons material-icons-white">save</i>
                </button>
            </div>

            <div class="lightbox-overlay" @click="close()">
                <img class="full-image" :src="imageData" alt="Image">
            </div>
        </div>
    </transition>
</template>

<script>

import store from '@/store/';

export default {
    name: 'Imageviewer',

    data () {
        return {
            imageData: '',
            display: false
        };
    },

    mounted () {
        store.state.msgbus.$on('showImage', this.showImage);
        store.state.msgbus.$on('hideImage', this.close);
        store.state.msgbus.$on('hotkey-esc', this.close);
    },

    beforeDestroy () {
        this.$store.state.msgbus.$off('showImage', this.showImage);
        this.$store.state.msgbus.$off('hideImage', this.close);
        this.$store.state.msgbus.$off('hotkey-esc', this.close);
    },

    methods: {
        close () {
            this.display = false;
            this.imageData = '';
        },

        download () {
            var link = document.createElement('a');
            link.download = `heart-image-${new Date().getTime()}.jpg`;
            link.href = document.querySelector('.full-image').src;
            document.body.appendChild(link);

            link.click();
            document.body.removeChild(link);
        },

        downloadUri () {

        },

        showImage (eventObj) {
            const MediaLoader = store.state.media_loader;
            MediaLoader.getMedia(eventObj.messageId, eventObj.type)
                .then((blob) => {
                    this.display = true;

                    const dataPrefix = 'data:' + this.mime + ';base64,';
                    this.imageData = dataPrefix + blob;
                });
        }
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
    .lightbox-toolbar {
        position: fixed;
        top: 0;
        right: 0;
        z-index: 1001;
    }

    .lightbox-wrapper {
        height: 100%;
    }

    .lightbox-overlay {
        text-align: center;
        background-color: rgba(0,0,0,1);
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: 1000;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .full-image {
        display: flex;
        height: auto;
        width: auto;
        max-height: 100%;
        max-width: 100%;
    }

    #download-button {
        float: right;
        margin-right: 10px;
        margin-top: 20px;
        color: white;
        z-index: 1001;
    }

    #close-button {
        float: right;
        margin-right: 20px;
        margin-top: 20px;
        color: white;
        z-index: 1001;
    }

</style>
