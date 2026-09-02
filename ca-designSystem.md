# Case Amplify design system

**Version:** v2026.09.01
**For:** designers, marketers and content creators building pages on caseamplify.com

---

## 1. Scope

This document explains how to build content. It does not explain how the site is built.

**In scope:** the page-building workflow, the pattern library, what each preset value currently is, image preparation, publishing, and what the block editor will and will not show you.

**Out of scope:** writing CSS, adding new patterns, adding header dropdowns or footer columns, teaching HTML. Those need a developer.

**Related documents:**

| Document | Holds |
|---|---|
| `wave-system.md` | motion internals, the full class token list, why things work the way they do |
| `case-amplify-manifest.md` | terminology, positioning, approved claims, compliance language |

**The governing rule.** Everything is preset. Spacing, responsive behavior, type, color and animation are already correct when a pattern is dropped in. You edit content. If you want to bend a rule, ask Ian rather than working around it.

---

## 2. Standard workflow

### 2.1 Start a page

Two ways in:

- **Duplicate an existing page** and replace the content. Fastest, and page settings come with it.
- **Start clean.** Create the page, then set page settings before adding anything.

Page settings for a clean start:

1. Page layout: **Full width**
2. Page title: **disabled**

### 2.2 Build the page

1. Click the blue **+** in the top left to open the inserter sidebar.
2. Go to **Patterns**, then the category you need.
3. Start with **ca-innerHero**. The paragraph block above the H1 is the eyebrow and already carries its class.
4. Add a **Spacer / Divider** block (Kadence's, not core's). Its values are preset.
5. Add the next pattern. Edit its content.
6. Repeat: spacer, section, spacer, section.

**Think in rows stacked on each other, not in columns.** A section is usually a header/divider row followed by a content row. Column layouts are baked into the patterns and are not an author decision.

**Spacers go between sections, never inside one.**

### 2.3 Composition rules

| Rule | Detail |
|---|---|
| Side agreement | If a header/divider row sits above a content row, the image in that content row goes on the **same side as the heading**. |
| Alternation | Switch the heading side after each section. Not absolute, but the page should vary rather than repeat one side down its whole length. |
| Standalone headings | A header/divider row can stand alone. A single strong statement does not need a content row under it. |
| Centered divider | `ca-divider--center` is a full stop. It closes a chapter. Never open a section with it. |
| One CTA pattern per page | Only one `ca-cta--*` pattern. This does not restrict primary CTA buttons inside other sections. |

### 2.4 Review

Leave the page in **Draft**. Ian or Rob approve before publish. Run the checklist in §8 first.

---

## 3. Foundations

Values below are current, not proposed. The **Owner** column says where each one actually lives, so that when this document and the site disagree you know which to trust.

### 3.1 Type

Owner: Kadence Customizer. Every size is fluid between a 400px and a 1400px viewport.

| Element | Font | Weight | Size | Line height |
|---|---|---|---|---|
| H1 | Literata | 600 | 30 → 58px | 1.1 |
| H2 | Literata | 600 | 26 → 46px | 1.15 |
| H3 | Literata | 600 | 23 → 36px | 1.2 |
| H4 | Inter | 600 | 20 → 29px | 1.3 |
| H5 | Inter | 500 | 18 → 23px | 1.4 |
| H6 | Inter | 400 | 17 → 18px | 1.5 |
| Body | Inter | 400 | 16 → 17px | 1.6 |

**Hero headlines are separate.** They are set in the child theme, not the Customizer, and are larger on purpose.

| Where | Size | Owner |
|---|---|---|
| Homepage hero | 40 → 74px | `ca-hero.css`, `--ca-h1` |
| Inner page hero | 34 → 58px | `ca-base.css`, `.p-hero h1` |

**Eyebrow.** IBM Plex Mono, 12px, letter-spacing 0.08em. Owner: `ca-base.css`, `.eyebrow`. Already applied inside the patterns that use one. Adding your own is advanced work; see §10.4.

**Adv highlight.** Colors inline text purple. Use it on one word in a heading. Two is the maximum, and if you use two, resize the window and check they do not get split across a line break. Reach it from the toolbar: the arrow to the right of the link button, then **Adv highlight**.

### 3.2 Color

Owner: `ca-base.css` `:root` for everything built as a custom code block. The Kadence palette covers theme blocks separately, and the two are not currently reconciled (see §11).

| Token | Value | Use |
|---|---|---|
| `--paper` | `#FFFFF8` | page background |
| `--ink` | `#11111C` | headings |
| `--body` | `#3A3A44` | body copy |
| `--hair` | `#C1C1B8` | rules and dividers |
| `--grape` | `#8D16D4` | highlights and accents |
| `--grape-1` | `#CE08F2` | gradient start |
| `--grape-2` | `#8F15D5` | gradient end |
| `--footer` | `#080612` | footer background |
| `--f-head` | `#CFCEC2` | footer headings |
| `--f-link` | `#90908D` | footer links |

You do not need to set colors. Nothing in the pattern library requires it.

### 3.3 Layout

