Concept
====

You may noticed that Unity's hierarchy system is very simillar to HTML's.

Goals
----
* Easy to learn, especially for HTML skilled programmers.
* Zero-overhead (No runtime execution, but still supports runtime API if you need.)
* Supports IL2CPP

Data binding
----
```HTML
<Text>{{message}}</Text>
```
```cs
class HelloWorldContext : Context { 
    public string message = "Hello World";

    void OnClick() {
        // This automatically chanes the content.
        message = "Bye World";
    }
}
```

__Collections__
```HTML
<Vertical>
    <Text for="message in messages">{{message}}</Text>
</Vertical>
```
```cs
class HelloWorldContext : Context { 
    public string[] messages = new string[] {
        "Apple",
        "Banana",
        "Amazon"
    };
}
```

__Two way binding__
```HTML
<Text>Input your name: </Text>
<Input model="nickname" />
```
```cs
class RegistrationContext : Context {
    public string nickname;

    public void OnClickNext() {
        // This will be automatically filled with UI value.
        Register(nickname);
    }
}
```

Customizable elements
----
```HTML
<Vertical>
    <RankingItem for="user in topUsers"></RankingItem>
</Vertical>
```
```cs
[UtmlElementName("RankingItem")]
class RankingItemElement : UtmlElement {

  // This is a utml constructor.
  public static void Construct(GameObject go, UtmlConstructionData cd) {
    var text = go.AddComponent<Text>();
    text.text = cd.innerText;
  }
}
```
