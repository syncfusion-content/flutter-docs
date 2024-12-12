---
layout: post
title: Theme in Flutter AssistView widget | Syncfusion
description: Learn here all about Theme feature of Syncfusion Flutter AI AssistView (SfAIAssistViewTheme) widget and how it enhances user interaction and customization.
platform: flutter
control: SfAIAssistViewTheme
documentation: ug
---

# Theme in Flutter AssistView (SfAIAssistViewTheme)

This section explains the customization properties available in [`AssistThemeData`].

**Import the Chat library** 

Import the following library to use the assist theme data:

{% tabs %}
{% highlight dart %}

    import 'package:syncfusion_flutter_core/theme.dart';

{% endhighlight %}
{% endtabs %}

## Action button foreground color

The [`actionButtonForegroundColor`] property is used to specify the color for the default action button icon.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        actionButtonForegroundColor: Colors.white,
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button background color

The [`actionButtonBackgroundColor`] property is used to specify the background color for the action button in its default state.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        actionButtonBackgroundColor: Colors.blueAccent,
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button focus color

The [`actionButtonFocusColor`] property is used to specify the background color for the action button when it is in the focused state.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        actionButtonFocusColor: Colors.blue,
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button hover color

The [`actionButtonHoverColor`] property is used to specify the background color for the action button when it is hovered over.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        actionButtonHoverColor: Colors.blueGrey,
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button splash color

The [`actionButtonSplashColor`] property is used to specify the color of the ripple effect when the action button is tapped.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        actionButtonSplashColor: Colors.lightBlueAccent,
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button disabled foreground color

The [`actionButtonDisabledForegroundColor`] property is used to specify the color of the text or icon on the action button when it is disabled.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        actionButtonDisabledForegroundColor: Colors.grey,
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button disabled background color

The [`actionButtonDisabledBackgroundColor`] property is used to specify the background color of the action button when it is disabled.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        actionButtonDisabledBackgroundColor: Colors.grey[300],
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button elevation

The [`actionButtonElevation`] property is used to specify the elevation of the action button in its default state.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        actionButtonElevation: 4.0,
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button focus elevation

The [`actionButtonFocusElevation`] property is used to specify the elevation of the action button when it is focused.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        actionButtonFocusElevation: 6.0,
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button hover elevation

The [`actionButtonHoverElevation`] property is used to specify the elevation of the action button when it is hovered over.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        actionButtonHoverElevation: 8.0,
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button highlight elevation

The [`actionButtonHighlightElevation`] property is used to specify the elevation of the action button when it is highlighted.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        actionButtonHighlightElevation: 12.0,
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button disabled elevation

The [`actionButtonDisabledElevation`] property is used to specify the elevation of the action button when it is disabled.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        actionButtonDisabledElevation: 0.0,
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button mouse cursor

The [`actionButtonMouseCursor`] property is used to specify the type of cursor displayed when hovering over the action button.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        actionButtonMouseCursor: SystemMouseCursors.click,
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Action button shape

The [`actionButtonShape`] property is used to specify the shape and border radius of the action button.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        actionButtonShape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(40.0),
        ),
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Request avatar background color

The [`requestAvatarBackgroundColor`] property is used to specify the background color of request message avatar.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        requestAvatarBackgroundColor: Colors.green[200],
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Response avatar background color

The [`responseAvatarBackgroundColor`] property is used to specify the background color of response message avatar.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        responseAvatarBackgroundColor: Colors.blue[200],
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Request bubble content background color

The [`requestBubbleContentBackgroundColor`] property is used to specify the background color of bubbles containing request messages.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        requestBubbleContentBackgroundColor: Colors.green[100],
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Response bubble content background color

The [`responseBubbleContentBackgroundColor`] property is used to specify the background color of bubbles containing response messages.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        responseBubbleContentBackgroundColor: Colors.blue[100],
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Editor text style

The [`editorTextStyle`] property is used to specify the style for text in the message editor.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        editorTextStyle: const TextStyle(
          color: Colors.black,
          fontSize: 16.0,
          fontWeight: FontWeight.normal,
        ),
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Request content text style

The [`requestContentTextStyle`] property is used to specify the style for text in request message bubbles.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        requestContentTextStyle: const TextStyle(
          color: Colors.black87,
          fontSize: 14.0,
          fontWeight: FontWeight.bold,
        ),
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Response content text style

The [`responseContentTextStyle`] property is used to specify the style for text in response message bubbles

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        responseContentTextStyle: const TextStyle(
          color: Colors.black,
          fontSize: 14.0,
          fontWeight: FontWeight.bold,
        ),
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Request primary header text style

The [`requestPrimaryHeaderTextStyle`] property is used to specify the style for the primary header text in request message bubbles.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        requestPrimaryHeaderTextStyle: const TextStyle(
          color: Colors.black,
          fontSize: 12.0,
          fontWeight: FontWeight.bold,
        ),
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Response primary header text style