| Value | Setting |
|---|---|
| Content width | 1400px |
| Grid | 12 columns, 20px gutter |
| Edge padding | 1rem desktop |
| Stacking breakpoint | 1024px |

### 3.4 Buttons

| Style | Appearance | Use |
|---|---|---|
| Theme base | purple gradient fill, 10px radius | the primary CTA in a section |
| Outline | text and border, no fill | any secondary CTA |

Add and remove buttons where the content needs them. One primary per section.

**Labels describe the destination.** Say where the reader is going, not that they should go.

**New tab** only when the link leaves the site — including `trust.caseamplify.com` — or opens a non-lightbox video, or when there is a specific reason to keep the current page open. Internal links stay in the same tab.

### 3.5 Icons

From the Phosphor library. Reach them at **Style > Icon Settings** in the right sidebar.

| Weight | Use |
|---|---|
| Filled | theme base CTA buttons only |
| Line | cards and secondary CTA buttons |

---

## 4. Pattern library

All patterns are **unsynced**. Editing one on a page does not affect any other page. Every pattern arrives with its data attributes, animation classes and image effect classes already in the right places.

### 4.1 Inventory

**Naming reads left to right in visual order.** `ca-header/divider` puts the heading on the left; `ca-divider/header` puts it on the right. `ca-image/content` puts the image on the left; `ca-content/image` puts it on the right.

| Pattern | Use |
|---|---|
| `ca-innerHero` | top of every inner page |
| `ca-header/divider` | section heading, left, with animated rule |
| `ca-divider/header` | section heading, right, with animated rule |
| `ca-header/text` | section heading with body copy |
| `ca-divider--center` | full stop at a chapter boundary |
| `ca-image/content` | image left, copy right |
| `ca-content/image` | copy left, image right |
| `ca-3cards/content` | three cards with supporting copy |
| `ca-content/cards--dark` | copy with cards on a dark field |
| `ca-4cards` | four cards |
| `ca-hoverCards` | expanding panels; see §5.3 |
| `ca-iconStrip` | row of icons |
| `ca-FAQ` | question and answer list |
| `ca-cta--contact` | closing CTA to the contact page |
| `ca-cta--resources` | closing CTA to the resources page |

### 4.2 Spacers

Kadence's **Spacer / Divider** block, preset. One between each section. None inside a section.

---

## 5. What the components do

You do not place these. They are already inside the patterns. This section exists so you recognize them and know what you are looking at.

### 5.1 Section rules

The animated line beside a section heading. It draws as you scroll past it, peaking when it reaches the middle of the screen.

Two roles, one mark:

- **Opener** — asymmetric, sits beside a heading, opens a section.
- **Full stop** — centered, stands alone, closes a chapter.

You can drag the divider's column width when the heading wraps awkwardly and leaves a gap. Only on header/divider combinations, and only a little.

### 5.2 Content rise

Content fades and lifts into place as it enters the screen. Every pattern already carries the right variant.

| Class | Motion | For |
|---|---|---|
| `ca-rise` | fade and 22px up | the default |
| `ca-rise--soft` | fade only | dense text |
| `ca-rise--lift` | 46px, slower | a few large feature cards |
| `ca-rise--settle` | fade and slight scale | media |
| `ca-rise--sweep` | from the left, wide stagger | an accent, at most once per screen |

Applied to a **row**, the sections inside stagger. Applied to a **section**, the blocks inside stagger. They can be combined.

### 5.3 Panels (`ca-hoverCards`)

Panels show less at once on purpose. By default only the image and heading are visible. Hovering, or tapping on mobile, expands a panel to reveal the rest of the text while the others shift out of the way.

Currently four panels only. Two and three panel versions may come later. Nothing restricts where they are used, though at present they appear only on the homepage. Editing them is advanced work; see §10.

### 5.4 Image effects

`ca-fade` softens the bottom edge of an image into the page. `ca-shadow` sits on its wrapper and lifts it off the page. Both are already applied inside the patterns that need them.

They are already correct wherever they appear. Applying them yourself is advanced work; see §10.4.

---

## 6. Images

### 6.1 Shape

| Where | Orientation |
|---|---|
| Content rows and panels | landscape |
| Heroes | vertical |

No aspect ratio is off limits. Avoid getting close to square.

### 6.2 File preparation

Format is **WebP**. Prepare files before upload using https://squoosh.app/:

1. Drop the image in.
2. Under **Compress**, choose WebP.
3. Optional: toggle **Resize** and reduce the percentage.
4. Drag the slider in the center to compare before and after. Stop before visible clarity is lost.

### 6.3 Alt text

Add alt text when the image goes into the media library, at the same time you file it into its folder. Do it once, there, and standard image blocks pull it automatically.

**Decorative images do not get alt text.** Background patterns, textures and ornaments stay empty.

Images inside custom HTML blocks are the exception: they do not inherit alt text and you have to paste it in by hand. See §10.

---

## 7. Menus

