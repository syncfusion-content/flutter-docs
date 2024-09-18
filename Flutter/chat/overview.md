---
layout: post
title: About Flutter Chat widget | Syncfusion 
description: Learn here all about the introduction of Syncfusion Flutter Chat (SfChat) widget, its features, and more.
platform: flutter
control: SfChat
documentation: ug
---

# Flutter Chat (SfChat) Overview

The Syncfusion Flutter Chat widget displays conversations between two or more users and offers a wide range of customization options, including the composer, action button, and message bubbles (header, footer, content, and avatar).

![Chat overview](images/overview/chat-overview.gif)

## Features

* **Placeholder** - The [`placeholderBuilder`] can be used to create a custom widget that appears when conversations are empty. This feature is especially useful for displaying a relevant or visually appealing message, indicating that the conversation currently has no messages.

* **Composer** - The primary text editor where new chat messages can be composed. You can also integrate custom composer widgets.

* **Action Button** - Represents the send button. Pressing this action button invokes the [`onPressed`] callback with the text entered in the default [`ChatComposer`].

* **Message Bubble** -  A list of [`ChatMessage`] objects that will be displayed in the chat interface as either incoming or outgoing messages based on the [`outgoingUser`]. Each [`ChatMessage`] includes details such as the message text, timestamp, and author information.

* **Bubble Header** - Displays the sender's name and the timestamp associated with each message. Using the [`bubbleHeaderBuilder`], a custom widget can be specified to display as a header for each chat bubble with required details about the respective message.

* **Bubble Footer** - By default, no footer is added to the message bubble. Using the [`bubbleFooterBuilder`], a custom widget can be specified to display as a footer for each chat bubble with required details about the respective message.

* **Bubble Content** - The actual message content. Using the [`bubbleContentBuilder`], a custom widget can be specified to display as the content for each chat message with a customized layout.

* **Bubble Avatar** - Displays user avatars or profile pictures of the respective message. Using the [`bubbleAvatarBuilder`], a custom widget can be specified to display the chat message avatar with relevant details.

>**Note**: You can refer to our [Flutter Chat](https://www.syncfusion.com/flutter-widgets/flutter-chat) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter Chat example](https://flutter.syncfusion.com/#/chat) which demonstrates conversations between two or more users in a fully customizable layout and shows how to easily configure the chat with built-in support for creating stunning visual effects.

#### See Also

* [Integrating syncfusion flutter chat in a flutter web application](https://support.syncfusion.com/kb/article/9941/how-to-integrate-syncfusion-chat-in-flutter).