# Yii2 CKEditor

This is a fork [MihailDev/yii2-ckeditor](https://github.com/MihailDev/yii2-ckeditor)

#### Features:
- The ability to add custom plugins
- Initialisation editor on event
- Added custom plugins 

Plugins:
- [Line Utilities](http://ckeditor.com/addon/lineutils)
- [Widget](http://ckeditor.com/addon/widget)
- [oembed](http://ckeditor.com/addon/oembed)
- Custom video (MP4, WebM)
- [Enhanced Image](http://ckeditor.com/addon/image2)

### Composer

The preferred way to install this extension is through [Composer](http://getcomposer.org/).

Either run ```php composer.phar require sadovojav/yii2-ckeditor "dev-master"```

or add ```"sadovojav/yii2-ckeditor": "dev-master"``` to the require section of your ```composer.json```

### Use

- Widget

```php
use sadovojav\ckeditor\CKEditor;

echo CKEditor::widget();
```

- ActiveForm

```php
use sadovojav\ckeditor\CKEditor;

echo $form->field($post, 'text_full')->widget(CKEditor::className());
```

#### Parameters
- array `editorOptions` - CKeditor options
- array `containerOptions` - Container options
- array `extraPlugins` - Extra plugins connection
- string `initOnEvent ` =  `false` - Event type for initialization

##### Example

```php
echo $form->field($post, 'text_full')->widget(CKEditor::className(), [
    'extraPlugins' => [
        ['test', '@root/uploads/plugins/test-plugin/', 'plugin.js']
    ],
    'editorOptions' => [
        'toolbar' => [
            ['Source', 'NewPage', 'Preview', 'Viewss'],
            ['PasteText', '-', 'Undo', 'Redo'],
            ['Replace', 'SelectAll', 'Scayt'],
            ['Format', 'FontSize'],
            ['Bold', 'Italic', 'Underline', 'TextColor', 'StrikeThrough', '-', 'Outdent', 'Indent', 'RemoveFormat',
                'Blockquote', 'HorizontalRule'],
            ['NumberedList', 'BulletedList', '-', 'JustifyLeft', 'JustifyCenter', 'JustifyRight',
                'JustifyBlock'],
            ['Image', 'oembed', 'Video', 'Iframe'],
            ['Link', 'Unlink'],
            ['Maximize', 'ShowBlocks'],
            ['test']
        ],
        'allowedContent' => true,
        'forcePasteAsPlainText' => true,
        'extraPlugins' => 'test,image2,widget,oembed,video',
        'language' => Yii::$app->language,
        'height' => 500
    ],
]);
```

#### Initialisation editor on event
```
'initOnEvent' => 'focus' //dblclick, mouseover, etc.
```

#### Use extra plugins

1. Add extra plugin connection information
```
'extraPlugins' => [
    ['test', '@root/uploads/plugins/test-plugin/', 'plugin.js']
],
```

- `test` required - plugin name
- `@root/uploads/plugins/test-plugin/` required - path to plugin
- `plugin.js` required - plugin script file
  
2. Add extra plugin to editorOptions -> extraPlugins
```
'extraPlugins' => 'test,image2,oembed,widget,video',
```
Without space after comma.

3. If your plugin use the button, add it on the panel
```
'toolbar' => [
    ['test'],
],
```

### Links

- Mouse event - https://api.jquery.com/category/events/mouse-events/
- CKEditor Api - http://docs.ckeditor.com/
- File manager ElFinder - https://github.com/MihailDev/yii2-elfinder
