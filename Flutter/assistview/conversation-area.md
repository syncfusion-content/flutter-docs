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

  late List<AssistMessage> _messages;

  void _generativeResponse(String data) async {
    final String response = await _getAIResponse(data);
    setState(() {
      _messages.add(AssistMessage.response(
        data: response,
        time: DateTime.now(),
        author: const AssistMessageAuthor(id: '123-002', name: 'AI Bot'),
      ));
    });
  }

  Future<String> _getAIResponse(String data) async {
    String response = '';
    // Connect with your preferred AI to generate a response to the request.
    return response;
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfAIAssistView(
        messages: _messages,
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(
                data: data,
                time: DateTime.now(),
                author: const AssistMessageAuthor(id: '123-001', name: 'User'),
              ));
            });
            _generativeResponse(data);
          },
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

### Request message

Customize the content of request messages by changing the background color, background shape, and other features based on the message, index, or specific conditions.

{% tabs %}
{% highlight dart %}

  late List<AssistMessage> _messages;

  void _generativeResponse(String data) async {
    final String response = await _getAIResponse(data);
    setState(() {
      _messages.add(AssistMessage.response(data: response));
    });
  }

  Future<String> _getAIResponse(String data) async {
    String response = '';
    // Connect with your preferred AI to generate a response to the request.
    return response;
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfAIAssistView(
        messages: _messages,
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(data: data));
            });
            _generativeResponse(data);
          },
        ),
        requestBubbleSettings: const AssistBubbleSettings(
          contentBackgroundColor: Color(0xFFF1F8E9),
          contentShape: RoundedRectangleBorder(
            borderRadius: BorderRadius.all(Radius.circular(10)),
          ),
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

### Response message

Customize the content of response messages by changing the background color, background shape, and other features based on the message, index, or specific conditions.

{% tabs %}
{% highlight dart %}

  late List<AssistMessage> _messages;

  void _generativeResponse(String data) async {
    final String response = await _getAIResponse(data);
    setState(() {
      _messages.add(AssistMessage.response(data: response));
    });
  }

  Future<String> _getAIResponse(String data) async {
    String response = '';
    // Connect with your preferred AI to generate a response to the request.
    return response;
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfAIAssistView(
        messages: _messages,
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(data: data));
            });
            _generativeResponse(data);
          },
        ),
        responseBubbleSettings: const AssistBubbleSettings(
          contentBackgroundColor: Color(0xFFE1F5FE),
          contentShape: RoundedRectangleBorder(
            borderRadius: BorderRadius.all(Radius.circular(5)),
          ),
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

### Header

The header displays the username of the message's author along with the time stamp of when the message was sent. Additionally, you can build a custom widget to display more information about messages.

{% tabs %}
{% highlight dart %}

  late List<AssistMessage> _messages;

  void _generativeResponse(String data) async {
    final String response = await _getAIResponse(data);
    setState(() {
      _messages.add(AssistMessage.response(
        data: response,
        time: DateTime.now(),
        author: const AssistMessageAuthor(id: '123-002', name: 'AI Bot'),
      ));
    });
  }

  Future<String> _getAIResponse(String data) async {
    String response = '';
    // Connect with your preferred AI to generate a response to the request.
    return response;
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfAIAssistView(
        messages: _messages,
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(
                data: data,
                time: DateTime.now(),
                author: const AssistMessageAuthor(id: '123-001', name: 'User'),
              ));
            });
            _generativeResponse(data);
          },
        ),
        requestBubbleSettings: const AssistBubbleSettings(
          showUserName: true,
          showTimestamp: true,
          showUserAvatar: true,
        ),
        responseBubbleSettings: const AssistBubbleSettings(
          showUserName: true,
          showTimestamp: true,
          showUserAvatar: true,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

### Footer

Showcases additional functionalities and information, including feedback options, AI model details, and more.

### Avatar

The message author's avatar displays either an image or the initials of their name. By default, if the avatar image source is not defined, the user's initials will be displayed. Additionally, you can create a custom widget that shows more information about the user.

{% tabs %}
{% highlight dart %}

  late List<AssistMessage> _messages;

  void _generativeResponse(String data) async {
    final String response = await _getAIResponse(data);
    setState(() {
      _messages.add(AssistMessage.response(
        data: response,
        time: DateTime.now(),
        author: const AssistMessageAuthor(
            id: '123-002', 
            name: 'AI Bot',
            avatar: NetworkImage('https://example.com/path/to/bot-avatar.jpg'),
        ),
      ));
    });
  }

  Future<String> _getAIResponse(String data) async {
    String response = '';
    // Connect with your preferred AI to generate a response to the request.
    return response;
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfAIAssistView(
        messages: _messages,
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(
                data: data,
                time: DateTime.now(),
                author: const AssistMessageAuthor(
                    id: '123-001', 
                    name: 'User',
                    avatar: NetworkImage('https://example.com/path/to/men-avatar.jpg'),
                ),
              ));
            });
            _generativeResponse(data);
          },
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

