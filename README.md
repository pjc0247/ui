# ui
Unity Interface<br>

HTML/JS style ui coding for Unity.

Overview
----
<img align="left" src="sample.jpg">

```html
<body>
  <div class"header"> 
    <img class="thumbnail" src="thumbnail.jpg" />
    <div>
      <text class="title">SuperMania2</text>
      <text class="developer">Junchul Park</text>
      <button class="install-btn">INSTALL</button>
    </div>
  </div>
  
  <div class="dev-specs">
    <img src="csharp.jpg />
    <img src="unity.jpg />
    <img src="android.jpg /> 
  </div>
  
  <scroll class="previews">
     <img src="1.jpg" />
     <img src="2.jpg" />
     <img src="3.jpg" />
  </scroll>
</body>
```
```css
#title {
  font-size: 50;
}

img {
  width: 100;
  height: 100;
}
```

Custom Elements
----
```cs
[UtmlElementName("ctext")]
class CustomText : UtmlElement {

  // This is a utml constructor.
  public static void Construct(GameObject go, UtmlConstructionData cd) {
    var text = go.AddComponent<Text>();
    text.text = cd.innerText;
    
    if (cd.HasAttribute("bold"))
      text.style = TextStyle.Bold;
  }
}
```
```html
<ctext bold>Hello World!</ctext>
```

Inline Style
----
```html
<utml>
  <vertical>
    <text>Hello</text>
    <text>World</text>
  </vertical>
  
  <style>
    text {
      color: red;
    }
  </style>
</html>
```

Bindings
----
