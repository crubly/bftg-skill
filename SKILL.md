---
name: bftg-skill
description: Use this catalog when replacing ordinary emoji with Telegram premium custom emoji in bot messages/keyboards, or when changing reply keyboard button colors via Telegram Bot API. Triggers on: tg-emoji, custom emoji id, icon_custom_emoji_id, premium emoji, telegram bot button color, KeyboardButton color.
---

# Telegram Premium Emoji Catalog

Use this catalog when replacing ordinary emoji in Telegram bot messages and keyboards.

## Message Format

Use:

```html
<tg-emoji emoji-id="ID">fallback</tg-emoji>
```

Example:

```html
<tg-emoji emoji-id="5870982283724328568">⚙️</tg-emoji> Settings
```

## Keyboard Button Format

Use `icon_custom_emoji_id` and keep `text` free of ordinary emoji:

```python
InlineKeyboardButton(
    text="Subscribe",
    url=CHANNEL_LINK,
    icon_custom_emoji_id="6039450962865688331",
)
```

## IDs

| Meaning | Fallback | custom emoji ID |
| --- | --- | --- |
| Settings | ⚙️ | `5870982283724328568` |
| Profile | 👤 | `5870994129244131212` |
| People | 👥 | `5870772616305839506` |
| Person with check | 👤 | `5891207662678317861` |
| Person with cross | 👤 | `5893192487324880883` |
| File | 📁 | `5870528606328852614` |
| Smiling face | 🙂 | `5870764288364252592` |
| Growth chart | 📊 | `5870930636742595124` |
| Stats chart | 📊 | `5870921681735781843` |
| House | 🏘 | `5873147866364514353` |
| Locked | 🔒 | `6037249452824072506` |
| Unlocked | 🔓 | `6037496202990194718` |
| Megaphone | 📣 | `6039422865189638057` |
| Check mark | ✅ | `5870633910337015697` |
| Cross mark | ❌ | `5870657884844462243` |
| Pen | 🖋 | `5870676941614354370` |
| Trash bin | 🗑 | `5870875489362513438` |
| Down | 📰 | `5893057118545646106` |
| Paperclip | 📎 | `6039451237743595514` |
| Link | 🔗 | `5769289093221454192` |
| Info | ℹ | `6028435952299413210` |
| Bot | 🤖 | `6030400221232501136` |
| Eye | 👁 | `6037397706505195857` |
| Hidden | 👁 | `6037243349675544634` |
| Send | ⬆ | `5963103826075456248` |
| Download | ⬇ | `6039802767931871481` |
| Notification | 🔔 | `6039486778597970865` |
| Gift | 🎁 | `6032644646587338669` |
| Clock | ⏰ | `5983150113483134607` |
| Celebration | 🎉 | `6041731551845159060` |
| Font | 🔗 | `5870801517140775623` |
| Write | ✍ | `5870753782874246579` |
| Media photo | 🖼 | `6035128606563241721` |
| Location pin | 📍 | `6042011682497106307` |
| Wallet | 👛 | `5769126056262898415` |
| Box | 📦 | `5884479287171485878` |
| Crypto bot | 👾 | `5260752406890711732` |
| Calendar | 📅 | `5890937706803894250` |
| Tag | 🏷 | `5886285355279193209` |
| Time elapsed | 🕓 | `5775896410780079073` |
| Apps | 📦 | `5778672437122045013` |
| Brush | 🖌 | `6050679691004612757` |
| Add text | 🔡 | `5771851822897566479` |
| Resize/format | ↔ | `5778479949572738874` |
| Money | 🪙 | `5904462880941545555` |
| Send money | 🪙 | `5890848474563352982` |
| Receive money | 🏧 | `5879814368572478751` |
| Code `</>` | 🔨 | `5940433880585605708` |
| Loading | 🔄 | `5345906554510012647` |
| Back | ◁ | no provided ID; use only as button text/symbol if no custom ID exists |

## Provided Button Examples

Use these IDs when matching existing subscription/check buttons if the project uses them:

| Button | custom emoji ID |
| --- | --- |
| Subscribe | `6039450962865688331` |
| Check subscription | `5774022692642492953` |

## Reply Keyboard Button Colors (Bot API)

Reply keyboard buttons can carry a color hint through the button's custom emoji icon, not through a separate "color" field — Telegram Bot API has no dedicated per-button color parameter. Color is achieved indirectly by attaching one of these color-coded custom emoji as `icon_custom_emoji_id` (or inline as `<tg-emoji>` in text) so the button icon renders in that hue:

| Color | custom emoji ID |
| --- | --- |
| Blue | `5373141891321699086` |
| Red | `5370810157871667232` |
| Green | `5471984997361523302` |

**Don't push color everywhere.** Color a button only where accent actually helps (e.g. destructive "Delete"/"Cancel" in red, confirm action in green). Leave other buttons without color icon, plain text.

## Replacement Checklist

- Messages: ordinary emoji becomes `<tg-emoji emoji-id="...">emoji</tg-emoji>`.
- Inline keyboards: remove emoji from `text`; add `icon_custom_emoji_id`.
- Reply keyboards: remove emoji from `text`; add `icon_custom_emoji_id` in each button object. Apply color IDs sparingly, only for buttons that need visual emphasis.
- Alerts and short answers: use premium emoji only if Telegram HTML/custom emoji is supported in that surface; otherwise prefer text without ordinary emoji.