### Content area

Customize the area where message content is displayed by changing its background color, shape, and functionalities based on the user or other specific conditions.

{% tabs %}
{% highlight dart %}

  late List<AssistMessage> _messages;

  void _generativeResponse(String data) async {
    final String response = await _getAIResponse(data);
    setState(() {
      _messages.add(AssistMessage.response(data: response));
    });
  }

  Future<String> _getAIResponse(String data) async {
    String response = '';
    // Connect with your preferred AI to generate a response to the request.
    return response;
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfAIAssistView(
        messages: _messages,
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(data: data));
            });
            _generativeResponse(data);
          },
        ),
        requestBubbleSettings: const AssistBubbleSettings(
          contentBackgroundColor: Color(0xFFF1F8E9),
          contentShape: RoundedRectangleBorder(
            borderRadius: BorderRadius.all(Radius.circular(10)),
          ),
        ),
        responseBubbleSettings: const AssistBubbleSettings(
          contentBackgroundColor: Color(0xFFE1F5FE),
          contentShape: RoundedRectangleBorder(
            borderRadius: BorderRadius.all(Radius.circular(5)),
          ),
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

### Suggestions

Provide a list response suggestions. When the user selects one, it is considered a new request message. The suggestions' layout, background, colors, and more can be customized.

{% tabs %}
{% highlight dart %}

  late List<AssistMessage> _messages;

  void _generativeResponse(String data) async {
    final String response = await _getAIResponse(data);
    setState(() {
      _messages.add(AssistMessage.response(
        data: response,
        suggestions: [
          const AssistMessageSuggestion(
            data: 'Time to relax!',
            selected: false,
          ),
          const AssistMessageSuggestion(
            data: 'Let’s get creative!',
            selected: false,
          ),
          const AssistMessageSuggestion(
            data: 'Try something new!',
            selected: false,
          ),
        ],
        suggestionSettings: AssistSuggestionSettings(
          itemBackgroundColor: WidgetStateProperty.resolveWith<Color>((states) {
            if (states.contains(WidgetState.hovered)) {
              return Colors.green.shade200;
            }
            return Colors.red.shade300;
          }),
          orientation: Axis.horizontal,
          itemOverflow: AssistSuggestionOverflow.wrap,
          selectionType: AssistSuggestionSelectionType.single,
        ),
      ));
    });
  }

  Future<String> _getAIResponse(String data) async {
    String response = '';
    // Connect with your preferred AI to generate a response to the request.
    return response;
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfAIAssistView(
        messages: _messages,
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(data: data));
            });
            _generativeResponse(data);
          },
        ),
        onSuggestionItemSelected:
            (selected, messageIndex, suggestion, suggestionIndex) {
          setState(() {
            _messages[messageIndex].suggestions![suggestionIndex] =
                suggestion.copyWith(selected: selected);
            _messages.add(AssistMessage.request(
                data: suggestion.data!,
                time: DateTime.now(),
                author:
                    const AssistMessageAuthor(id: '123-001', name: 'User')));
            _generativeResponse(suggestion.data!);
          });
        },
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

### Loading indicator

Indicates that the AI service's response is in progress after a request has been submitted. By default, the indicator is a shimmer effect that is displayed until the response is received.

{% tabs %}
{% highlight dart %}

  late List<AssistMessage> _messages;

  void _generativeResponse(String data) async {
    final String response = await _getAIResponse(data);
    setState(() {
      _messages.add(AssistMessage.response(data: response));
    });
  }

  Future<String> _getAIResponse(String data) async {
    String response = '';
    // Connect with your preferred AI to generate a response to the request.
    return response;
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfAIAssistView(
        messages: _messages,
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(data: data));
            });
            _generativeResponse(data);
          },
        ),
        responseLoadingBuilder: _buildResponseLoadingBuilder,
      ),
    );
  }

