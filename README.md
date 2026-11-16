# 📎✍️📌 Sticky Paperclip

A plugin for Nagram XF. The paperclip (attach files and photos) button stays in the message field while you type, so you can write your text first and add a file after.

## Why I made it

The paperclip disappeared the moment I started typing. When I had written a message and then wanted to attach something, there was no button for it.

## The cause

Nagram's attach menu in the input option (on by default) hides the paperclip as soon as the field has text. The chat's send button check calls the attach button check with "hide", which removes the button and fades it out together with the bot, silent and scheduled buttons next to it.

## What the plugin does

* It turns that hide call into the app's own "keep shown" path, so the button keeps its normal tap, its icon and its spot.
* The message field keeps room for the button, so long text wraps before it and never runs under it. The room is measured from the paperclip itself and set again every time the app works out the field's width (switching topics, scheduled messages loading, the keyboard opening or closing, turning the phone). The emoji and send buttons stay where they are.
* The paperclip is taken out of the fade animation; the bot, silent and scheduled buttons next to it still fade away while you type, as before.
* Tapping it opens the attach sheet with your text kept, like a normal tap.

## Changes

* 1.0.1: typed text could slide under the paperclip after a topic switch. The app recalculates the message field's width whenever it checks for scheduled messages, and that check only looked at the bot, silent and scheduled buttons, which are faded out while you type, so it gave the field almost no room on the right. The plugin now gives the room back right after each of those checks, using the paperclip's real width, and never lets the field shrink below a usable size.
* 1.0.0: first release.

## Performance

It only acts at the moment the app was about to hide the button or recalculate the field's width. Nothing is polled or redrawn, and nothing runs per keystroke beyond two very cheap hook calls (the hooks run in Java, not Python). The field's width is only written when it actually changes. Logcat tag `XFClip`, errors only.

## Measured

Pixel 6 Pro, Nagram XF 12.10.1 plugin build, a busy forum topic with the Page Up Down plugin on, three rounds of typing and clearing a short sentence:

* Main thread CPU: 30 to 36 ticks without the plugin, 28 with it
* Slowest frames: 90th percentile 40 to 42 ms without, 27 to 28 ms with; 99th percentile 53 to 69 ms without, 32 to 34 ms with

1.0.1, same phone, a quieter topic, same three rounds: main thread CPU 32 ticks, no janky frames, 90th percentile 13 ms, 99th percentile 16 ms.

## Install

1. Use the plugin build of Nagram XF and turn on the plugin engine (Settings, N Settings, Plugins).
2. Download `sticky_paperclip.plugin` from the latest release.
3. Send it to your Saved Messages, tap it and choose install.

Switching the plugin off removes the hooks; the next time you clear the field the paperclip behaves as stock again.

## License

MIT

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=firestarter1996/xf-sticky-paperclip&type=Date)](https://star-history.com/#firestarter1996/xf-sticky-paperclip&Date)
