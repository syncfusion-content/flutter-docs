# Chat UG Documentation Change Report

This document summarizes the updates made to the Flutter Chat UG pages in this folder.

## Overview

- Renamed the duplicate `Message Content` feature bullet to `Custom Message Content`.
- Verified the `messageContentBuilder` link and kept it aligned with the API documentation.
- Added cross-links from the feature list to the conversation area sections for header, footer, and content customization.

## Getting Started

- Added `syncfusion_flutter_core` alongside `syncfusion_flutter_chat` in the dependency guidance.
- Rewrote the examples as complete runnable Flutter snippets with imports and class wrappers.
- Fixed the placeholder example so `_messages` is initialized correctly.
- Updated the action button section wording for clarity.
- Adjusted the composer and placeholder image captions to better match the section intent.

## Composer

- Added complete runnable examples for every composer property section.
- Expanded the decoration guidance to mention more supported `InputDecoration` properties.
- Documented `editorTextStyle` in the intro and linked it to chat theme styling.
- Reworked the builder example into a working stateful sample.
- Added controller disposal, message appending, clearing the text controller, and a note about empty `onPressed` values when using `ChatComposer.builder`.
- Replaced deprecated `withOpacity` usage with `withValues(alpha: ...)`.

## Conversation Area

- Added runnable examples for messages, suggestions, outgoing user, and message settings.
- Introduced dedicated sections for `messageHeaderBuilder`, `messageFooterBuilder`, and `messageContentBuilder`.
- Added the missing `intl` import note for timestamp formatting.
- Clarified `ChatAuthor.avatar` input types as `ImageProvider`.
- Consolidated bubble-setting examples into one clean, comprehensive example.
- Fixed grammar and clarity issues in the outgoing user and message settings descriptions.

## Action Button

- Rewrote all examples as complete runnable Flutter samples.
- Clarified that `SfChat` does not auto-add composed text to the messages list.
- Added builder behavior guidance and a cross-reference to the composer page.
- Fixed deprecated color handling using `withValues(alpha: ...)`.
- Corrected the missing `_messages` and `_outgoingUserId` issues.
- Added a new `Enable or disable action button` section.

## Chat Theme

- Added dependency guidance for both `syncfusion_flutter_chat` and `syncfusion_flutter_core`.
- Replaced partial snippets with complete runnable examples.
- Standardized code fences and removed inconsistent `Dart` casing.
- Corrected the outgoing/incoming message shape naming to `outgoingMessageContentShape` and `incomingMessageContentShape`.
- Consolidated the large list of theme properties into clearer grouped sections.
- Removed problematic const/color patterns and cleaned up sample usage.

## Placeholder

- Converted the placeholder example into a complete runnable Flutter sample.
- Fixed the intro wording to say the placeholder is removed once messages are added.
- Kept the example layout focused and valid with imports and a class wrapper.
- Added a `See Also` section linking to related chat pages.

## Right to Left

- Corrected the page title and front matter so it matches RTL support instead of placeholder content.
- Added both RTL approaches: `Directionality` and `MaterialApp` locale-based rendering.
- Rewrote all examples as complete runnable snippets.
- Added explicit coverage for placeholder, composer, action button, and message content RTL behavior.
- Clarified that message header and footer also render correctly in RTL.
- Added a note about `AssetImage` sample assets needing to exist in the app.

## FlutterFlow Custom Widget

- Updated the page title and description for consistency.
- Cleaned up boilerplate wording and removed the raw icon reference text.
- Standardized the dependency note to say the current version targets the latest Flutter SDK.
- Clarified that `syncfusion_flutter_core` must also be added.
- Reworded the widget-code sample instructions for clarity.
- Added troubleshooting guidance for compile issues.
- Added a note about passing data into the custom widget from FlutterFlow.
