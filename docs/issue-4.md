### antd表单默认值无法动态更新问题：

解决方法：
Form.create({
  mapPropsToFields(props){
  }//添加mapPropsToFields
})(PositionEditorForm)

原因：虽然数据已经在render中动态更新了，但是表单的默认值并没有改变，可以打印下this.props.form.getFieldValue({key:value}) 对比下，默认值并没有随着动态更新

1.如果没有initValue的情况下，直接使用resetFields可以清空文本框的值

2.如果是有initValue的情况下，直接使用resetFields方法会直接重置为initValue的值

归根结底：是因为设置initValue的时候，直接设置了input的value的默认值。

原因在此：

    w3c网站有这样的描述(http://www.w3school.com.cn/htmldom/dom_obj_reset.asp)
"在 HTML 表单中 <input type="reset"> 标签每出现一次，一个Reset对象就会被创建。当重置按钮被点击，包含它的表单中所有输入元素的值都重置为它们的默认值。默认值由 HTML value 属性或 JavaScript 的 defaultValue 属性指定。"

    意思就是如果这个textarea如果设置了value属性的值，那么reset按钮就会恢复textarea到这个value属性的值，而不是空。

结论如下：

    reset并不是清空输入框的值，而是将输入框的值恢复到value属性所指定的值。

源自：https://www.cnblogs.com/jcxfighting/p/10517406.html