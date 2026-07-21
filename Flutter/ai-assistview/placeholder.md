---
layout: post
title: Placeholder in Flutter AI AssistView widget | Syncfusion
description: Learn here all about Placeholder feature of Syncfusion Flutter AI AssistView (SfAIAssistView) widget, including its properties and more.
platform: flutter
control: SfAIAssistView
documentation: ug
---

# Placeholder in Flutter AI AssistView (SfAIAssistView)

Define a custom [`placeholder`](https://pub.dev/documentation/syncfusion_flutter_chat/latest/assist_view/SfAIAssistView/placeholderBuilder.html) widget to display when there are no messages in the AI AssistView. You can use the [`placeholderBehavior`](https://pub.dev/documentation/syncfusion_flutter_chat/latest/assist_view/SfAIAssistView/placeholderBehavior.html) property to control whether the placeholder is hidden when a message is added or scrolls along with the messages. By default, `placeholderBehavior` is set to [`AssistPlaceholderBehavior.hideOnMessage`](https://pub.dev/documentation/syncfusion_flutter_chat/latest/assist_view/AssistPlaceholderBehavior.html).

## Hide on message

Configure the placeholder to become visible when there are no messages in the AI AssistView and to be hidden when a new message is added.

{% tabs %}
{% highlight dart hl_lines="111" %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_chat/assist_view.dart';

class HideOnMessageExample extends StatefulWidget {
  @override
  State<HideOnMessageExample> createState() => _HideOnMessageExampleState();
}

class _HideOnMessageExampleState extends State<HideOnMessageExample> {
  final List<AssistMessage> _messages = <AssistMessage>[];

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
              _generativeResponse(data);
            });
          },
        ),
        placeholderBuilder: (BuildContext context) {
          return Center(
            child: Column(
              mainAxisSize: MainAxisSize.min,
              children: [
                const Text(
                  'What can I help you with today?',
                ),
                const SizedBox(height: 25),
                Row(
                  mainAxisAlignment: MainAxisAlignment.center,
                  children: [
                    DecoratedBox(
                      decoration: BoxDecoration(
                        border: Border.all(
                          color: Colors.black,
                          width: 1.5,
                        ),
                        borderRadius: BorderRadius.circular(10),
                      ),
                      child: const Padding(
                        padding: EdgeInsets.all(10.0),
                        child: Text(
                          'Travel Tips',
                        ),
                      ),
                    ),
                    const SizedBox(width: 10),
                    DecoratedBox(
                      decoration: BoxDecoration(
                        border: Border.all(
                          color: Colors.black,
                          width: 1.5,
                        ),
                        borderRadius: BorderRadius.circular(10),
                      ),
                      child: const Padding(
                        padding: EdgeInsets.all(10.0),
                        child: Text(
                          'Recipe Ideas',
                        ),
                      ),
                    ),
                    const SizedBox(width: 10),
                    DecoratedBox(
                      decoration: BoxDecoration(
                        border: Border.all(
                          color: Colors.black,
                          width: 1.5,
                        ),
                        borderRadius: BorderRadius.circular(10),
                      ),
                      child: const Padding(
                        padding: EdgeInsets.all(10.0),
                        child: Text(
                          'Fun Fact',
                        ),
                      ),
                    ),
                    const SizedBox(width: 10),
                    DecoratedBox(
                      decoration: BoxDecoration(
                        border: Border.all(
                          color: Colors.black,
                          width: 1.5,
                        ),
                        borderRadius: BorderRadius.circular(10),
                      ),
                      child: const Padding(
                        padding: EdgeInsets.all(10.0),
                        child: Text(
                          'Life Hacks',
                        ),
                      ),
                    ),
                  ],
                ),
              ],
            ),
          );
        },
        placeholderBehavior: AssistPlaceholderBehavior.hideOnMessage,
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

![AIAssistView placeholder support](images/placeholder/placeholder-hideOnMessage.gif)

## Scroll with message

The placeholder can [`scroll`](https://pub.dev/documentation/syncfusion_flutter_chat/latest/assist_view/AssistPlaceholderBehavior.html#scrollWithMessage) along with messages. This behavior is identical to the previous sample, with the [`placeholderBehavior`](https://pub.dev/documentation/syncfusion_flutter_chat/latest/assist_view/SfAIAssistView/placeholderBehavior.html) set to [`AssistPlaceholderBehavior.scrollWithMessage`](https://pub.dev/documentation/syncfusion_flutter_chat/latest/assist_view/AssistPlaceholderBehavior.html).

{% tabs %}
{% highlight dart hl_lines="3" %}

  // Replace the placeholderBehavior value in the previous sample to
  // make the placeholder scroll along with messages.
  placeholderBehavior: AssistPlaceholderBehavior.scrollWithMessage,
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

![AIAssistView placeholder support](images/placeholder/placeholder-scrollWithMessage.gif)

>You can refer to our [Flutter AI AssistView](https://www.syncfusion.com/flutter-widgets/flutter-aiassistview) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter AI AssistView example](https://flutter.syncfusion.com/#/ai-assist-view/getting-started) which demonstrates interaction between users and AI services in a fully customizable layout and shows how to easily configure the AI AssistView with built-in support for creating stunning visual effects.