The [`responsePrimaryHeaderTextStyle`] property is used to specify the style for the primary header text in response message bubbles.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        responsePrimaryHeaderTextStyle: const TextStyle(
          color: Colors.black,
          fontSize: 12.0,
          fontWeight: FontWeight.bold,
        ),
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Request secondary header text style

The [`requestSecondaryHeaderTextStyle`] property is used to specify the style for the secondary header text in request message bubbles.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        requestSecondaryHeaderTextStyle: const TextStyle(
          color: Colors.grey,
          fontSize: 12.0,
          fontStyle: FontStyle.italic,
        ),
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Response secondary header text style

The [`responseSecondaryHeaderTextStyle`] property is used to specify the style for the secondary header text in response message bubbles.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        responseSecondaryHeaderTextStyle: const TextStyle(
          color: Colors.grey,
          fontSize: 12.0,
          fontStyle: FontStyle.normal,
        ),
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Suggestion item text style

The [`suggestionItemTextStyle`] property is used to specify the text style for response message suggestion items.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
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
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Request bubble content shape

The [`requestBubbleContentShape`] property is used to specify the shape and border radius of request message bubbles.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        requestBubbleContentShape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(16.0),
        ),
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Response bubble content shape

The [`responseBubbleContentShape`] property is used to specify the shape and border radius of response message bubbles.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        responseBubbleContentShape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(16.0),
        ),
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Suggestion background color

The [`suggestionBackgroundColor`] property is used to specify the background color of response message suggestion bubble.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        suggestionBackgroundColor: Colors.lightBlue[50],
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Suggestion background shape

The [`suggestionBackgroundShape`] property is used to specify the background shape of response message suggestion bubble.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        suggestionBackgroundShape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(8.0),
        ),
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Suggestion item background color

The [`suggestionItemBackgroundColor`] property is used to specify the background color for response message suggestion items.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
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
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Suggestion item shape

The [`suggestionItemShape`] property is used to specify the shape for response message suggestion items.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
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
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Response toolbar background color

The [`responseToolbarBackgroundColor`] property is used to specify the background color of response message toolbar bubble.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        responseToolbarBackgroundColor: Colors.red,
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Response toolbar background shape

The [`responseToolbarBackgroundShape`] property is used to specify the background shape of response message toolbar bubble.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        responseToolbarBackgroundShape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(8.0),
        ),
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Response toolbar item background color

The [`responseToolbarItemBackgroundColor`] property is used to specify the background color of response message toolbar items.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        responseToolbarItemBackgroundColor:
            WidgetStateProperty.resolveWith(
          (Set<WidgetState> state) {
            if (state.contains(WidgetState.selected)) {
              return Colors.blue;
            } else if (state.contains(WidgetState.focused)) {
              return Colors.blueGrey;
            } else if (state.contains(WidgetState.hovered)) {
              return Colors.lightBlueAccent;
            } else if (state.contains(WidgetState.disabled)) {
              return Colors.grey[400];
            }
            return Colors.white;
          },
        ),
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Response toolbar item shape

The [`responseToolbarItemShape`] property is used to specify the shape of response message toolbar items.

{% tabs %}
{% highlight Dart %}

  // Load if there are existing messages.
  final List<AssistMessage> _messages = <AssistMessage>[];

  @override
  Widget build(BuildContext context) {
    return SfAIAssistViewTheme(
      data: const SfAIAssistViewThemeData(
        responseToolbarItemShape: WidgetStateProperty.resolveWith(
          (Set<WidgetState> state) {
            if (state.contains(WidgetState.selected)) {
              return RoundedRectangleBorder(
                borderRadius: BorderRadius.circular(16.0),
              );
            } else if (state.contains(WidgetState.focused)) {
              return RoundedRectangleBorder(
                borderRadius: BorderRadius.circular(12.0),
              );
            } else if (state.contains(WidgetState.hovered)) {
              return RoundedRectangleBorder(
                borderRadius: BorderRadius.circular(8.0),
              );
            } else if (state.contains(WidgetState.disabled)) {
              return RoundedRectangleBorder(
                borderRadius: BorderRadius.circular(4.0),
              );
            }
            return RoundedRectangleBorder(
              borderRadius: BorderRadius.circular(10.0),
            );
          },
        ),
      ),
      child: Scaffold(
        body: SfAIAssistView(
          messages: _messages,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

>You can refer to our [`Flutter AI AssistView`](https://www.syncfusion.com/flutter-widgets/flutter-chat) feature tour page for its groundbreaking feature representations. You can also explore our [`Flutter AI AssistView example`](https://flutter.syncfusion.com/#/chat/getting-started) which demonstrates conversations between two or more users in a fully customizable layout and shows how to easily configure the assist view with built-in support for creating stunning visual effects.