---
layout: post
title: Conversation Area in Flutter AI AssistView widget | Syncfusion
description: Learn here all about Messages and its details of Syncfusion Flutter AI AssistView (SfAIAssistView) widget and more.
platform: flutter
control: SfAIAssistView
documentation: ug
---

# Conversation area in Flutter AI AssistView (SfAIAssistView)

This section explains the customization options available for modifying the request and response messages in the assist widget.

## Conversation area

The AI AssistView displays the content of user requests and AI responses. Each message includes details like the message's text, sending time stamp, and author. The response message contains additional information, including suggestions and toolbar items.

{% tabs %}
{% highlight dart %}

{% endhighlight %}
{% endtabs %}

### Request message

Customize the content of request messages by changing the background color, background shape, and other features based on the message, index, or specific conditions.

{% tabs %}
{% highlight dart %}

{% endhighlight %}
{% endtabs %}

### Response message

Customize the content of response messages by changing the background color, background shape, and other features based on the message, index, or specific conditions.

{% tabs %}
{% highlight dart %}

{% endhighlight %}
{% endtabs %}

### Header

The header displays the username of the message's author along with the time stamp of when the message was sent. Additionally, you can build a custom widget to display more information about messages.

{% tabs %}
{% highlight dart %}

{% endhighlight %}
{% endtabs %}

### Footer

Showcases additional functionalities and information, including feedback options, AI model details, and more.

{% tabs %}
{% highlight dart %}

{% endhighlight %}
{% endtabs %}

### Avatar

The message author's avatar displays either an image or the initials of their name. By default, if the avatar image source is not defined, the user's initials will be displayed. Additionally, you can create a custom widget that shows more information about the user.

{% tabs %}
{% highlight dart %}

{% endhighlight %}
{% endtabs %}

### Content area

Customize the area where message content is displayed by changing its background color, shape, and functionalities based on the user or other specific conditions.

{% tabs %}
{% highlight dart %}

{% endhighlight %}
{% endtabs %}

### Suggestions

Provide a list response suggestions. When the user selects one, it is considered a new request message. The suggestions' layout, background, colors, and more can be customized.

{% tabs %}
{% highlight dart %}

{% endhighlight %}
{% endtabs %}

### Loading indicator

Indicates that the AI service's response is in progress after a request has been submitted. By default, the indicator is a shimmer effect that is displayed until the response is received.

{% tabs %}
{% highlight dart %}

{% endhighlight %}
{% endtabs %}

### Toolbar items

Append a toolbar to response messages that provides options to perform various actions, such as rating the response, sharing it, copying it, and more.

{% tabs %}
{% highlight dart %}

{% endhighlight %}
{% endtabs %}

>You can refer to our [Flutter Chat](https://www.syncfusion.com/flutter-widgets/flutter-chat) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter Chat example](https://flutter.syncfusion.com/#/chat/getting-started) which demonstrates conversations between two or more users in a fully customizable layout and shows how to easily configure the chat with built-in support for creating stunning visual effects.

#### See Also

* You can also customize the bubble shapes and colors properties of both [`requestBubbleSettings`] and [`responseBubbleSettings`] using [`SfAIAssistViewTheme`] by wrapping with [`SfAIAssistView`].