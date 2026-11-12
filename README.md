# 📎✍️📌 Sticky Paperclip

A plugin for Nagram XF. The paperclip (attach files and photos) button stays in the message field while you type, so you can write your text first and add a file after.

## Why I made it

The paperclip disappeared the moment I started typing. When I had written a message and then wanted to attach something, there was no button for it.

## The cause

Nagram's attach menu in the input option (on by default) hides the paperclip as soon as the field has text. The chat's send button check calls the attach button check with "hide", which removes the button and fades it out together with the bot, silent and scheduled buttons next to it.

## What the plugin does

* It turns that hide call into the app's own "keep shown" path, so the button keeps its normal tap, its icon and its spot.
* The message field keeps room for the button, so long text wraps before it and never runs under it. The emoji and send buttons stay where they are.
* The paperclip is taken out of the fade animation; the bot, silent and scheduled buttons next to it still fade away while you type, as before.
* Tapping it opens the attach sheet with your text kept, like a normal tap.

## Performance

It only acts at the moment the app was about to hide the button. Nothing is polled or redrawn, and nothing runs per keystroke beyond two very cheap hook calls (the hooks run in Java, not Python). Logcat tag `XFClip`, errors only.

## Measured

Pixel 6 Pro, Nagram XF 12.10.1 plugin build, a busy forum topic with the Page Up Down plugin on, three rounds of typing and clearing a short sentence:

* Main thread CPU: 30 to 36 ticks without the plugin, 28 with it
* Slowest frames: 90th percentile 40 to 42 ms without, 27 to 28 ms with; 99th percentile 53 to 69 ms without, 32 to 34 ms with

## Install

1. Use the plugin build of Nagram XF and turn on the plugin engine (Settings, N Settings, Plugins).
2. Download `sticky_paperclip.plugin` from the latest release.
3. Send it to your Saved Messages, tap it and choose install.

Switching the plugin off removes the hooks; the next time you clear the field the paperclip behaves as stock again.

## License

MIT

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=firestarter1996/xf-sticky-paperclip&type=Date)](https://star-history.com/#firestarter1996/xf-sticky-paperclip&Date)
