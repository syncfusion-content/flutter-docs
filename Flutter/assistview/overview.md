---
layout: post
title: About Flutter AssistView widget | Syncfusion 
description: Learn here all about the introduction of Syncfusion Flutter AssistView (SfAIAssistView) widget, its features, and more.
platform: flutter
control: SfAIAssistView
documentation: ug
---

# Flutter AssistView (SfAIAssistView) Overview

The Syncfusion Flutter AssistView widget displays conversations between users and AI, offering a wide range of customization options, including the composer, action button, message bubbles (with customizable header, footer, content, and avatar), response loading, message suggestion, bubble alignment, and toolbar actions.

## Features

* **Placeholder** - The [`placeholderBuilder`] can be used to create a custom widget that appears when conversations are empty. This feature is especially useful for displaying a relevant or visually appealing message, indicating that the conversation currently has no messages.

* **Composer** - The primary text editor where new request messages can be composed. You can also integrate custom composer widgets.

* **Action Button** - Represents the send button. Pressing this action button invokes the [`onPressed`] callback with the text entered in the default [`AssistComposer`].

* **Message Bubble** -  A list of [`AssistMessage`] objects that will be displayed in the chat interface as either a request message from the user or a response message from AI. Each [`AssistMessage`] includes details such as the message text, timestamp, and author information.

* **Bubble Header** - Displays the sender's name and the timestamp associated with each message. Using the [`bubbleHeaderBuilder`], a custom widget can be specified to display as a header for each chat bubble with required details about the respective message.

* **Bubble Footer** - By default, no footer is added to the message bubble. Using the [`bubbleFooterBuilder`], a custom widget can be specified to display as a footer for each chat bubble with required details about the respective message.

* **Bubble Content** - The actual message content. Using the [`bubbleContentBuilder`], a custom widget can be specified to display as the content for each chat message with a customized layout.

* **Bubble Avatar** - Displays user avatars or profile pictures of the respective message. Using the [`bubbleAvatarBuilder`], a custom widget can be specified to display the chat message avatar with relevant details.

>You can refer to our [Flutter Chat](https://www.syncfusion.com/flutter-widgets/flutter-chat) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter Chat example](https://flutter.syncfusion.com/#/chat/getting-started) which demonstrates conversations between two or more users in a fully customizable layout and shows how to easily configure the chat with built-in support for creating stunning visual effects.