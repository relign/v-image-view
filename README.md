# image-view

> vue image view component

<div style="text-align:center">
</div>

### install component

```bash
$ npm install v-image-view --save-dev
```

### check Demo

```bash
# install dependencies
$ npm install v-image-view --save-dev

# dev mode
$ npm run dev

```


### Attributes

参数            | 说明                                                                 | 类型             | 可选值                              | 默认值
------------- | ------------------------------------------------------------------ | -------------- | -------------------------------- | -----
imgWidth      | 图片宽                                                                | Number         | --                   | 100
imgHeight         | 图片高                                                                | Number | --                               | 100
emptyMessage     | 无图片时展示文案                                                             | String         | --                               | --
viewTitle     | 预览图片时是否展示图片名                                                             | Boolean         | --                               | true
imgUrl   | 图片url                                                            | String         | --                               | --
viewUrl      | 预览图片url                                                                 | String        | --                               | --
viewFullscreen          | 是否支持图片全屏预览                                    | Boolean         | --               | false
viewToolbar          | 是否显示图片工具栏                                                            | Boolean         | --                               | true
viewNavbar          | 预览时是否展示缩略图                                      | Boolean         | --                               | false
multipleImage      | 支持多图预览 | Boolean | --                               | false
viewOptions | options设置,详细见[viewerjs](https://github.com/fengyuanchen/viewerjs)                                                          | Object         | --                          | --


更多设置见[viewerjs](https://github.com/fengyuanchen/viewerjs)

