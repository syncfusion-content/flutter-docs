---
layout: post
title: Composer in Flutter AI AssistView widget | Syncfusion
description: Learn here all about Composer feature of Syncfusion Flutter AI AssistView (SfAIAssistView) widget, including its properties and more.
platform: flutter
control: SfAIAssistView
documentation: ug
---

# Composer in Flutter AI AssistView (SfAIAssistView)

This section explains the customization options available in [`AssistComposer`], including the option to add any type of widget as a composer.

## Default Composer

The default [`composer`] is a rounded rectangular text editor that allows users to compose request messages. You can customize its appearance by adding hint text, borders, prefix icons, suffix icons, and more.

When the composer is null, no default text field is added to the assist widget.

### Minimum and maximum lines

* [`minLines`] specifies the minimum number of lines in the text span, which affects the height of the text field.
* [`maxLines`] defines the maximum number of lines for the text, determining how many lines are visible when the text wraps.

The default value for minLines is 1, and the default value for maxLines is 6.

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
        composer: const AssistComposer(
          minLines: 2,
          maxLines: 3,
        ),
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(data: data));
            });
            _generativeResponse(data);
          },
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

### Decoration

The [`decoration`] property customizes the visual attributes of the message input field, such as hint text,borders, and internal padding, using an [`InputDecoration`].

The [`InputDecoration`] class enhances the composer by utilizing its properties, such as borders, labels, icons, and styles.

The following are the major features available in [`InputDecoration`] for decorating the composer:
* [`enabled`]
* [`border`]
* [`contentPadding`]
* [`hintText`]
* [`hintStyle`]
* [`prefixIcon`] and [`suffixIcon`]

#### Enabled

The [`enabled`] property defines whether the compose feature is in an enabled or disabled state. By default, it is set to true. If set to false, the compose feature will be disabled, and the default action button will also be disabled.

#### Border

The [`border`] property defines shape of the border that is drawn around the text field. By default, an [`OutlineInputBorder`] is used.

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
        composer: AssistComposer(
          decoration: InputDecoration(
            border: OutlineInputBorder(
              borderRadius: BorderRadius.circular(10),
            ),
          ),
        ),
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(data: data));
            });
            _generativeResponse(data);
          },
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

#### Content padding

The [`contentPadding`] property defines the padding surrounding the text added inside the text field. By default, the padding is set to 16 horizontally and 18 vertically.

{% tabs %}
{% highlight dart hl_lines="28" %}

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
        composer: const AssistComposer(
          decoration: InputDecoration(
            hintText: 'Type a message',
            contentPadding: EdgeInsets.all(30),
          ),
        ),
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(data: data));
            });
            _generativeResponse(data);
          },
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

#### Hint text

The [`hintText`] property sets the placeholder text for the text field. By default, it is set to null.

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
        composer: const AssistComposer(
          decoration: InputDecoration(
            hintText: 'Type a message',
          ),
        ),
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(data: data));
            });
            _generativeResponse(data);
          },
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

#### Hint text style

The [`hintStyle`] property refers to the text style of the hint text.

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
        composer: const AssistComposer(
          decoration: InputDecoration(
            hintText: 'Type a message',
            hintStyle: TextStyle(
              color: Colors.blue,
              fontSize: 16,
              fontStyle: FontStyle.italic,
            ),
          ),
        ),
        actionButton: AssistActionButton(
          onPressed: (String data) {
            setState(() {
              _messages.add(AssistMessage.request(data: data));
            });
            _generativeResponse(data);
          },
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

#### Prefix and suffix icons

The [`prefixIcon`] and [`suffixIcon`] properties are used to add icons at the beginning and end of the text field, respectively.

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
        composer: const AssistComposer(
          decoration: InputDecoration(
            prefixIcon: Icon(
              Icons.attachment,
              color: Color(0xFF433D8B),
            ),
            suffixIcon: Icon(
              Icons.camera_alt,
              color: Color(0xFF433D8B),
            ),
          ),
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

### Padding

The [`padding`] property defines the space around the text field, which is used to create space between the conversion area and the text field.

By default, the top padding is set to 16.

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
        composer: const AssistComposer(
          padding: EdgeInsets.fromLTRB(10, 30, 10, 20),
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

### Text style

The [`textStyle`] property is used to set the style for the default [`AssistComposer`] text.

The specified text style will be merged with the [`bodyMedium`] and `editorTextStyle` text styles.

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
        composer: const AssistComposer(
          textStyle: TextStyle(
            color: Color(0xFF433D8B),
          ),
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Builder

The [AssistComposer.builder] is used to specify a custom widget for the composer, allowing you to enable multiple options for composing messages, such as text, voice, and image messages.

If [`AssistComposer.builder`] is used, the action button will always be enabled.

{% tabs %}
{% highlight dart %}

  late List<AssistMessage> _messages;
  final TextEditingController _controller = TextEditingController();

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
        composer: builderComposer(),
      ),
    );
  }

  AssistComposer builderComposer() {
    return AssistComposer.builder(
      builder: (context) {
        return Row(
          children: [
            const Icon(
              Icons.add,
              size: 35,
              color: Color(0xFF433D8B),
            ),
            const SizedBox(width: 5),
            Expanded(
              child: Container(
                decoration: BoxDecoration(
                  color: Theme.of(context).colorScheme.primary.withOpacity(0.2),
                  borderRadius: BorderRadius.circular(25),
                ),
                child: TextField(
                  minLines: 1,
                  maxLines: 6,
                  controller: _controller,
                  decoration: InputDecoration(
                    contentPadding: const EdgeInsets.symmetric(
                      vertical: 10,
                      horizontal: 18,
                    ),
                    hintText: 'Messages...',
                    hintStyle: TextStyle(
                      color: Colors.grey.shade800,
                      fontSize: 14,
                      fontWeight: FontWeight.w500,
                    ),
                    suffixIcon: const Padding(
                      padding: EdgeInsets.only(right: 5.0),
                      child: Icon(
                        Icons.emoji_emotions_outlined,
                        color: Color(0xFF433D8B),
                      ),
                    ),
                    border: InputBorder.none,
                  ),
                ),
              ),
            ),
            const SizedBox(width: 7),
            const Icon(
              Icons.send,
              color: Color(0xFF433D8B),
            ),
          ],
        );
      },
    );
  }

{% endhighlight %}
{% endtabs %}

>You can refer to our [`Flutter Chat`](https://www.syncfusion.com/flutter-widgets/flutter-chat) feature tour page for its groundbreaking feature representations. You can also explore our [`Flutter Chat example`](https://flutter.syncfusion.com/#/chat/getting-started) which demonstrates conversations between two or more users in a fully customizable layout and shows how to easily configure the chat with built-in support for creating stunning visual effects.
