---
layout: post
title: Placeholder in Flutter Chat widget | Syncfusion
description: Learn here all about Placeholder feature of Syncfusion Flutter Chat (SfChat) widget, including its properties and more.
platform: flutter
control: SfChat
documentation: ug
---

# Placeholder in Flutter Chat (SfChat)

By default, the chat widget does not display any content when there are no messages. To provide a custom message or visual indication in place of an empty chat, you can use the [`placeholderBuilder`] property.  This property allows you to specify a custom widget that will be displayed when the list of chat messages is empty.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];
  final String _outgoingUserId = '';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfChat(
        messages: _messages,
        outgoingUser: _outgoingUserId,
        placeholderBuilder: (BuildContext context) {
          return const Center(
            child: Text(
              'No messages yet!',
              style: TextStyle(fontSize: 16, color: Colors.black),
            ),
          );
        },
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

![Chat composer support](images/placeholder/placeholder-chat.png)