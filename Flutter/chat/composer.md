---
layout: post
title: Composer in Flutter Chat widget | Syncfusion
description: Learn here all about Composer feature of Syncfusion Flutter Chat (SfChat) widget, including its properties and more.
platform: flutter
control: SfChat
documentation: ug
---

# Composer in Flutter Chat (SfChat)

This section explains how to integrate and customize the composer in the Chat widget.

## Composer

The [`composer`] property in the chat widget defines the chat input area where users can type and send messages. By default, this property uses the [`ChatComposer`] widget, which provides a standard text input field for message entry. The default [`ChatComposer`] offers a basic setup but can be customized with properties such as [`minLines`], [`maxLines`], [`padding`], [`decorations`], and [`textStyle`] to adjust the appearance and functionality of the text input field according to your needs.

### TextStyle

* The [`textStyle`] property customizes the appearance of the text in the message input field, including color, font size, and style.

{% tabs %}
{% highlight dart %}

// Load if there are existing messages.
final List<ChatMessage> _messages = <ChatMessage>[];
final String _outgoingUserId = '';

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfChat(
      messages: _messages,
      outgoingUser: _outgoingUserId,
      composer: const ChatComposer(
        textStyle: TextStyle(fontSize: 16.0, color: Colors.black),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

### Lines

* The [`minLines`] property sets the minimum number of lines that the message input field should display, determining its initial height.
* The [`maxLines`] property defines the maximum number of lines the message input field can expand to before becoming scrollable.

{% tabs %}
{% highlight dart %}

// Load if there are existing messages.
final List<ChatMessage> _messages = <ChatMessage>[];
final String _outgoingUserId = '';

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfChat(
      messages: _messages,
      outgoingUser: _outgoingUserId,
      composer: const ChatComposer(
        minLines: 1,
        maxLines: 6,
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

### Decoration

* The [`decoration`] property customizes the visual attributes of the message input field, such as hint text,borders, and internal padding, using an InputDecoration object.

{% tabs %}
{% highlight dart %}

// Load if there are existing messages.
final List<ChatMessage> _messages = <ChatMessage>[];
final String _outgoingUserId = '';

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfChat(
      messages: _messages,
      outgoingUser: _outgoingUserId,
      composer: const ChatComposer(
        decoration: InputDecoration(
          hintText: 'Type a message',
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

### Padding

* The [`padding`] property adjusts the space around the input field, controlling its distance from the parent widget.

{% tabs %}
{% highlight dart %}

// Load if there are existing messages.
final List<ChatMessage> _messages = <ChatMessage>[];
final String _outgoingUserId = '';

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfChat(
      messages: _messages,
      outgoingUser: _outgoingUserId,
      composer: const ChatComposer(
        padding: EdgeInsets.only(top: 16.0),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Chat composer support](images/composer/default-composer.png)

## Custom Composer

The [`composer`] property in the chat widget can be customized using [`ChatComposer.builder`]. This approach provides advanced customization options for the chat input area, allowing you to create a fully tailored composer widget that meets your specific design and functional requirements. With [`ChatComposer.builder`], you can define the structure and appearance of the input area beyond the default settings, giving you complete control over the chat input experience.

When implementing a custom composer through the [`builder`] property, the padding around the input field is automatically adjusted to fit your custom design. By default, the [`padding`] is set to ensure appropriate spacing between the input area and its parent widget.

### Builder

* The [`builder`] property allows you to specify a custom widget for the chat composer. This lets you customize both the appearance and functionality of the message input area. In the provided example, a TextField widget is used directly to define the chat input area.

{% tabs %}
{% highlight dart %}

// Load if there are existing messages.
final List<ChatMessage> _messages = <ChatMessage>[];
final String _outgoingUserId = '';

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfChat(
      messages: _messages,
      outgoingUser: _outgoingUserId,
      composer: ChatComposer.builder(
        builder: (context) {
          return const TextField(
            decoration: InputDecoration(
              hintText: 'Type a message...',
              border: OutlineInputBorder(),
            ),
          );
        },
        padding: const EdgeInsets.only(top: 16.0),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Chat composer support](images/composer/composer-builder.png)