Widget _buildResponseLoadingBuilder(
    BuildContext context, int index, AssistMessage message) {
  return SizedBox(
    width: 80.0,
    height: 24.0,
    child: Row(
      mainAxisAlignment: MainAxisAlignment.center,
      children: List.generate(3, (dotIndex) {
        return AnimatedDot(dotIndex: dotIndex);
      }),
    ),
  );
}

class AnimatedDot extends StatefulWidget {
  final int dotIndex;

  const AnimatedDot({super.key, required this.dotIndex});

  @override
  AnimatedDotState createState() => AnimatedDotState();
}

class AnimatedDotState extends State<AnimatedDot>
    with SingleTickerProviderStateMixin {
  late AnimationController _controller;
  late Animation<double> _animation;

  @override
  void initState() {
    super.initState();
    _controller = AnimationController(
      duration: const Duration(milliseconds: 600),
      vsync: this,
    )..repeat(reverse: true);

    _animation = Tween<double>(begin: 0.0, end: 1.0).animate(
      CurvedAnimation(
        parent: _controller,
        curve: Interval(
          (widget.dotIndex) * 0.2,
          (widget.dotIndex + 1) * 0.2,
          curve: Curves.easeInOut,
        ),
      ),
    );
  }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return FadeTransition(
      opacity: _animation,
      child: const Padding(
        padding: EdgeInsets.symmetric(horizontal: 4.0),
        child: Text(
          '•',
          style: TextStyle(
            fontSize: 24.0,
          ),
        ),
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

### Toolbar items

Append a toolbar to response messages that provides options to perform various actions, such as rating the response, sharing it, copying it, and more.

{% tabs %}
{% highlight dart %}

  late List<AssistMessage> _messages;

  void _generativeResponse(String data) async {
    final String response = await _getAIResponse(data);
    setState(() {
      _messages.add(AssistMessage.response(
        data: response,
        toolbarItems: [
          const AssistMessageToolbarItem(
            content: Icon(Icons.thumb_up_outlined),
            tooltip: 'Like',
          ),
          const AssistMessageToolbarItem(
            content: Icon(Icons.thumb_down_outlined),
            tooltip: 'DisLike',
          ),
          const AssistMessageToolbarItem(
            content: Icon(Icons.copy_all),
            tooltip: 'Copy',
          ),
          const AssistMessageToolbarItem(
            content: Icon(Icons.restart_alt),
            tooltip: 'Restart',
          ),
        ],
      ));
    });
  }

  Future<String> _getAIResponse(String data) async {
    String response = '';
    // Connect with your preferred AI to generate a response to the request.
    return response;
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfAIAssistView(
        messages: _messages,
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(data: data));
            });
            _generativeResponse(data);
          },
        ),
        onBubbleToolbarItemSelected:
            (selected, messageIndex, toolbarItem, toolbarItemIndex) {
          setState(() {
            _messages[messageIndex].toolbarItems![toolbarItemIndex] =
                toolbarItem.copyWith(
              isSelected: selected,
            );
          });
        },
        responseToolbarSettings: AssistMessageToolbarSettings(
          itemBackgroundColor: WidgetStateProperty.resolveWith(
            (Set<WidgetState> state) {
              if (state.contains(WidgetState.hovered)) {
                return Colors.lightBlueAccent;
              }
              return Colors.lightBlue;
            },
          ),
          itemShape: WidgetStateProperty.resolveWith(
            (Set<WidgetState> state) {
              if (state.contains(WidgetState.hovered)) {
                return RoundedRectangleBorder(
                  borderRadius: BorderRadius.circular(8.0),
                );
              }
              return RoundedRectangleBorder(
                borderRadius: BorderRadius.circular(10.0),
              );
            },
          ),
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

>You can refer to our [Flutter Chat](https://www.syncfusion.com/flutter-widgets/flutter-chat) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter Chat example](https://flutter.syncfusion.com/#/chat/getting-started) which demonstrates conversations between two or more users in a fully customizable layout and shows how to easily configure the chat with built-in support for creating stunning visual effects.

#### See Also

* You can also customize the bubble shapes and colors properties of both [`requestBubbleSettings`] and [`responseBubbleSettings`] using [`SfAIAssistViewTheme`] by wrapping with [`SfAIAssistView`].