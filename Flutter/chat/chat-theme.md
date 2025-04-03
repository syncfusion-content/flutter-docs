---
layout: post
title: Theme in Flutter Chat widget | Syncfusion
description: Learn here all about the Theme feature of Syncfusion Flutter Chat (SfChatTheme) widget and how it enhances user interaction and customization.
platform: flutter
control: SfChatTheme
documentation: ug
---

# Theme in Flutter Chat (SfChatTheme)

This section explains the customization properties available in [`ChatThemeData`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfThemeData/chatThemeData.html).

**Import the Chat library** 

Import the following library to use the chat theme data:

{% tabs %}
{% highlight dart %}

    import 'package:syncfusion_flutter_core/theme.dart';

{% endhighlight %}
{% endtabs %}

## Action button foreground color

The [`actionButtonForegroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonForegroundColor.html) property is used to specify the color for the default action button icon.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        actionButtonForegroundColor: Colors.white,
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button background color

The [`actionButtonBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonBackgroundColor.html) property is used to specify the background color for the action button in its default state.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        actionButtonBackgroundColor: Colors.blueAccent,
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button focus color

The [`actionButtonFocusColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonFocusColor.html) property is used to specify the background color for the action button when it is in the focused state.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        actionButtonFocusColor: Colors.blue,
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button hover color

The [`actionButtonHoverColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonHoverColor.html) property is used to specify the background color for the action button when it is hovered over.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        actionButtonHoverColor: Colors.blueGrey,
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button splash color

The [`actionButtonSplashColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonSplashColor.html) property is used to specify the color of the ripple effect when the action button is tapped.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        actionButtonSplashColor: Colors.lightBlueAccent,
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button disabled foreground color

The [`actionButtonDisabledForegroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonDisabledForegroundColor.html) property is used to specify the color of the text or icon on the action button when it is disabled.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        actionButtonDisabledForegroundColor: Colors.grey,
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button disabled background color

The [`actionButtonDisabledBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonDisabledBackgroundColor.html) property is used to specify the background color of the action button when it is disabled.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        actionButtonDisabledBackgroundColor: Colors.grey[300],
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button elevation

The [`actionButtonElevation`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonElevation.html) property is used to specify the elevation of the action button in its default state.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        actionButtonElevation: 4.0,
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button focus elevation

The [`actionButtonFocusElevation`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonFocusElevation.html) property is used to specify the elevation of the action button when it is focused.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        actionButtonFocusElevation: 6.0,
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button hover elevation

The [`actionButtonHoverElevation`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonHoverElevation.html) property is used to specify the elevation of the action button when it is hovered over.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        actionButtonHoverElevation: 8.0,
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button highlight elevation

The [`actionButtonHighlightElevation`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonHighlightElevation.html) property is used to specify the elevation of the action button when it is highlighted.

{% tabs %}
{% highlight Darthl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        actionButtonHighlightElevation: 12.0,
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button disabled elevation

The [`actionButtonDisabledElevation`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonDisabledElevation.html) property is used to specify the elevation of the action button when it is disabled.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        actionButtonDisabledElevation: 0.0,
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button mouse cursor

The [`actionButtonMouseCursor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonMouseCursor.html) property is used to specify the type of cursor displayed when hovering over the action button.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        actionButtonMouseCursor: SystemMouseCursors.click,
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button shape

The [`actionButtonShape`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/actionButtonShape.html) property is used to specify the shape and border radius of the action button.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        actionButtonShape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(40.0),
        ),
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Outgoing avatar background color

The [`outgoingAvatarBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/outgoingAvatarBackgroundColor.html) property is used to specify the background color of outgoing message avatar.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        outgoingAvatarBackgroundColor: Colors.green[200],
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Incoming avatar background color

The [`incomingAvatarBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/incomingAvatarBackgroundColor.html) property is used to specify the background color of incoming message avatar.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        incomingAvatarBackgroundColor: Colors.blue[200],
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Outgoing message background color

The [`outgoingMessageBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/outgoingMessageBackgroundColor.html) property is used to specify the background color of bubbles containing outgoing messages.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        outgoingMessageBackgroundColor: Colors.green[100],
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Incoming message background color

The [`incomingMessageBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/incomingMessageBackgroundColor.html) property is used to specify the background color of bubbles containing incoming messages.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        incomingMessageBackgroundColor: Colors.blue[100],
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Editor text style

The [`editorTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/editorTextStyle.html) property is used to specify the style for text in the message editor.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        editorTextStyle: const TextStyle(
          color: Colors.black,
          fontSize: 16.0,
          fontWeight: FontWeight.normal,
        ),
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Outgoing content text style

The [`outgoingContentTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/outgoingContentTextStyle.html) property is used to specify the style for text in outgoing message bubbles.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        outgoingContentTextStyle: const TextStyle(
          color: Colors.black87,
          fontSize: 14.0,
          fontWeight: FontWeight.bold,
        ),
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Incoming content text style

The [`incomingContentTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/incomingContentTextStyle.html) property is used to specify the style for text in incoming message bubbles

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        incomingContentTextStyle: const TextStyle(
          color: Colors.black,
          fontSize: 14.0,
          fontWeight: FontWeight.bold,
        ),
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Outgoing primary header text style

The [`outgoingPrimaryHeaderTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/outgoingPrimaryHeaderTextStyle.html) property is used to specify the style for the primary header text in outgoing message bubbles.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        outgoingPrimaryHeaderTextStyle: const TextStyle(
          color: Colors.black,
          fontSize: 12.0,
          fontWeight: FontWeight.bold,
        ),
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Incoming primary header text style

The [`incomingPrimaryHeaderTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/incomingPrimaryHeaderTextStyle.html) property is used to specify the style for the primary header text in incoming message bubbles.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        incomingPrimaryHeaderTextStyle: const TextStyle(
          color: Colors.black,
          fontSize: 12.0,
          fontWeight: FontWeight.bold,
        ),
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Outgoing secondary header text style

The [`outgoingSecondaryHeaderTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/outgoingSecondaryHeaderTextStyle.html) property is used to specify the style for the secondary header text in outgoing message bubbles.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        outgoingSecondaryHeaderTextStyle: const TextStyle(
          color: Colors.grey,
          fontSize: 12.0,
          fontStyle: FontStyle.italic,
        ),
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Incoming secondary header text style

The [`incomingSecondaryHeaderTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/incomingSecondaryHeaderTextStyle.html) property is used to specify the style for the secondary header text in incoming message bubbles.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        incomingSecondaryHeaderTextStyle: const TextStyle(
          color: Colors.grey,
          fontSize: 12.0,
          fontStyle: FontStyle.normal,
        ),
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Suggestion item text style

The [`suggestionItemTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/suggestionItemTextStyle.html) property is used to specify the text style for both outgoing and incoming message suggestion items.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        suggestionItemTextStyle: WidgetStateProperty.resolveWith(
          (Set<WidgetState> state) {
            if (state.contains(WidgetState.selected)) {
              return const TextStyle(
                  color: Colors.blue,
                  fontSize: 16.0,
                  fontWeight: FontWeight.bold);
            } else if (state.contains(WidgetState.focused)) {
              return const TextStyle(
                  color: Colors.blueGrey,
                  fontSize: 16.0,
                  fontWeight: FontWeight.bold);
            } else if (state.contains(WidgetState.hovered)) {
              return const TextStyle(
                  color: Colors.lightBlueAccent,
                  fontSize: 16.0,
                  fontWeight: FontWeight.bold);
            } else if (state.contains(WidgetState.disabled)) {
              return const TextStyle(
                  color: Colors.grey,
                  fontSize: 16.0,
                  fontWeight: FontWeight.bold);
            }
            return const TextStyle(
                color: Colors.black,
                fontSize: 16.0,
                fontWeight: FontWeight.bold);
          },
        ),
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Outgoing message shape

The [`outgoingMessageShape`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/outgoingMessageShape.html) property is used to specify the shape and border radius of outgoing message bubbles.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        outgoingMessageContentShape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(16.0),
        ),
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Incoming message shape

The [`incomingMessageShape`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/incomingMessageShape.html) property is used to specify the shape and border radius of incoming message content.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        incomingMessageContentShape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(16.0),
        ),
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
          outgoingUser: '123-001',
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Suggestion background color

The [`suggestionBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/suggestionBackgroundColor.html) property is used to specify the background color of both outgoing and incoming message suggestion bubble.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        suggestionBackgroundColor: Colors.lightBlue[50],
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Suggestion background shape

The [`suggestionBackgroundShape`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/suggestionBackgroundShape.html) property is used to specify the background shape of both outgoing and incoming message suggestion bubble.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        suggestionBackgroundShape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(8.0),
        ),
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Suggestion item background color

The [`suggestionItemBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/suggestionItemBackgroundColor.html) property is used to specify the background color for both outgoing and incoming message suggestion items.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        suggestionItemBackgroundColor: WidgetStateProperty.resolveWith(
          (Set<WidgetState> state) {
            if (state.contains(WidgetState.selected)) {
              return Colors.blue;
            } else if (state.contains(WidgetState.focused)) {
              return Colors.blueGrey;
            } else if (state.contains(WidgetState.hovered)) {
              return Colors.lightBlueAccent;
            } else if (state.contains(WidgetState.disabled)) {
              return Colors.grey[300];
            }
            return Colors.white;
          },
        ),
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Suggestion item shape

The [`suggestionItemShape`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChatThemeData/suggestionItemShape.html) property is used to specify the shape for both outgoing and incoming message suggestion items.

{% tabs %}
{% highlight Dart hl_lines="8" %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        suggestionItemShape: WidgetStateProperty.resolveWith(
          (Set<WidgetState> state) {
            if (state.contains(WidgetState.selected)) {
              return RoundedRectangleBorder(
                borderRadius: BorderRadius.circular(12.0),
              );
            } else if (state.contains(WidgetState.focused)) {
              return RoundedRectangleBorder(
                borderRadius: BorderRadius.circular(8.0),
              );
            } else if (state.contains(WidgetState.hovered)) {
              return RoundedRectangleBorder(
                borderRadius: BorderRadius.circular(6.0),
              );
            } else if (state.contains(WidgetState.disabled)) {
              return RoundedRectangleBorder(
                borderRadius: BorderRadius.circular(4.0),
              );
            }
            return RoundedRectangleBorder(
              borderRadius: BorderRadius.circular(8.0),
            );
          },
        ),
      ),
      child: Scaffold(
        body: SfChat(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

>You can refer to our [Flutter Chat](https://www.syncfusion.com/flutter-widgets/flutter-chat) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter Chat example](https://flutter.syncfusion.com/#/chat/getting-started) which demonstrates conversations between two or more users in a fully customizable layout and shows how to easily configure the chat with built-in support for creating stunning visual effects.