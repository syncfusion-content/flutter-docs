---
layout: post
title: Action Button in Flutter Chat widget | Syncfusion
description: Learn here all about the Action Button feature of Syncfusion Flutter Chat (SfChat) widget and how it enhances user interaction and customization.
platform: flutter
control: SfChat
documentation: ug
---

# Action Button in Flutter Chat (SfChat)

This section explains how to integrate and customize the action button in the chat widget.

## Action Button

The [`actionButton`] property in the chat widget is used to send messages or trigger other interactions within the action button UI. This property uses the [`ChatActionButton`] widget, which provides a standard button for sending new messages.

By default, the chat widget does not rebuild itself when the send button is clicked. Therefore, it is necessary to create a new message object using the newly composed message passed as a parameter in the [`onPressed`] callback of the [`ChatActionButton`]. After that, you should rebuild the widget using the [`setState`] function.

{% tabs %}
{% highlight dart %}

// Load if there are existing messages.
final List<ChatMessage> _messages = <ChatMessage>[];
final String _outgoingUserId = '';

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfChat(
      messages: _messages,
      outgoingUser: _outgoingUserId,
      actionButton: ChatActionButton(
        onPressed: (String newMessage) {
          setState(() {
            _messages.add(
              ChatMessage(
                text: newMessage,
                time: DateTime.now(),
                author: ChatAuthor(
                  id: _outgoingUserId,
                  name: 'John Doe',
                ),
              ),
            );
          });
        },
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Chat actionButton support](images/action-button/actionbutton-background.png)

## Custom Action Button

The [`actionButton`] property in the chat widget can be customized using [`ChatActionButton`]. This allows you to adjust the button’s appearance and behavior to match your app’s design. You can change the button’s content, colors, shape, size, shadow, cursor, and padding to make sure it fits well with your app’s look and feels.

### Child

* The [`child`] property defines the content of the button, such as an icon or text.

### Tooltip

* The [`tooltip`] property provides a hint or description when the user hovers over the button.

### Colors

* The [`foregroundColor`] property sets the color of the button's text and icons.
* The [`backgroundColor`] property defines the button's background color.
* The [`focusColor`] property sets the color displayed when the button gains focus.
* The [`hoverColor`] property defines the color displayed when the button is hovered over.
* The [`splashColor`] property specifies the color of the ripple effect when the button is pressed.

### Elevation

* The [`elevation`] property sets the z-coordinate of the button, determining its shadow and elevation.
* The [`focusElevation`] property defines the elevation of the button when it has focus.
* The [`hoverElevation`] property sets the elevation of the button when it is hovered over.
* The [`highlightElevation`] property determines the elevation when the button is pressed.

### Mouse Cursor

* The [`mouseCursor`] property defines the type of cursor that appears when hovering over the button.

### Shape

* The [`shape`] property sets the shape of the button's border, such as rounded or circular.

### Padding

* The [`padding`] property defines the space inside the button between its border and the content.

### Size

* The [`size`] property specifies the width and height of the button.

### onPressed callback

* The [`onPressed`] property specifies a callback function triggered when the button is pressed.

{% tabs %}
{% highlight dart %}

// Load if there are existing messages.
final List<ChatMessage> _messages = <ChatMessage>[];
final String _outgoingUserId = '';

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfChat(
      messages: _messages,
      outgoingUser: _outgoingUserId,
      actionButton: ChatActionButton(
        child: Icon(Icons.send, color: Colors.grey[300]),
        tooltip: 'Send Message',
        foregroundColor: Colors.white,
        backgroundColor: Colors.blue,
        focusColor: Colors.lightBlueAccent,
        hoverColor: Colors.blueAccent,
        splashColor: Colors.white.withOpacity(0.3),
        elevation: 2.0,
        focusElevation: 6.0,
        hoverElevation: 4.0,
        highlightElevation: 8.0,
        mouseCursor: SystemMouseCursors.click,
        shape: RoundedRectangleBorder(
            borderRadius: BorderRadius.circular(25.0)),
        padding: const EdgeInsetsDirectional.only(start: 8.0),
        size: const Size.square(40.0),
        onPressed: (String newMessage) {
          setState(() {
            _messages.add(
              ChatMessage(
                text: newMessage,
                time: DateTime.now(),
                author: ChatAuthor(
                  id: _outgoingUserId,
                  name: 'John Doe',
                ),
              ),
            );
          });
        },
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Chat actionButton support](images/action-button/customized-actionbutton-chat.png)

#### See Also

* You can also customize the above properties using [`SfChatTheme`] by wrapping with [`SfChat`].