# Studio Blocks — real interfaces, not generic motion

The `studio` theme (the default) follows four reference Shorts that perform well (in
`Downloads/IMPROVE MY VIDEOS`): a Claude Code plugin explainer, an AirTag/Find My explainer, a
solo-founder productivity piece and a Luhn check-digit explainer. **Read this file before writing a
shot list for any studio video.** `scene-blocks.md` still covers transitions, sound and the older
blocks.

---

## What the references do (and the old videos didn't)

| Reference habit | What it means for every shot |
|---|---|
| **The thing itself is on screen.** A card number sits on a VISA card above a checkout form; a task list is an app window with real rows, times and tags; a plugin install is a real terminal. | Every product, app, service or action that is named gets a **faithful replica of its interface**. WhatsApp is a WhatsApp chat. M-Pesa is the M-Pesa SMS. Never an icon and a word. |
| **The spoken line is the headline.** Top of frame, words appear as they're said, the newest dark, the rest grey, one keyword in a selection box with handles, sometimes an emoji. | The studio template does this automatically from `words.js`. Mark 1 keyword per sentence with `key(t, "emoji?")`. No bottom caption box. |
| **One stage, many beats.** A scene holds 5–15 s while things change *inside* it: rows highlight, bars fill, a number counts, a status chip flips, the camera pushes into one element. Hard cuts are rare (0–14 per video). | Build chapters, not 30 separate shots. Aim for **one stage per idea**, 6–12 stages a minute, each with a change every 1–2 s. |
| **The interface is used.** A cursor clicks Merge, a checkbox ticks, a message arrives, a field turns red with "Invalid card number". | Every stage has at least one interaction: `click`, `check`, `msg`, `notify`, `fill`, `typer`, `counter`, `label`, `select`. |
| **Real-looking data.** `48,120 tokens · 404 lines written`, `Refactor invoice.ts · 20 min · easy`, `4539 1488 0343 6467`, `Ksh 1,250.00`. | Invent plausible, specific data that fits the narration and list it as invented in the report. Never lorem ipsum, never "Item 1". |
| **Focus by dimming.** The one row that matters stays bright; everything else drops to 20 % and blurs. | `focus(sel, others, t)`, then `unfocus`. Pair with `select()` for the keyword. |
| **Persistent orientation.** Step pills (`Double · Add digits · Total · Ends in 0`) or a status chip (`OFFLINE → BROADCASTING → REPORTED`) stay on screen and advance. | For any process with steps, put a **steps bar** or **status chip** in a section that spans the whole explanation. |
| **Light and bright, dark for drama.** Off-white grid paper most of the time; a dark scene with a soft accent glow for the "here's the twist" beat. | Default light. Add `class="shot dark"` for 1–3 contrast beats. Captions switch to light automatically. |
| **A real ask at the end.** "Comment RIP and I'll send it to you" shown as a comment thread with the word being typed; "Save this" with a bookmark. | End on a **comment CTA** or **save CTA** block, not a logo slam. |

### Banned (reads as generic)

- An icon or logo with one word under it, used to stand in for an app. Show the app.
- Floating shapes, orbs, particles, abstract node networks — unless the topic *is* a graph.
- More than two full-frame word slams in a video. The headline captions already carry the words.
- A stock photo of "a person on a phone" when you could show the phone's screen.
- Shaking the camera on every hit. The studio theme keeps shake at 0.25 and flash off.

---

## Topic → interface lookup

Build the replica with the UI kit below. Use the real product's layout, colours and microcopy;
don't put the company's logo on things it didn't make.

| Mentioned | Show |
|---|---|
| WhatsApp, chats, groups, read receipts | Phone → WhatsApp chat (green `#008069` header, beige doodle wallpaper, `#d9fdd3` outgoing bubbles, blue ✓✓, the yellow 🔒 encryption notice) or the chat list with green unread badges |
| M-Pesa, mobile money, Fuliza, paybill, till | Phone → SMS thread from **MPESA**: `QJK7XY12AB Confirmed. Ksh1,250.00 sent to JANE WANJIKU 0712 345 678 on 25/10/26 at 9:41 AM. New M-PESA balance is Ksh3,480.50. Transaction cost, Ksh13.00.` Plus the STK push prompt "Enter M-PESA PIN" |
| Bank card, payments, checkout | Card visual + checkout form (`field-in`, `btn`), red invalid state, green success |
| An app's notifications | Lock-screen `notif` banners stacking |
| Code, CLI, installs, AI coding tools | `term` window with prompt, command, real-looking output, progress bar |
| AI chat (ChatGPT, Claude, Gemini) | Chat window: user bubble right, assistant text left, typing dots, the model name in the title bar |
| Websites, Google, sign-ups | `win browser` with the URL pill, the page's real structure (search box and results, form) |
| Email | Inbox window: sender rows with bold unread, subject, preview, time |
| Spreadsheets, budgets | Window with a grid, a formula bar, cells filling in |
| Social posts (X, Instagram, TikTok) | The post card: avatar, handle, text, counts ticking up |
| Settings, privacy toggles | iOS-style settings list with switches flipping |
| Maps, delivery, location | A map card (grid streets in CSS), a pin dropping, a route drawing |
| Stats, money, growth | A `ui-card` with a `num` counter and a bar or line chart — inside the app it came from where possible |
| A person or company | Photo (`find_media.py`), then their product's interface |