| Menu | Controls |
|---|---|
| `ca-header1` | first header dropdown |
| `ca-header2` | second header dropdown |
| `ca-footer1` | footer link column 1 |
| `ca-footer2` | footer link column 2 |
| `ca-footer3` | footer link column 3 |
| `ca-footer4` | footer link column 4 |

Editing the pages inside one of these menus changes what appears in that dropdown or column on the live site. That is the whole of what an author needs.

**Adding a new dropdown or a fifth footer column is out of scope.** It requires PHP work. Ask a developer.

The header and footer themselves are not editable from the page editor and should be left alone.

---

## 8. Publishing checklist

Before handing a page to Ian or Rob:

- [ ] Page layout is Full width
- [ ] Page title is disabled
- [ ] No page parent. Every page sits at the root
- [ ] Slug is the page name in lowercase with hyphens, e.g. `/vocational-rehabilitation`
- [ ] SEO title and description written for this page's content
- [ ] Featured image is the hero image
- [ ] All images are WebP and have alt text, or are deliberately decorative
- [ ] One `ca-cta--*` pattern, no more
- [ ] Spacers between every section, none inside a section
- [ ] Heading sides alternate down the page
- [ ] Images sit on the same side as the heading above them
- [ ] Highlighted words do not break across lines at any window width
- [ ] External links open in a new tab, internal links do not
- [ ] Status is Draft

---

## 9. What to expect in the block editor

The editor shows structure. It does not show the finished page. **Everything in this section is normal and none of it needs fixing.**

| In the editor | On the live site |
|---|---|
| Dividers do not draw | they draw and animate on scroll |
| Panels, CTA sections and other custom blocks show as raw HTML | fully styled |
| Eyebrow text looks like ordinary paragraph text | monospace, small, letter-spaced |
| Images have no gradient fade or shadow | both applied |
| Nothing rises or animates in | content staggers in on scroll |
| The homepage hero looks like a mess of unstyled markup | correct |
| Header and footer do not render at all | present |

**Do not judge spacing in the editor.** It is preset and it is not what you are seeing.

The one thing you can adjust visually is divider width, using the draggable column handle, when heading wrap leaves an awkward gap.

---

## 10. Advanced editing

Everything here involves touching HTML. It is optional, and none of it is required for standard page building.

### 10.1 Before you start

**Save your work.** Then start editing.

Reading HTML is not covered here. If you cannot find what you need, paste the block's code into an AI assistant and ask where the thing you want to change is.

**Add CSS classes only. Never write CSS.** If a block needs styling that does not exist, that is a request to Ian, not something to solve in the page.

### 10.2 Editing text inside a custom block

Find the tag, change the text between the tags.

To find it fast: copy the current text off the page, open the custom HTML block, press **Ctrl + F** and paste. It will jump straight to the line.

### 10.3 Replacing an image inside a custom block

1. Upload the image to the **media library** and set its alt text there. Never link to an image hosted anywhere else.
2. Copy the media library URL into the block.
3. Copy the alt text from the media library and paste it into the `alt` attribute by hand.

Step 3 is the one that gets missed. A standard image block pulls alt text automatically. A custom-coded image does not, and will ship with none.

### 10.4 Adding classes

**Advanced > Advanced > Additional CSS class(es)**, in the right sidebar.

No leading dot. Type `ca-rise--soft`, not `.ca-rise--soft`.

| Applied to | Effect |
|---|---|
| A row | the sections inside it stagger |
| A section | the blocks inside it stagger |

Both at once is allowed and the nesting resolves correctly.

Available classes include `ca-rise` and its variants (§5.2), `ca-fade` and `ca-shadow` (§5.4), and `eyebrow` (§3.1). The full token list is in `wave-system.md`.

Every pattern already carries a `ca-rise` variant. Change it only if you have a specific look in mind, and check the result on the live page rather than in the editor.

**`eyebrow`** turns a plain paragraph block into a section eyebrow. Nothing else is needed.

**`ca-fade` and `ca-shadow` go on two different elements.** The fade on the image, the shadow on its wrapper. Both on one element and the shadow silently does nothing, with no error to tell you.

### 10.5 Highlighting a word in a CTA heading

CTA sections are custom blocks, so the Adv highlight tool is not available in them. Wrap the word in `<em>` tags instead:

```html
<h2>Bring <em>clarity</em> to every case</h2>
```

Every CTA section ships with those tags already in place. Move them onto the word you want purple, or delete the tags if you do not want a highlight. Do not leave them wrapped around whatever text happened to be there in the default copy.

The one-word rule from §3.1 still applies. Two words at most, and check they do not split across a line break at any window width.

---

## 11. Open items

Known gaps, recorded so they are not rediscovered.

- **Color lives in two places.** Custom code blocks read `ca-base.css` `:root`; Kadence blocks read the Customizer palette. The two are not synchronized and hold different purples. One source is the goal. No action for authors.
- **Panels are four only.** Two and three panel variants are possible future work.
- **Full width is a manual step** because the site default page layout is set to narrow. Changing that default would remove a checklist item.

---

## Getting help

Anything that needs new CSS, a new pattern, a new header dropdown, a new footer column, or a rule bent: ask Ian.
