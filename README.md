<img src="banner.svg" width="23%" align="right">

Serve
=====
Bundle any script as a macOS _[service]_<sup>*</sup>.

\* Services are [contextual], and can be assigned a <kbd>k</kbd><kbd>e</kbd><kbd>y</kbd>board shortcut under System Preferences:

![](screenshot.png)

[CLI]
-----
`serve script.*` [`--app`] [`--icon icon.*`]

| Option              | Description                                                                                      | Default         |
|:--------------------|:-------------------------------------------------------------------------------------------------|:----------------|
| `-`[`-h`]`elp`      | Print brief usage information.                                                                   |                 |
| `-`[`-v`]`ersion`   | Print running version info.                                                                      |                 |
| `-`[`-n`]`ame`      | Specify the name of the service as it should appear in menus.                                    | Script Name     |
| `-`[`-i`]`nput`     | [Type of input][uti] the service should accept. See below for `--input`s.                        | `auto` (`text`) |
| `-`[`-o`]`utput`    | Replace selected `text`?                                                                         | `false`         |
| `-`[`-a`]`pp`       | Service should only be available for the given `app`lication[`,`s].                              | `any`           |
| `--icon`            | Apply icon from any image, [SVG], [`icns`], app or folder.                                       | `icon.*`        |
| `-`[`-t`]`humbnail` | Specify the `workflow` [Finder thumbnail]. See `Image` drop menu inside Automator.app for icons. | Action          |
| `-`[`c`]`olor`      | Specify a `workflow` colour                                                                      |                 |
| `--install`         | Compile service into `~/Library/Services`.                                                       | `false`         |

| `--input`        | [UTI]                    | Description                        |
|:-----------------|:-------------------------|:-----------------------------------|
| `text`           | `public.utf8-plain-text` |                                    |
| `rtf`            | `public.rtf`             | [Rich Text Format][rtf] documents. |
| `url`[`s`]       | `public.utf8-plain-text` |                                    |
| `address`[`es`]  | `public.utf8-plain-text` |                                    |
| `phone`/`tel`    | `public.utf8-plain-text` |                                    |
| `date`[`s`]      | `public.utf8-plain-text` |                                    |
| `email`/`mailto` | `public.utf8-plain-text` |                                    |
| `item`[`s`]      | `public.item`            | Files or folders.                  |
| `folder`[`s`]    | `public.folder`          |                                    |
| `document`[`s`]  | `public.content`         |                                    |
| `pdf`[`s`]       | `com.adobe.pdf`          |                                    |
| `image`[`s`]     | `public.image`           |                                    |
| `movie`[`s`]     | `public.movie`           |                                    |
| `audio`[`s`]     | `public.audio`           |                                    |
| `web`            | `com.apple.webarchive`   |                                    |
| `no`[`ne`]       |                          | Workflow receives no input.        |

Examples
--------
~~~ sh
serve ace.* --input text --icon src/deuce.svg
# ~/Library/Services/Ace.workflow/Contents/QuickLook/Thumbnail.png
# Services > Ace
serve us-open.sh --name "US Open" --app finder --install
# Finder > Services > US Open
serve double-fault.rb -i folders -a com.apple.finder
# Double Fault.workflow
~~~

Install
-------
with _[Homebrew]_:
~~~ sh
brew tap danielbayley/services
brew install serve
~~~

Development
-----------
~~~ sh
git clone https://github.com/danielbayley/serve
cd serve
brew bundle install
~~~

License
-------
[MIT] © [Daniel Bayley]

[MIT]:                LICENSE.md
[Daniel Bayley]:      https://github.com/danielbayley

[service]:            https://support.apple.com/guide/mac-help/mchlp1012
[contextual]:         https://developer.apple.com/macos/human-interface-guidelines/menus/contextual-menus
[uti]:                https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/UTIRef/Articles/System-DeclaredUniformTypeIdentifiers.html#//apple_ref/doc/uid/TP40009259-SW1

[rtf]:                https://en.wikipedia.org/wiki/Rich_Text_Format

[SVG]:                https://developer.mozilla.org/docs/Web/SVG
[`icns`]:             https://en.wikipedia.org/wiki/Apple_Icon_Image_format
[finder thumbnail]:   https://osxdaily.com/2007/03/13/how-to-get-image-thumbnail-icons-in-the-os-x-finder

[homebrew]:           http://brew.sh
[CLI]:                man.md
