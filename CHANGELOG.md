# CHANGELOG.md

## v1.4.0 (22-03-2024)

**Added:**
- A new `chatWindow` section has been added into the [**Configurations**](https://react-chatbotify.tjtanjin.com/docs/introduction/bot_options#configurations) category with the following default values:
  ```
  chatWindow: {
    showScrollbar: false,
    autoJumpToBottom: false,
    showMessagePrompt: true,
    messagePromptText: "New Messages ↓",
    messagePromptOffset: 30,
  }
  ```
  Explanations for what each property does can be found on the [**documentation website**](https://react-chatbotify.tjtanjin.com/docs/introduction/bot_options#configurations).

**Fixed:**
- Fixed an occasional issue where stream messages do not autoscroll when user is at the bottom of the chat
- Fixed an issue where users can interrupt the `start` block if it is streaming
- Fixed a bug where users can pinch-zoom the chat window on mobile devices to cause it to be distorted
- Fixed a rare bug where the chat window could be scrolled out of view
- Fixed a longstanding issue where playing notification sounds on mobile devices causes media controls to appear in notifications tray

**Note:**

Initially planned for only bug fixes, I eventually added a whole new `chatWindow` section simply because I felt there were many small areas that could use enhancements (hiding the scrollbar, showing new message prompts instead of forcing users to the bottom etc). This led to **version 1.4.0** which was entirely focused on cleaning up the imperfections from the several changes that have been made in the last few releases.

## v1.3.2 (16-03-2024)

**Fixed:**
- Fixed an issue where chat window auto-scrolling does not work for streamed messages
- Fixed an issue where loading chat history caused current scroll position to shift
- Fixed an issue where extremely long words get abruptly cut-off at the tail end of the message bubble

## v1.3.1 (13-03-2024)

**Added:**
- Added `simStream` and `streamSpeed` options for `userBubble` to be consistent with `botBubble`

**Fixed:**
- Fixed an issue where users can quickly click on **options** or **checkboxes** in rapid succession resulting in multiple inputs
- Fixed an issue where simulating stream messages would ignore the `blockSpam` option

## v1.3.0 (12-03-2024)

**Added:**
- Added `simStream` and `streamSpeed` options within `botBubble` to simulate streaming of messages
- Added `params.streamMessage` parameter that allows real-time streaming of messages (great for integration with LLMs)

**Modified:**
- The `isUser` field within [`Message`](https://react-chatbotify.tjtanjin.com/docs/introduction/conversations#message) component has been replaced with `sender`.
- Both `params.injectMessage` and newly added `params.streamMessage` are now **async** functions (previously, `params.injectMessage` was **non-async**)

**Miscellaneous:**
- Internally, logic for chat history, notifications and a few other minor areas have been updated to support stream messages

**Note:**

The [documentation website](https://react-chatbotify.tjtanjin.com/docs/introduction/bot_options/) has been updated to reflect all the latest information. A possible "breaking" change would be `params.injectMessage` which is now **async**. Depending on your existing usage, there might not be a need to make any changes. However, if you are using multiple `params.injectMessage` in quick succession, this could mean multiple messages are being sent at once without the use of **await**.

## v1.2.0 (12-02-2024)

**Fixed:**
- Fixed chatbot window resizing on mobile devices (previously window is out of view on some devices/browsers)
- Fixed chatbot window orientation (previously chatbot would not re-orientate on phone rotation)

**Note:**

The above fixes are important for users who wish to properly support the chatbot on mobile devices. While there has been significantly more mobile view tests done for these fixes, it is near-impossible to exhaustively run through all devices/browsers. Should anyone still encounter issues with mobile view, please do not hesitate to [reach out](https://discord.com/invite/X8VSdZvBQY).

## v1.1.0 (28-01-2024)

**Added:**
- Added support for enforcing & showing character count/limit via the following options:
  - `chatInput.showCharacterCount`: false
  - `chatInput.characterLimit`: -1
- Added support for styling the above character limit display via the following styles:
  - `characterLimitStyle`
  - `characterLimitReachedStyle`

**Note:**

The above additions have been updated on the [documentation website](https://react-chatbotify.tjtanjin.com/docs/introduction/bot_options/) for reference.

## v1.0.6 (10-09-2023)

**Fixed:**
- Fixed async file uploads

**Miscellaneous:**
- Disabled speech recognition on unsupported browsers (e.g. Opera)

## v1.0.5 (31-08-2023)

**Fixed:**
- Fixed missing support for user defined async functions (important fix if you wish to make use of API calls and wait for completion)

## v1.0.4 (13-08-2023)

**Fixed:**
- Fixed module export (imports by consumers should work properly for both cjs and mjs)

## v1.0.3 (05-08-2023)

**Added:**
- Added `desktopEnabled` and `mobileEnabled` options under the `theme` section to allow developers to control chatbot visibility based on platform

**Fixed:**
- Fixed a bug with distorted layout for embedded chat windows on mobile

## v1.0.2 (03-08-2023)

**Fixed:**
- Fixed missing export in _package.json_

## v1.0.1 (03-08-2023)

**Miscellaneous:**
- Cleanup _dist_ folder (halved the build size)
- Cleanup unused exports
- Cleanup documentation and configurations

## v1.0.0 (02-08-2023)

**Added:**
- Initial Release