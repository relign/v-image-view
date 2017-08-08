<template>
    <section class="example-box">
        <h3>单图预览(图片与预览图片分开)</h3>
        <div>
            <v-image-view
                :img-width="200"
                :img-height="200"
                :view-title="false"
                view-url="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1502171031557&di=95c16002744261a85bbec0a0eb3c5906&imgtype=0&src=http%3A%2F%2Fimgstore.cdn.sogou.com%2Fapp%2Fa%2F100540002%2F881025.jpg"
                empty-message="暂无图片"
                :img-url="'http://img0.imgtn.bdimg.com/it/u=3977996883,4096693033&fm=26&gp=0.jpg'"
            >
            </v-image-view>
        </div>
        <h3>单图预览(支持全屏预览)</h3>
        <div>
            <v-image-view
                :img-width="150"
                :img-height="150"
                :view-fullscreen="true"
                empty-message="暂无图片"
                :img-url="'http://img0.imgtn.bdimg.com/it/u=3206479345,2477776551&fm=26&gp=0.jpg'"
            >
            </v-image-view>
        </div>
        <h3>单图预览(工具栏隐藏)</h3>
        <div>
            <v-image-view
                :img-width="150"
                :img-height="150"
                :view-fullscreen="true"
                :view-toolbar="false"
                empty-message="暂无图片"
                :img-url="'http://img5.imgtn.bdimg.com/it/u=105228323,1287421560&fm=26&gp=0.jpg'"
            >
            </v-image-view>
        </div>
        <h3>单图预览(点击预览)</h3>
        <div>
            <button class="btn btn-primary" @click="showView()">预览</button>
            <v-image-view
                :img-width="150"
                :img-height="150"
                :view-fullscreen="true"
                :view-trigger.sync="viewShow"
                :img-url="'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1502171212218&di=b056121f48b2696f6516933e1b820151&imgtype=0&src=http%3A%2F%2Fpic40.nipic.com%2F20140412%2F17568098_220839323196_2.jpg'"
            >
            </v-image-view>
        </div>
        <h3>单图预览(传入options对象)</h3>
        <div>
            <v-image-view
                :img-width="150"
                :img-height="150"
                :view-fullscreen="true"
                :view-options="viewOptions"
                :img-url="'https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=2545970364,2764082774&fm=26&gp=0.jpg'"
            >
            </v-image-view>
        </div>
        <h3>多图预览</h3>
        <div>
            <v-image-view
                :multiple-image="true"
                :view-navbar="true"
            >
                <ul class="images-list-box clearfix" slot="imagesList">
                    <li><img src="https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=2545970364,2764082774&fm=26&gp=0.jpg" alt=""></li>
                    <li><img src="https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=2545970364,2764082774&fm=26&gp=0.jpg" alt=""></li>
                    <li><img src="https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=551688346,3402665354&fm=26&gp=0.jpg" alt=""></li>
                    <li><img src="http://img0.imgtn.bdimg.com/it/u=3206479345,2477776551&fm=26&gp=0.jpg" alt=""></li>
                    <li><img src="http://img5.imgtn.bdimg.com/it/u=105228323,1287421560&fm=26&gp=0.jpg" alt=""></li>
                </ul>
            </v-image-view>
        </div>
    </section>
</template>
<script>
import VImageView from '../src/';
export default {
    data () {
        return {
            viewOptions: {
                transition: false,
                keyboard: false,
                scalable: false
            },
            viewShow: false
        };
    },
    components: {
        'v-image-view': VImageView
    },
    methods: {
        showView () {
            this.viewShow = true;
        }
    }
};
</script>
<style lang="scss">
$icon-font-path: '~bootstrap-sass/assets/fonts/bootstrap/';
@import '~bootstrap-sass/assets/stylesheets/_bootstrap.scss';

.example-box {
    padding: 20px;
}
.images-list-box {
    li {
        float: left;
        width: 33.3%;
        height: 33.3%;
        margin: 0 -1px -1px 0;
        border: 1px solid transparent;
        overflow: hidden;
        img {
            width: 100%;
            vertical-align: middle;
            cursor: zoom-in;
        }
    }
}
</style>

