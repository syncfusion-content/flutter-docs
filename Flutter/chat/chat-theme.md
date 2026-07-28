---
layout: post
title: Theme in Flutter Chat widget | Syncfusion
description: Step-by-step guide to customize themes in Syncfusion Flutter Chat (SfChat)—colors, text styles, and component styling.
platform: flutter
control: SfChatTheme
documentation: ug
---

# Theme in Flutter Chat (SfChatTheme)

This section explains the customization properties available in [`SfChatThemeData`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData-class.html).

## Add dependencies

To use chat theming, add both chat and core packages in `pubspec.yaml`.

{% tabs %}
{% highlight yaml %}

dependencies:
  syncfusion_flutter_chat: ^x.x.x
  syncfusion_flutter_core: ^x.x.x

{% endhighlight %}
{% endtabs %}

## Import libraries

Import the required libraries for chat and theme support.

{% tabs %}
{% highlight dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_chat/chat.dart';
import 'package:syncfusion_flutter_core/theme.dart';

{% endhighlight %}
{% endtabs %}

## Basic themed chat

Wrap [`SfChat`](https://pub.dev/documentation/syncfusion_flutter_chat/latest/chat/SfChat-class.html) with [`SfChatTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatTheme-class.html) and set [`SfChatThemeData`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData-class.html) values.

{% tabs %}
{% highlight dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_chat/chat.dart';
import 'package:syncfusion_flutter_core/theme.dart';

void main() {
  runApp(const BasicThemeExample());
}

class BasicThemeExample extends StatelessWidget {
  const BasicThemeExample({super.key});

  @override
  Widget build(BuildContext context) {
    final List<ChatMessage> messages = <ChatMessage>[
      ChatMessage(
        text: 'Hi!',
        time: DateTime(2024, 08, 07, 9, 0),
        author: const ChatAuthor(id: '123-001', name: 'John Doe'),
      ),
      ChatMessage(
        text: 'Hello! How’s it going?',
        time: DateTime(2024, 08, 07, 9, 5),
        author: const ChatAuthor(id: '123-002', name: 'Jane Smith'),
      ),
    ];

    return MaterialApp(
      home: SfChatTheme(
        data: const SfChatThemeData(
          actionButtonForegroundColor: Colors.white,
          actionButtonBackgroundColor: Colors.blueAccent,
        ),
        child: Scaffold(
          body: SfChat(
            messages: messages,
            outgoingUser: '123-001',
          ),
        ),
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

## Action button theme properties

The following properties customize the default action button:

* [`actionButtonForegroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonForegroundColor.html)
* [`actionButtonBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonBackgroundColor.html)
* [`actionButtonFocusColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonFocusColor.html)
* [`actionButtonHoverColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonHoverColor.html)
* [`actionButtonSplashColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonSplashColor.html)
* [`actionButtonDisabledForegroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonDisabledForegroundColor.html)
* [`actionButtonDisabledBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonDisabledBackgroundColor.html)
* [`actionButtonElevation`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonElevation.html)
* [`actionButtonFocusElevation`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonFocusElevation.html)
* [`actionButtonHoverElevation`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonHoverElevation.html)
* [`actionButtonHighlightElevation`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonHighlightElevation.html)
* [`actionButtonDisabledElevation`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonDisabledElevation.html)
* [`actionButtonMouseCursor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonMouseCursor.html)
* [`actionButtonShape`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonShape.html)

{% tabs %}
{% highlight dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_chat/chat.dart';
import 'package:syncfusion_flutter_core/theme.dart';

void main() {
  runApp(const ActionButtonThemeExample());
}

class ActionButtonThemeExample extends StatelessWidget {
  const ActionButtonThemeExample({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: SfChatTheme(
        data: SfChatThemeData(
          actionButtonForegroundColor: Colors.white,
          actionButtonBackgroundColor: Colors.blue,
          actionButtonFocusColor: Colors.blue.withValues(alpha: 0.86),
          actionButtonHoverColor: Colors.blue.withValues(alpha: 0.91),
          actionButtonSplashColor: Colors.white.withValues(alpha: 0.3),
          actionButtonDisabledForegroundColor: Colors.grey.shade600,
          actionButtonDisabledBackgroundColor: Colors.grey.shade300,
          actionButtonElevation: 2,
          actionButtonFocusElevation: 6,
          actionButtonHoverElevation: 4,
          actionButtonHighlightElevation: 8,
          actionButtonDisabledElevation: 0,
          actionButtonMouseCursor: SystemMouseCursors.click,
          actionButtonShape: RoundedRectangleBorder(
            borderRadius: BorderRadius.circular(40),
          ),
        ),
        child: Scaffold(
          body: SfChat(
            messages: const <ChatMessage>[],
            outgoingUser: '123-001',
          ),
        ),
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

## Avatar and message colors

Use the following properties to style avatar backgrounds and message backgrounds:

* [`outgoingAvatarBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/outgoingAvatarBackgroundColor.html)
* [`incomingAvatarBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/incomingAvatarBackgroundColor.html)
* [`outgoingMessageBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/outgoingMessageBackgroundColor.html)
* [`incomingMessageBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/incomingMessageBackgroundColor.html)

{% tabs %}
{% highlight dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_chat/chat.dart';
import 'package:syncfusion_flutter_core/theme.dart';

void main() {
  runApp(const MessageColorThemeExample());
}

class MessageColorThemeExample extends StatelessWidget {
  const MessageColorThemeExample({super.key});

  @override
  Widget build(BuildContext context) {
    final List<ChatMessage> messages = <ChatMessage>[
      ChatMessage(
        text: 'Theme sample',
        time: DateTime(2024, 08, 07, 9, 0),
        author: const ChatAuthor(id: '123-001', name: 'John Doe'),
      ),
      ChatMessage(
        text: 'Looks good',
        time: DateTime(2024, 08, 07, 9, 2),
        author: const ChatAuthor(id: '123-002', name: 'Jane Smith'),
      ),
    ];

    return MaterialApp(
      home: SfChatTheme(
        data: SfChatThemeData(
          outgoingAvatarBackgroundColor: Colors.green.shade200,
          incomingAvatarBackgroundColor: Colors.blue.shade200,
          outgoingMessageBackgroundColor: Colors.green.shade100,
          incomingMessageBackgroundColor: Colors.blue.shade100,
        ),
        child: Scaffold(
          body: SfChat(
            messages: messages,
            outgoingUser: '123-001',
          ),
        ),
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

## Text styles

Use the following properties to style editor, message content, and headers:

* [`editorTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/editorTextStyle.html)
* [`outgoingContentTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/outgoingContentTextStyle.html)
* [`incomingContentTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/incomingContentTextStyle.html)
* [`outgoingPrimaryHeaderTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/outgoingPrimaryHeaderTextStyle.html)
* [`incomingPrimaryHeaderTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/incomingPrimaryHeaderTextStyle.html)
* [`outgoingSecondaryHeaderTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/outgoingSecondaryHeaderTextStyle.html)
* [`incomingSecondaryHeaderTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/incomingSecondaryHeaderTextStyle.html)

{% tabs %}
{% highlight dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_chat/chat.dart';
import 'package:syncfusion_flutter_core/theme.dart';

void main() {
  runApp(const TextStyleThemeExample());
}

class TextStyleThemeExample extends StatelessWidget {
  const TextStyleThemeExample({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: SfChatTheme(
        data: const SfChatThemeData(
          editorTextStyle: TextStyle(
            color: Colors.black,
            fontSize: 16,
            fontWeight: FontWeight.normal,
          ),
          outgoingContentTextStyle: TextStyle(
            color: Colors.black87,
            fontSize: 14,
            fontWeight: FontWeight.bold,
          ),
          incomingContentTextStyle: TextStyle(
            color: Colors.black,
            fontSize: 14,
            fontWeight: FontWeight.bold,
          ),
          outgoingPrimaryHeaderTextStyle: TextStyle(
            color: Colors.black,
            fontSize: 12,
            fontWeight: FontWeight.bold,
          ),
          incomingPrimaryHeaderTextStyle: TextStyle(
            color: Colors.black,
            fontSize: 12,
            fontWeight: FontWeight.bold,
          ),
          outgoingSecondaryHeaderTextStyle: TextStyle(
            color: Colors.grey,
            fontSize: 12,
            fontStyle: FontStyle.italic,
          ),
          incomingSecondaryHeaderTextStyle: TextStyle(
            color: Colors.grey,
            fontSize: 12,
            fontStyle: FontStyle.normal,
          ),
        ),
        child: Scaffold(
          body: SfChat(
            messages: const <ChatMessage>[],
            outgoingUser: '123-001',
          ),
        ),
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

## Outgoing message shape

Use [`outgoingMessageShape`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/outgoingMessageShape.html) to customize outgoing bubble shape.

## Incoming message shape

Use [`incomingMessageShape`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/incomingMessageShape.html) to customize incoming bubble shape.

{% tabs %}
{% highlight dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_chat/chat.dart';
import 'package:syncfusion_flutter_core/theme.dart';

void main() {
  runApp(const MessageShapeThemeExample());
}

class MessageShapeThemeExample extends StatelessWidget {
  const MessageShapeThemeExample({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: SfChatTheme(
        data: SfChatThemeData(
          outgoingMessageShape: RoundedRectangleBorder(
            borderRadius: BorderRadius.circular(16),
          ),
          incomingMessageShape: RoundedRectangleBorder(
            borderRadius: BorderRadius.circular(16),
          ),
        ),
        child: Scaffold(
          body: SfChat(
            messages: const <ChatMessage>[],
            outgoingUser: '123-001',
          ),
        ),
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

## Suggestion styling

Use these properties to customize suggestion backgrounds, shapes, and item text styles:

* [`suggestionBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/suggestionBackgroundColor.html)
* [`suggestionBackgroundShape`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/suggestionBackgroundShape.html)
* [`suggestionItemBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/suggestionItemBackgroundColor.html)
* [`suggestionItemShape`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/suggestionItemShape.html)
* [`suggestionItemTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/suggestionItemTextStyle.html)

{% tabs %}
{% highlight dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_chat/chat.dart';
import 'package:syncfusion_flutter_core/theme.dart';

void main() {
  runApp(const SuggestionThemeExample());
}

class SuggestionThemeExample extends StatelessWidget {
  const SuggestionThemeExample({super.key});

  @override
  Widget build(BuildContext context) {
    final List<ChatMessage> messages = <ChatMessage>[
      ChatMessage(
        text: 'How are you?',
        time: DateTime(2024, 08, 07, 9, 0),
        author: const ChatAuthor(id: '123-002', name: 'Jane Smith'),
        suggestions: const <ChatMessageSuggestion>[
          ChatMessageSuggestion(data: 'Doing well!'),
          ChatMessageSuggestion(data: 'All good!'),
        ],
      ),
    ];

    return MaterialApp(
      home: SfChatTheme(
        data: SfChatThemeData(
          suggestionBackgroundColor: Colors.lightBlue.shade50,
          suggestionBackgroundShape: RoundedRectangleBorder(
            borderRadius: BorderRadius.circular(8),
          ),
          suggestionItemBackgroundColor: WidgetStateProperty.resolveWith(
            (Set<WidgetState> states) {
              if (states.contains(WidgetState.selected)) {
                return Colors.blue;
              }
              if (states.contains(WidgetState.focused)) {
                return Colors.blueGrey;
              }
              if (states.contains(WidgetState.hovered)) {
                return Colors.lightBlueAccent;
              }
              if (states.contains(WidgetState.disabled)) {
                return Colors.grey.shade300;
              }
              return Colors.white;
            },
          ),
          suggestionItemShape: WidgetStateProperty.resolveWith(
            (Set<WidgetState> states) {
              if (states.contains(WidgetState.selected)) {
                return RoundedRectangleBorder(
                  borderRadius: BorderRadius.circular(12),
                );
              }
              if (states.contains(WidgetState.focused)) {
                return RoundedRectangleBorder(
                  borderRadius: BorderRadius.circular(8),
                );
              }
              if (states.contains(WidgetState.hovered)) {
                return RoundedRectangleBorder(
                  borderRadius: BorderRadius.circular(6),
                );
              }
              if (states.contains(WidgetState.disabled)) {
                return RoundedRectangleBorder(
                  borderRadius: BorderRadius.circular(4),
                );
              }
              return RoundedRectangleBorder(
                borderRadius: BorderRadius.circular(8),
              );
            },
          ),
          suggestionItemTextStyle: WidgetStateProperty.resolveWith(
            (Set<WidgetState> states) {
              if (states.contains(WidgetState.selected)) {
                return const TextStyle(
                  color: Colors.blue,
                  fontSize: 16,
                  fontWeight: FontWeight.bold,
                );
              }
              if (states.contains(WidgetState.focused)) {
                return const TextStyle(
                  color: Colors.blueGrey,
                  fontSize: 16,
                  fontWeight: FontWeight.bold,
                );
              }
              if (states.contains(WidgetState.hovered)) {
                return const TextStyle(
                  color: Colors.lightBlueAccent,
                  fontSize: 16,
                  fontWeight: FontWeight.bold,
                );
              }
              if (states.contains(WidgetState.disabled)) {
                return const TextStyle(
                  color: Colors.grey,
                  fontSize: 16,
                  fontWeight: FontWeight.bold,
                );
              }
              return const TextStyle(
                color: Colors.black,
                fontSize: 16,
                fontWeight: FontWeight.bold,
              );
            },
          ),
        ),
        child: Scaffold(
          body: SfChat(
            messages: messages,
            outgoingUser: '123-001',
          ),
        ),
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

>You can refer to our [Flutter Chat](https://www.syncfusion.com/flutter-widgets/flutter-chat) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter Chat example](https://flutter.syncfusion.com/#/chat/getting-started) which demonstrates conversations between two or more users in a fully customizable layout and shows how to easily configure the chat with built-in support for creating stunning visual effects.