---
layout: post
title: Placeholder in Flutter AI AssistView widget | Syncfusion
description: Learn here all about Placeholder feature of Syncfusion Flutter AI AssistView (SfAIAssistView) widget, including its properties and more.
platform: flutter
control: SfAIAssistView
documentation: ug
---

# Placeholder in Flutter AI AssistView (SfAIAssistView)

Define a custom placeholder widget to display at the top of all messages, serving as a header, or to be shown when there are no messages in the chat.

## Hide on message

Configure the placeholder to become visible when there are no messages in the AI AssistView and to be hidden when a new message is added.

{% tabs %}
{% highlight Dart %}

  late List<AssistMessage> _messages;

  void _generativeResponse(String data) async {
    final String response = await _getAIResponse(data);
    setState(() {
      _messages.add(AssistMessage.response(data: response));
    });
  }

  Future<String> _getAIResponse(String data) async {
    String response = '';
    // Connect with your preferred AI to generate a response to the request.
    return response;
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfAIAssistView(
        messages: _messages,
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(data: data));
            });
            _generativeResponse(data);
          },
        ),
        placeholderBuilder: (BuildContext context) {
          return const Center(
            child: Text(
              'Ask AI Anything!',
              style: TextStyle(
                  fontSize: 18,
                  color: Colors.black54,
                  fontWeight: FontWeight.bold),
            ),
          );
        },
        placeholderBehavior: AssistPlaceholderBehavior.hideOnMessage,
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Scroll with message

The placeholder can scroll along with messages.

{% tabs %}
{% highlight Dart %}

  late List<AssistMessage> _messages;

  void _generativeResponse(String data) async {
    final String response = await _getAIResponse(data);
    setState(() {
      _messages.add(AssistMessage.response(data: response));
    });
  }

  Future<String> _getAIResponse(String data) async {
    String response = '';
    // Connect with your preferred AI to generate a response to the request.
    return response;
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfAIAssistView(
        messages: _messages,
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(data: data));
            });
            _generativeResponse(data);
          },
        ),
        placeholderBuilder: (BuildContext context) {
          return const Center(
            child: Text(
              'Ask AI Anything!',
              style: TextStyle(
                  fontSize: 18,
                  color: Colors.black54,
                  fontWeight: FontWeight.bold),
            ),
          );
        },
        placeholderBehavior: AssistPlaceholderBehavior.scrollWithMessage,
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

>You can refer to our [`Flutter Chat`](https://www.syncfusion.com/flutter-widgets/flutter-chat) feature tour page for its groundbreaking feature representations. You can also explore our [`Flutter Chat example`](https://flutter.syncfusion.com/#/chat/getting-started) which demonstrates conversations between two or more users in a fully customizable layout and shows how to easily configure the chat with built-in support for creating stunning visual effects.