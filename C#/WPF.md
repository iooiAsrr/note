###### WPF控件可以分类

- Control:基本控件。文本框、按钮等。
- Shape: 创建简单的图形控件，椭圆、线条、矩形等
- Panel: - 有助于对齐和定位控件。 例如，grid 帮助我们以表格方式对齐，stack panel 有助于水平 和垂直对齐。 

###### 什么是MVVM模式？请简要解释MVVM模式的结构和各 个部分的职责

- Model： 负责管理数据的获取、存储、验证。不直接与视图进行交互，而是由ViewModel来访问和操作。 
- View： 在屏幕上呈现数据和接收用户输入。 
- ViewModel：负责处理视图逻辑、数据转换和UI交互。 ViewModel包含了视图所需的数据以及与数据相关的操作，通常实现了命令、属性绑定等功能。

###### 4.WPF 中的资源是什么？

一次设置多个控件的属性。单个资源能在多个元素上设置背景属性。 

###### 什么是资源字典

- 存储共享资源。样式、控件模板、数据模板等

######  5.什么是静态资源和动态资源？ 

- 静态资源值在加载时确定，动态资源运行时更改属性值的情况下使用

**xmlns**代表 XML 命名空间。 它帮助我们避免 XML 文档中的名称冲突和混淆

###### 什么是数据模板（DataTemplate）？ 

-  数据模板在资源字典中定义，用 `DataTemplate` 标签，定义如何在 UI 中显示数据，增强可视化和可定制。

###### 什么是控件模板

- 定义控件外观和行为的 XAML 结构

- 可以通过 `Template` 属性将模板应用到控件

- **TargetType**：指定要应用模板的控件类型。

  **ContentPresenter**：用于呈现控件的内容。

###### XML 元素由开始标签和结束标签包围。用于数据交换、配置文件、文档

```xml
<note>
    <to>Tove</to>
    <from>Jani</from>
</note>
```

