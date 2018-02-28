
#APICloud选择相册模块文档

##1.setParam
设置参数
```html
setParam(param,callback(ret))
ret：
类型：JSON对象
内部字段：
{
    status: true   //布尔型；true
}
param：

{
        allowTakePicture:true,  /// 默认为false，如果设置为false,拍照按钮将隐藏,用户将不能选择照片
        allowPickingVideo:false, /// 默认为false，如果设置为false,用户将不能选择视频
        allowPickingImage:true,  /// 默认为false，如果设置为false,用户将不能选择发送图片
        allowPickingOriginalPhoto:false, /// 默认为false，如果设置为false,原图按钮将隐藏，用户不能选择发送原图
        allowPickingGif:false, /// 默认为false，如果设置为false,用户可以选择gif图片
        allowPickingMultipleVideo:false,/// Default is false / 默认为false，为true时可以多选视频/gif图片，和照片共享最大可选张数maxImagesCount的限制
        sortAscendingByModificationDate:true,/// 对照片排序，按修改时间升序，默认是false。如果设置为false,最新的照片会显示在最前面，内部的拍照按钮会排在第一个
        showSelectBtn:false,  ///在单选模式下，照片列表页中，显示选择按钮,默认为false
        allowCrop:true,  ///< 允许裁剪,默认为false，showSelectBtn为false才生效
        needCircleCrop:false, //需要圆形裁剪框
        isSelectOriginalPhoto:false,//选择原图
        columnNumber:4, //一行显示的张数
        imagesCount:3, //最大选择照片数量
        cropRect:{
                  x:0,
                  y:0,
                  w:0,
                  h:0
                  } 裁剪区域暂时没用
    },function(ret, err){
        
    }
类型：JSON对象
内部字段：

```
####示例代码
```javascript 
var demo = api.require('WMImagePicker');
    
    demo.setParam({
        allowTakePicture:true,
        allowPickingVideo:false,
        allowPickingImage:true,
        allowPickingOriginalPhoto:false,
        allowPickingGif:false,
        allowPickingMultipleVideo:false,
        sortAscendingByModificationDate:true,
        showSelectBtn:false,
        allowCrop:true,
        needCircleCrop:false,
        isSelectOriginalPhoto:false,
        columnNumber:4,
        imagesCount:3,
        cropRect:{
                  x:0,
                  y:0,
                  w:0,
                  h:0
                  }
    },function(ret, err){
        var msg = "点击了第" + ret.status + "个按钮";
        api.toast({
            msg: msg
        });
    });
```
##2. pushImagePickerController

打开相册
```html
pushImagePickerController(callback(ret))
ret：
类型：JSON对象
内部字段：
{
    status: true   //布尔型；true
    base64:String  //逗号分隔的base64图片字符串
}

```
####示例代码
```javascript 
demo.pushImagePickerController(function(ret){


            document.getElementById('image').src='data:image/jpeg;base64,'+ ret.base64.split(",")[0]


        });
```