---

## UI kit (studio theme)

Every class below lives in `themes/studio.css`. Sizes are for vertical 1080x1920; the stage is
y = 360…1780 (headline above, handle below).

### Phone + WhatsApp chat
```html
<section class="shot" id="s03"><div class="stage" id="s03st">
  <div class="phone" style="left:230px;top:400px"><div class="island"></div><div class="screen">
    <div class="statusbar wa-sb"><span>9:41</span><span class="sig"></span></div>
    <div class="wa-head"><span class="back">←</span><div class="avatar" style="background:#e17055">M</div>
      <div class="who"><b>Mum</b><small id="s03who">online</small></div><span class="icons">📹📞</span></div>
    <div class="wa"><div class="wa-msgs">
      <div class="wa-lock">🔒 Messages and calls are end-to-end encrypted. No one outside of this chat can read them.</div>
      <div class="wa-out" id="s03m1">Did you get the money? <span class="wa-meta">9:41<span class="tk read">✓✓</span></span></div>
      <div class="wa-in typing" id="s03dots"><i></i><i></i><i></i></div>
      <div class="wa-in" id="s03m2">Yes! Just came in 🙏 <span class="wa-meta">9:41</span></div>
    </div><div class="wa-input"><div class="field">🙂 <span>Message</span></div><div class="mic">🎤</div></div></div>
  </div></div>
</div></section>
```
```js
shot("s03", 8.0, 15.2);
msg("#s03m1", 8.6);
label("#s03who", [[0,"online"],[9.4,"typing…"],[10.3,"online"]]);
msg("#s03m2", 10.3, "#s03dots");          // dots show 0.9s before the reply lands
select("#s03m2", 11.0, "delivered");
zoomTo("#s03st", "#s03m2", 12.0, .8, 1.5); // push in on the reply
```
Chat list: `.wa-row` rows (avatar, `.txt` with `<b>` name and `<span>` last message, `.side` time and `.n` unread badge) inside `.screen`.
Read receipts: `.tk` grey ✓✓, add `read` for blue — `addClass("#s03m1 .tk","read",11.5)` flips them on cue.

### Phone + SMS (M-Pesa)
```html
<div class="screen"><div class="statusbar"><span>9:41</span><span class="sig"></span></div>
  <div class="sms-head"><div class="avatar" style="background:#4cae4c">M</div>MPESA</div>
  <div class="sms"><div class="sms-msgs">
    <div class="sms-time">Today 9:41 AM</div>
    <div class="sms-in" id="s05sms"><b>QJK7XY12AB</b> Confirmed. Ksh1,250.00 sent to JANE WANJIKU 0712345678 on 25/10/26 at 9:41 AM. New M-PESA balance is Ksh3,480.50.</div>
  </div></div></div>
```

### Notification
```html
<div class="notif" id="s06n" style="left:70px;right:70px;top:420px">
  <div class="app">💬</div><div class="txt"><div class="top"><span>WHATSAPP</span><span>now</span></div><b>Mum</b><p>Yes! Just came in 🙏</p></div></div>
```
```js
notify("#s06n", 18.2);
```

### App window, browser, terminal
```html
<div class="win" id="s07w" style="left:70px;right:70px;top:420px">
  <div class="win-bar"><i></i><i></i><i></i><span class="title">Today · Paperkite</span></div>
  <div class="win-body">
    <div class="row" id="s07r1"><span class="box" id="s07b1"></span><span class="grow">Refactor invoice.ts</span><span class="meta">20 min</span><span class="tag">easy</span></div>
    <div class="row" id="s07r2">…</div>
  </div></div>
<div class="win browser" style="…"><div class="win-bar"><i></i><i></i><i></i><span class="url">safaricom.co.ke/mpesa</span></div>…</div>
<div class="term" style="left:70px;right:70px;top:1180px"><div class="bar"><i></i><i></i><i></i>&nbsp;zsh</div><pre id="s07pre"></pre></div>
```
```js
stagger("#s07w .row", 20.1);            // rows land one by one
check("#s07b1", 21.0);                  // tick + ding
focus("#s07r2", "#s07w .row", 22.0);    // dim the rest
terminal("#s07pre", [{t:23,e:23.8,html:"<span class='p'>❯</span> npm i ponytail\n"},{t:24,e:24,html:"<span class='ok'>✓ added 1 package</span>\n"}]);
```
Add `dark-ui` to a `.win` for a dark app window on a light stage.

