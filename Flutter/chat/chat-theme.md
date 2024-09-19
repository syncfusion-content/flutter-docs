---
layout: post
title: Theme in Flutter Chat widget | Syncfusion
description: Learn here all about the Theme feature of Syncfusion Flutter Chat (SfChatTheme) widget and how it enhances user interaction and customization.
platform: flutter
control: SfChatTheme
documentation: ug
---

# Theme in Flutter Chat (SfChatTheme)

This section explains the customization properties available in [`SfChatThemeData`].

**Import the Chat library** 

Import the following library to use the chat theme data:

{% tabs %}
{% highlight dart %}

    import 'package:syncfusion_flutter_core/theme.dart';

{% endhighlight %}
{% endtabs %}

## Action Button Foreground Color

The [`actionButtonForegroundColor`] property is used to specify the color for the default action button icon.

{% tabs %}
{% highlight Dart %}

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

## Action Button Background Color

The [`actionButtonBackgroundColor`] property is used to specify the background color for the action button in its default state.

{% tabs %}
{% highlight Dart %}

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

## Action Button Focus Color

The [`actionButtonFocusColor`] property is used to specify the background color for the action button when it is in the focused state.

{% tabs %}
{% highlight Dart %}

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

## Action Button Hover Color

The [`actionButtonHoverColor`] property is used to specify the background color for the action button when it is hovered over.

{% tabs %}
{% highlight Dart %}

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

## Action Button Splash Color

The [`actionButtonSplashColor`] property is used to specify the color of the ripple effect when the action button is tapped.

{% tabs %}
{% highlight Dart %}

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

## Action Button Disabled Foreground Color

The [`actionButtonDisabledForegroundColor`] property is used to specify the color of the text or icon on the action button when it is disabled.

{% tabs %}
{% highlight Dart %}

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

## Action Button Disabled Background Color

The [`actionButtonDisabledBackgroundColor`] property is used to specify the background color of the action button when it is disabled.

{% tabs %}
{% highlight Dart %}

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

## Action Button Elevation

The [`actionButtonElevation`] property is used to specify the elevation of the action button in its default state.

{% tabs %}
{% highlight Dart %}

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

## Action Button Focus Elevation

The [`actionButtonFocusElevation`] property is used to specify the elevation of the action button when it is focused.

{% tabs %}
{% highlight Dart %}

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

## Action Button Hover Elevation

The [`actionButtonHoverElevation`] property is used to specify the elevation of the action button when it is hovered over.

{% tabs %}
{% highlight Dart %}

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

## Action Button Highlight Elevation

The [`actionButtonHighlightElevation`] property is used to specify the elevation of the action button when it is highlighted.

{% tabs %}
{% highlight Dart %}

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

## Action Button Disabled Elevation

The [`actionButtonDisabledElevation`] property is used to specify the elevation of the action button when it is disabled.

{% tabs %}
{% highlight Dart %}

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

## Action Button Mouse Cursor

The [`actionButtonMouseCursor`] property is used to specify the type of cursor displayed when hovering over the action button.

{% tabs %}
{% highlight Dart %}

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

## Action Button Shape

The [`actionButtonShape`] property is used to specify the shape and border radius of the action button.

{% tabs %}
{% highlight Dart %}

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

## Outgoing Bubble Content Background Color

The [`outgoingBubbleContentBackgroundColor`] property is used to specify the background color of bubbles containing outgoing messages.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        outgoingBubbleContentBackgroundColor: Colors.green[100],
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

## Incoming Bubble Content Background Color

The [`incomingBubbleContentBackgroundColor`] property is used to specify the background color of bubbles containing incoming messages.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        incomingBubbleContentBackgroundColor: Colors.blue[100],
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

## Editor Text Style

The [`editorTextStyle`] property is used to specify the style for text in the message editor.

{% tabs %}
{% highlight Dart %}

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

## Outgoing Content Text Style

The [`outgoingContentTextStyle`] property is used to specify the style for text in outgoing message bubbles.

{% tabs %}
{% highlight Dart %}

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

## Incoming Content Text Style

The [`incomingContentTextStyle`] property is used to specify the style for text in incoming message bubbles

{% tabs %}
{% highlight Dart %}

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

## Outgoing Primary Header Text Style

The [`outgoingPrimaryHeaderTextStyle`] property is used to specify the style for the primary header text in outgoing message bubbles.

{% tabs %}
{% highlight Dart %}

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

## Incoming Primary Header Text Style

The [`incomingPrimaryHeaderTextStyle`] property is used to specify the style for the primary header text in incoming message bubbles.

{% tabs %}
{% highlight Dart %}

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

## Outgoing Secondary Header Text Style

The [`outgoingSecondaryHeaderTextStyle`] property is used to specify the style for the secondary header text in outgoing message bubbles.

{% tabs %}
{% highlight Dart %}

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

## Incoming Secondary Header Text Style

The [`incomingSecondaryHeaderTextStyle`] property is used to specify the style for the secondary header text in incoming message bubbles.

{% tabs %}
{% highlight Dart %}

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

## Outgoing Bubble Content Shape

The [`outgoingBubbleContentShape`] property is used to specify the shape and border radius of outgoing message bubbles.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        outgoingBubbleContentShape: RoundedRectangleBorder(
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

## Incoming Bubble Content Shape

The [`incomingBubbleContentShape`] property is used to specify the shape and border radius of incoming message bubbles.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<ChatMessage> _messages = <ChatMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfChatTheme(
      data: const SfChatThemeData(
        incomingBubbleContentShape: RoundedRectangleBorder(
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

>You can refer to our [Flutter Chat](https://www.syncfusion.com/flutter-widgets/flutter-chat) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter Chat example](https://flutter.syncfusion.com/#/chat/getting-started) which demonstrates conversations between two or more users in a fully customizable layout and shows how to easily configure the chat with built-in support for creating stunning visual effects.