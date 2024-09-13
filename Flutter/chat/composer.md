---
layout: post
title: Composer in Flutter Chat widget | Syncfusion
description: Learn here all about Composer feature of Syncfusion Flutter Chat (SfChat) widget, including its properties and more.
platform: flutter
control: SfChat
documentation: ug
---

# Composer in Flutter Chat (SfChat)
This section explains how to integrate and customize the composer in the SfChat widget and how to use a custom composer with the composerBuilder.

## Default Composer
By default, the chat widget provides a basic composer that includes a text input field for users to type their messages. The composer is customizable with several properties to meet the design and functionality requirements of your chat application.

### TextStyle
The [`textStyle`] property is used to customize the appearance of the text in the message input field, including color, font size, and style.

### Lines
The [`minLines`] property is used to set the minimum number of lines that the message input field should display, determining its initial height.
The [`maxLines`] property is used to define the maximum number of lines the message input field can expand to before becoming scrollable.

### Decoration
The [`decoration`] property is used to customize the visual attributes of the message input field, such as hint text,borders, and internal padding, using an InputDecoration object.

### Padding
The [`padding`] property is used to adjust the space around the input field, controlling its distance from the parent widget.

{% tabs %}
{% highlight Dart %}

List<ChatMessage> _messages = <ChatMessage>[]; // Load if there are existing messages.

@override
Widget build(BuildContext context) {
  return SfChat(
    messages: _messages,
    outgoingUser: currentUser.id,
    composer: ChatComposer(
      textStyle: TextStyle(fontSize: 16.0, color: Colors.black),
      minLines: 1,
      maxLines: 6,
      decoration: InputDecoration(
        hintText: 'Type a message',
      ),
      padding: const EdgeInsets.only(top: 16.0),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Chat composer support](images/composer/default-composer.png)

## Custom Composer using composer.builder
The composer.builder property in the SfChat widget allows for advanced customization of the chat input area. By using this property, you can create a custom composer widget tailored to your specific design and functionality needs.

### Builder
The [`builder`] property lets you specify a custom widget, like CustomChatInputWidget, for the chat composer. This customizes how the message input area looks and works.

### Padding
The [`padding`] property is used to adjust the space around the input field, controlling its distance from the parent widget.

{% tabs %}
{% highlight Dart %}

List<ChatMessage> _messages = <ChatMessage>[]; // Load if there are existing messages.

@override
Widget build(BuildContext context) {
  return SfChat(
    messages: _messages,
    outgoingUser: currentUser.id,
    composer: ChatComposer.builder(
      builder: (context) => CustomChatInputWidget(),
      padding: const EdgeInsets.only(top: 16.0),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Chat composer support](images/composer/composer-builder.png)