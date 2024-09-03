---
layout: post
title: About Flutter Chat widget | Syncfusion 
description: Learn here all about the introduction of Syncfusion Flutter Chat (SfChat) widget, its features, and more.
platform: Flutter
control: SfChat
documentation: ug
---

# Flutter Slider (SfChat) Overview

The Syncfusion Flutter Chat widget displays conversations between two or more users in a fully customizable layout. It presents messages in a chat user interface and allows you to customize various aspects such as message composition, action buttons, and bubble appearance.

![Chat overview](images/overview/chat-overview.png)

## Features

* **Message and user support** - Provides functionalities for displaying [`message`] text, timestamps, and author information, with customization options for user profiles support for distinguishing between incoming and outgoing messages using [`isOutgoingUser`].

* **Composer** - The [`composer`] property lets you add a message entry field to the chat interface. This widget includes a customizable text input area for users to compose and send new messages.You can use a predefined widget or provide a custom builder for complete flexibility in the message input field's presentation and styling.

* **Action Button** - Represents a customizable [`actionButton`] for sending new messages in the chat conversation.

* **Place Holders** - You can use the [`placeholderBuilder`] to create a custom widget that appears when the conversation is idle. This is particularly handy for presenting users with a relevant or visually appealing message indicating that the conversation is currently empty.

* **Header Builder** - The [`bubbleHeaderBuilder`] allows you to specify a custom widget that will be shown as a header within each chat bubble. This is particularly useful for displaying additional information such as the sender's name and timestamp associated with each message.

* **Avatar Builder** - The [`bubbleAvatarBuilder`] allows you to specify a custom widget that will be shown as an avatar within each chat bubble.
This is particularly useful for displaying user avatars or profile pictures in the chat interface.

* **Content Builder** - The [`bubbleContentBuilder`] allows you to specify a custom widget to display as the content within each chat bubble. This is useful for customizing how the message content is presented, such as using different background colors, borders, or padding.

* **Footer Builder** - The [`bubbleFooterBuilder`] allows you to specify a custom widget that will be shown as a footer within each chat bubble. This is particularly useful for displaying timestamps or other additional information related to the message.

* **Incoming Bubble Settings** - The [`incomingBubbleSettings`] property allows you to customize the appearance of incoming chat bubbles, including the display of the sender's username, timestamp, avatar, and various padding options.

* **Outgoing Bubble Settings** - The [`outgoingBubbleSettings`] property allows you to customize the appearance of outgoing chat bubbles, including the display of the sender's username, timestamp, avatar, and various padding options.