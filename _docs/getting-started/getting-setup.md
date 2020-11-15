---
title: Getting Setup
category: Getting Started
order: 1
---

Using TinYard is super simple - especially when only wanting its IoC capabilities.

To get up and running with TinYard all you need is a [`Context`](#Context):

```c#
Context context = new Context();

context.Mapper.Map<IExampleInterface>().ToValue<ExampleImplementation>();
```

With the snippet above setup, you can [`Inject`](#Inject-Attribute) the `ExampleImplementation` into another class by asking for the `IExampleInterface` in the class like so:

```c#
public class InjectableExample
{
    [Inject]
    public IExampleInterface implementation;

    //..
}
```
Now, to get this `InjectableExample` provided with the value, we have two options:

1. Map `InjectableExample` on the `context.Mapper`
2. Call `Inject` on the `context.Injector`

Often, you'll find you end up doing option 1 without thinking about it as it can be handy to `Map` many objects.. but sometimes, you really will not want to do that!

This is where option 2 can come in. The `context.Injector` handles all `injections`, so simply call `context.Inject(injectableExampleInstance)` and voila!

A lot of the above is performed for you in the [`MVC Bundle`](#MVC-Bundle) extensions, making it a great tool for more complex use. To learn a bit more about this, take a look at [extensions](#TinYard-Extensions).