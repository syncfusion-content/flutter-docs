---
layout: post
title: Composer in Flutter Chat widget | Syncfusion
description: Learn here all about Composer feature of Syncfusion Flutter Chat (SfChat) widget, including its properties and more.
platform: flutter
control: SfChat
documentation: ug
---

# Composer in Flutter Chat (SfChat)

This section explains how to integrate and customize the composer in the Chat widget and how to use a custom composer with the composerBuilder.

## Composer

The composer property in the chat widget can be customized using the [`ChatComposer`] widget. This widget allows you to define various aspects of the chat input area, such as text style, input field dimensions, and decoration. By default, the chat widget provides a basic composer that includes a text input field for users to type their messages.

### TextStyle

* The [`textStyle`] property is used to customize the appearance of the text in the message input field, including color, font size, and style.

{% tabs %}
{% highlight dart %}

// Load if there are existing messages.
List<ChatMessage> _messages = <ChatMessage>[];
final String _outgoingUserId = '';

@override
Widget build(BuildContext context) {
  return SfChat(
    messages: _messages,
    outgoingUser: _outgoingUserId,
    composer: ChatComposer(
      textStyle: TextStyle(fontSize: 16.0, color: Colors.black),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

### Lines

* The [`minLines`] property is used to set the minimum number of lines that the message input field should display, determining its initial height.
* The [`maxLines`] property is used to define the maximum number of lines the message input field can expand to before becoming scrollable.

{% tabs %}
{% highlight dart %}

// Load if there are existing messages.
List<ChatMessage> _messages = <ChatMessage>[];
final String _outgoingUserId = '';

@override
Widget build(BuildContext context) {
  return SfChat(
    messages: _messages,
    outgoingUser: _outgoingUserId,
    composer: ChatComposer(
      minLines: 1,
      maxLines: 6,
    ),
  );
}

{% endhighlight %}
{% endtabs %}

### Decoration

* The [`decoration`] property is used to customize the visual attributes of the message input field, such as hint text,borders, and internal padding, using an InputDecoration object.

{% tabs %}
{% highlight dart %}

// Load if there are existing messages.
List<ChatMessage> _messages = <ChatMessage>[];
final String _outgoingUserId = '';

@override
Widget build(BuildContext context) {
  return SfChat(
    messages: _messages,
    outgoingUser: _outgoingUserId,
    composer: ChatComposer(
      decoration: InputDecoration(
        hintText: 'Type a message',
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

### Padding

* The [`padding`] property is used to adjust the space around the input field, controlling its distance from the parent widget.

{% tabs %}
{% highlight dart %}

// Load if there are existing messages.
List<ChatMessage> _messages = <ChatMessage>[];
final String _outgoingUserId = '';

@override
Widget build(BuildContext context) {
  return SfChat(
    messages: _messages,
    outgoingUser: _outgoingUserId,
    composer: ChatComposer(
      padding: const EdgeInsets.only(top: 16.0),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Chat composer support](images/composer/default-composer.png)

## Custom Composer

The composer property in the chat widget can be customized using [`ChatComposer.builder`]. This property enables advanced customization of the chat input area, allowing you to create a custom composer widget tailored to your specific design and functional requirements.

When implementing a custom composer through the `builder` property, the padding around the input field is automatically adjusted to fit your custom design. By default, the padding is set to ensure appropriate spacing between the input area and its parent widget. This padding can be fine-tuned as needed within your custom widget to achieve the desired look and feel.

### Builder

* The [`builder`] property lets you specify a custom widget, like CustomChatInputWidget, for the chat composer. This customizes how the message input area looks and works.

{% tabs %}
{% highlight dart %}

// Load if there are existing messages.
List<ChatMessage> _messages = <ChatMessage>[];
final String _outgoingUserId = '';

@override
Widget build(BuildContext context) {
  return SfChat(
    messages: _messages,
    outgoingUser: _outgoingUserId,
    composer: ChatComposer.builder(
      builder: (context) {
        return TextField(
          decoration: InputDecoration(
            hintText: 'Type a message...',
            border: OutlineInputBorder(),
          ),
        );
      },
      padding: const EdgeInsets.only(top: 16.0),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Chat composer support](images/composer/composer-builder.png)