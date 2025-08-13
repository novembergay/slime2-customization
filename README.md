Setting up slime2 and adding a custom font for chat

extension home page: [https://slime2.stream/](https://slime2.stream/)

general installation guide: [https://forums.slime2.stream/resources/widget-setup.3/](https://forums.slime2.stream/resources/widget-setup.3/)

Steps for installing a custom font will be applicable for the [Flexible Bubble Chat widget](https://forums.slime2.stream/resources/flexible-bubble-chat.22/) but should apply for other slime2 chat widgets if a different one is used.

Flexible Bubble Chat has 2 different display modes to switch between, Full and Compact, but adding the custom font will apply to both.

### Prep Steps:
1. Download a slime2 chat widget like [Flexible Bubble Chat](https://forums.slime2.stream/resources/flexible-bubble-chat.22/)
2. Place downloaded widget wherever you store your in-use OBS assets
3. Configure widget _outside of OBS_ by following the general setup instructions: [widget setup guide](https://forums.slime2.stream/resources/widget-setup.3/)
4. Confirm the slime2 widget works correctly as a Browser Source in OBS
5. Download the custom font you want to use

### Adding a Custom Font:
Downloading a custom font should give you a `.ttf` ; `.woff` ; `.woff2` ; or other font file type. You can install the font on your computer itself if you want to use it in other applications, but that is not required for using it in slime2.

The font file will be copied over to the slime2 widget folder, and then referenced directly so that it is used when rendering text in the chat widget. After copying over the file, you will need to edit the `.css` text file that provides the style for the chat widget rendered as a Browser Source. Finally, the newly added font will be manually specified to be used in the widget.

### Custom Font Install Steps:
1. Locate the root directory of the slime2 chat widget. After configuring the widget, this will be where the `.html` ; `.js` ; and your `SLIME2_TWITCH_KEY.js` are located.
2. Copy the custom font file into this location.
3. Copy the full file name of the font file. example: `AtkinsonHyperlegibleNext.ttf`
4. Open the `.css` style file for your widget. For Flexible Bubble Chat: `styles-flex-chat.css`
5. Add a definition for your custom font to the top of the `.css` file:

~~~ css
@font-face {
    font-family: 'AtkinsonHyperlegibleNext';
    src: url('AtkinsonHyperlegibleNext.ttf') format('truetype');
    font-style: normal;
}
~~~

6. Open your slime2 chat widget and go to the font settings. Open this directly in the browser so settings can be saved, not in OBS.
7. Your font will not show up in the font selector. However, enter the exact name set for the `font-family` manually into the Font field. You should see the Font Preview change correctly to your new font.
8. Check the font applies in the browser successfully with some test messages.
9. Save your Widget Settings and close the browser.
10. Check that the font loads correctly in OBS after opening the chat widget in a Browser Source.


NOTES:
- `font-family` name that you will be how you reference your custom font. it can be whatever name you want
- `url` value should be the copied file name with extension of your custom font. No paths are added since it is placed next to the widget files.
- `format` will depend on your actual font file extensions. Use one of the following values based on what extension your font file ends with.

| font file extension | format value |
| - | - |
| `.ttf` | 'truetype' |
| `.woff` | 'woff' |
| `.woff2` | 'woff2' |

- `font-style` is "normal" since this was a non-italic font. if you want to also specify a separate italic font, you can add another identical block referencing a different font file, with the same `font-family` value, with `font-style`: italic;

_Italics Example_
~~~css
@font-face {
    font-family: 'AtkinsonHyperlegibleNext';
    src: url('AtkinsonHyperlegibleNext-Italic.ttf') format('truetype');
    font-style: italic;
}
~~~

END NOTES;