### Form with validation
```html
<div class="ui-card" style="left:110px;right:110px;top:520px">
  <div class="label">CARD NUMBER</div>
  <div class="field-in" id="s08f" style="margin:12px 0 20px"><span id="s08t"></span><span class="caret"></span></div>
  <div class="btn" id="s08btn">Pay Ksh 1,250</div></div>
```
```js
typer("#s08t", "4539 1488 0343 6467", 30.2, 31.6);
click("#s08btn", 32.0);
addClass("#s08f", "bad", 32.2); SFX.push({t:32.2,type:"error"});
```

### Steps bar (persistent)
A section that spans the whole process, placed **after** the scenes it overlays so it sits on top:
```html
<section class="shot" id="steps"><div class="pills" style="top:330px">
  <div class="pill" id="p1"><i>1</i>Dial *334#</div><div class="pill" id="p2"><i>2</i>Enter PIN</div><div class="pill" id="p3"><i>3</i>Confirm</div></div></section>
```
```js
shot("steps", 40.0, 58.0, "fade");
addClass("#p1","on",40.2); addClass("#p1","done",45.0); addClass("#p2","on",45.0); …
```
When the steps bar is on, move the stage content down ~80px so it clears the headline.

### Status chip (persistent)
```html
<div class="chip" id="s09chip" style="left:70px;top:1660px">OFFLINE</div>
```
```js
label("#s09chip", [[0,"OFFLINE"],[12.4,"BROADCASTING"],[20.1,"REPORTED"]]);
tl.set("#s09chip",{"--chip":"var(--red)"},0); tl.set("#s09chip",{"--chip":"var(--green)"},20.1);
```

### Stat card / counter
```html
<div class="ui-card" style="left:110px;right:110px;top:600px"><div class="label">SENT THROUGH M-PESA · 2025</div>
  <div class="num" style="font-size:170px"><span class="accent">Ksh</span> <span id="s10n">0</span>T</div>
  <div class="bar g" style="margin-top:20px"><i id="s10bar"></i></div></div>
```
```js
counter("#s10n", 0, 38.3, 50.1, 51.4, true, 1); fill("#s10bar", 82, 50.1, 51.4); hit(51.4,.5);
```

### Compare (before / after, with / without)
Two `.ui-card`s stacked: the bad one with a red `.bar.r` and a red `tag`, the good one with a green border
(`style="outline:3px solid var(--green)"`), a green bar and the win stated in data (`22,100 tokens · 1 line`).
Then a large `stat` like **−54 %** popping in beside them.

### Selection, spotlight, cursor
- `select("#el", t, "label?")` — accent box with corner handles around any element (the reference
  "Figma selection" look). Use it on the exact word, number or row being talked about.
- `focus(sel, others, t)` / `unfocus(others, t)` — spotlight.
- `click(sel, t)` — cursor glides to the element and clicks (click sound + ripple). Consecutive clicks
  travel from the last position. `cursorOff(t)` hides it.
- `zoomTo(stage, sel, t, d, scale)` / `zoomOut(stage, t)` — push the camera into one element. The
  shot's content must be wrapped in `<div class="stage">`. Place clicks before a zoom, not during it.

### Quiz / pause-and-guess (engagement)
Ask the viewer something the video then answers: a question card with 2–4 option `row`s, a 3-2-1
`counter` going down, then `focus` + green `check` on the right one. Put it where the narration asks
a question ("so which one is fake?"). Viewers rewatch and comment their guess.

### Comment CTA (end card)
```html
<div class="cmt" id="cta" style="left:110px;right:110px;top:820px">
  <h4>Comments</h4>
  <div class="c"><div class="avatar" style="background:#00b894">J</div><div><b>you · now</b><p id="ctaw"></p></div></div>
  <div class="compose"><span class="grow" id="ctat"></span><span class="send">➤</span></div></div>
<div class="cx display" id="ctak" style="top:560px;font-size:200px"><span class="rel">MPESA</span></div>
```
```js
pop("#cta", 92.0); slam("#ctak", 92.3, .6); select("#ctak .rel", 92.6);
typer("#ctat", "MPESA", 92.8, 93.5); click("#cta .send", 94.0);
typer("#ctaw", "MPESA", 94.1, 94.1);   // the comment posts
```
Only promise something in the CTA that the user actually said they'll send.

### Save CTA
A small card "Save this for later" with a bookmark 🔖 that `pop`s and fills with the accent, the
handle under it. Use when the video is a reference people come back to (steps, codes, shortcuts).

---

## Stage pacing checklist

For every stage in the shot list, write down:
1. **The interface** (which real screen).
2. **The beats** — one interaction every 1–2 s, each tied to a word time.
3. **The keyword** for `key()` in that sentence.
4. **Light or dark.**

If a row in the shot list has no interface and no interaction, it's generic. Redesign it.
