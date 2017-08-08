<template>
    <div class="v-image-view">
        <div
            v-if="!multipleImage"
            class="v-image-box"
            :style="{width: imgWidth + 'px', height: imgHeight + 'px'}"
            >
            <img
                ref="img"
                :data-original="viewUrl"
                v-if="imgUrl"
                @hide="viewHide"
                :src="imgUrl">
            <div
                v-if="!imgUrl"
                :style="{width: imgWidth + 'px', height: imgHeight + 'px'}"
                class="v-empty-img">
                {{emptyMessage}}
            </div>
        </div>
        <div
            v-if="multipleImage"
            ref="imagesBox"
            class="v-images-list">
            <slot name="imagesList">
            </slot>
        </div>
    </div>
</template>
<script>
import Viewer from 'viewerjs';

export default {
    name: 'v-image-view',
    componentName: 'VImageView',
    props: {
        imgWidth: {
            type: Number,
            default: 100
        },
        imgHeight: {
            type: Number,
            default: 100
        },
        imgUrl: {
            type: String,
            default: ''
        },
        viewUrl: {
            type: String,
            default: ''
        },
        emptyMessage: {
            type: String,
            default: ''
        },
        minViewWidth: {
            type: Number,
            default: 200
        },
        minViewHeight: {
            type: Number,
            default: 100
        },
        viewInline: {
            type: Boolean,
            default: false
        },
        viewTitle: {
            type: Boolean,
            default: true
        },
        viewFullscreen: {
            type: Boolean,
            default: false
        },
        viewToolbar: {
            type: Boolean,
            default: true
        },
        multipleImage: {
            type: Boolean,
            default: false
        },
        viewNavbar: {
            type: Boolean,
            default: false
        },
        viewOptions: {
            type: Object,
            default: () => {}
        },
        viewTrigger: {
            type: Boolean,
            default: false
        }
    },
    data () {
        return {
            viewInlineDisplay: 'show',
            options: {
                inline: false,
                navbar: false,
                title: true,
                fullscreen: false,
                toolbar: true,
                minWidth: 200,
                minHeight: 100,
                zIndex: 2015
            },
            viewer: {}
        };
    },
    mounted () {
        let imgElement;
        const options = this.initOptions();
        if (!this.multipleImage) {
            imgElement = this.$refs.img;
        } else {
            imgElement = this.$refs.imagesBox;
        }
        this.viewer = new Viewer(imgElement, options);
    },
    methods: {
        initOptions () {
            let viewAttr = 'src';
            if (this.viewUrl) {
                viewAttr = 'data-original';
            }
            const viewOptions = Object.assign(this.options, {
                minWidth: this.minViewWidth,
                minHeight: this.minViewHeight,
                inline: this.viewInline,
                title: this.viewTitle,
                fullscreen: this.viewFullscreen,
                toolbar: this.viewToolbar,
                navbar: this.viewNavbar,
                url: viewAttr
            }, this.viewOptions);
            return viewOptions;
        },
        showViewInline () {
            this.viewDisplay = 'show';
        },
        viewHide () {
            this.$emit('update:viewTrigger', false);
        }
    },
    watch: {
        viewTrigger (val) {
            if (val) {
                this.viewer.show();
            }
        }
    }
};
</script>
<style>
@import '~viewerjs/dist/viewer.min.css';
.v-image-view {
    width: 100%;
}
.v-image-view .v-image-box {
    border: 1px solid #d3dce6;
    cursor: pointer;

}
.v-image-view .v-image-box img {
    width: inherit;
    height: inherit;
}
.v-image-view .v-empty-img {
    background-color: #E5E9F2;
    text-align: center;
    padding: 10px;
    color: #666;
    position: relative;
    display: table-cell;
    vertical-align: middle;
}
</style>

