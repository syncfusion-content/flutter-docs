---
layout: post
title: About Flutter AssistView widget | Syncfusion 
description: Learn here all about the introduction of Syncfusion Flutter AssistView (SfAIAssistView) widget, its features, and more.
platform: flutter
control: SfAIAssistView
documentation: ug
---

# Flutter AssistView (SfAIAssistView) Overview

The Syncfusion Flutter AI AssistView widget is a powerful and customizable tool designed to simplify the integration of AI assistant functionality. It allows users to customize message content, headers, footers, avatars, response toolbars, loading indicators, suggestion items, text editors, and action buttons.

## Placeholder

Define a custom placeholder widget to display at the top of all messages, serving as a header, or to be shown when there are no messages in the chat.

### Hide on message

The placeholder is visible when there are no messages in the conversation and is hidden once a new message is added.

### Scroll with message

The placeholder scrolls along with the messages as new content is added, maintaining its position until it's no longer needed.

## Composer

The primary text editor where new request messages can be composed. You can also integrate custom composer widgets.

### Default composer

The default composer is a rounded rectangular text editor that allows users to compose request messages. You can customize its appearance by adding hint text, borders, prefix icons, suffix icons, and more.

### Builder

The [`AssistComposer.builder`] enables the option to specify any type of widget as a primary composer, which is useful for integrating additional options alongside the text field, such as a microphone button, file attachment button, and so on.

## Action Button

Define buttons that perform actions such as sending a message, attaching a file, recording a voice message, and more.

### Default action button

The default action button is a send button. Pressing or clicking this button triggers a callback, allowing the user to request a response to their composed message from their preferred AI service.

### Builder

Define a custom widget consisting of one or more interactive widgets to serve as action buttons, such as a send button, microphone button, or file attachment button.

## Conversation area

The AI AssistView displays the content of user requests and AI responses. Each message includes details like the message's text, sending time stamp, and author. The response message contains additional information, including suggestions and toolbar items.

### Request message

Customize the content of request messages by changing the background color, background shape, and other features based on the message, index, or specific conditions.

### Response message

Customize the content of response messages by changing the background color, background shape, and other features based on the message, index, or specific conditions.

### Header

The header displays the username of the message's author along with the time stamp of when the message was sent. Additionally, you can build a custom widget to display more information about messages.

### Footer

The footer showcases additional functionalities and information, such as feedback options, AI model details, and more. Moreover, you can build a custom widget to display more information about messages.

### Avatar

The message author's avatar displays either an image or the initials of their name. By default, if the avatar image source is not defined, the user's initials will be displayed. Additionally, you can create a custom widget that shows more information about the user.

### Content area

Customize the area where message content is displayed by changing its background color, shape, and functionalities based on the user or other specific conditions.

### Suggestions

Provide a list response suggestions. When the user selects one, it is considered a new request message. The suggestions' layout, background, colors, and more can be customized.

### Loading indicator

Indicates that the AI service's response is in progress after a request has been submitted. By default, the indicator is a shimmer effect that is displayed until the response is received.

### Toolbar items

Append a toolbar to response messages that provides options to perform various actions, such as rating the response, sharing it, copying it, and more.

>You can refer to our [Flutter Chat](https://www.syncfusion.com/flutter-widgets/flutter-chat) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter Chat example](https://flutter.syncfusion.com/#/chat/getting-started) which demonstrates conversations between two or more users in a fully customizable layout and shows how to easily configure the chat with built-in support for creating stunning visual effects.