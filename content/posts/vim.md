---
title: "🤷‍♂️ Vim (noob notes)"
date: 2021-11-30T12:00:00+01:00
draft: false
tags: ["vim", "noob notes"]
showtoc: false
---

`Shift - i`: jump to beginning of line and start insert mode

`$`: jump to end of line

## Moving Horizontally Word By Word

- `w` to move word by word
- `b` to move backwards word by word
- `W` to move word by WORD
- `B` to move backwards WORD by WORD

```
type wwww ==> v   v v   v   v
              word. are two words
              word. is one WORD
type WWW  ==> ^     ^  ^   ^
```

- `e` to jump to the end of a word
- `ge` to jup to the end of the previous word

## Move to a Specific Character

- Use `f{character}` (find) to move to the next occurrence of a character in a line.
- Use `F{character}` to find the previous occurrence of a character
- Use `t{character}` to move the cursor just before the next occurrence of a character (think of `t{character}` of moving your cursor until that character).
- Again, you can use `T{character}` to do the same as `t{character}` but backwards

After using `f{character}` you can type `;` to go to the next occurrence of the character or `,` to go to the previous one. You can see the `;` and `,` as commands for repeating the last character search. This is nice because it saves you from typing the same search over and over again.

```
type fdfdfd ==> v   v               v        v
                let damage = weapon.damage * d20();
                let damage = weapon.damage * d20();
type fd;;   ==> v   v               v        v
```

- `0`: Moves to the first character of a line
- `^`: Moves to the first non-blank character of a line
- `$`: Moves to the end of a line
- `g_`: Moves to the non-blank character at the end of a line

```typescript
v                // I've added some extra whitespace at the end
function helloVimWorld() {
  console.log("Hello vim world");
}
// So original Jaime. Your Grandma would be proud.
```

## Moving Vertically

- `}` jumps entire paragraphs downwards
- `{` similarly but upwards
- `CTRL-D` lets you move down half a page by scrolling the page
- `CTRL-U` lets you move up half a page also by scrolling

## High Precision Vertical Motions With Search Pattern

- `/{pattern}` to search forward
- `?{pattern}` to search backwards

```
--------------------------
---v----------------v-----
-----------v---cucumber---
-----v-----------v--------
--------------------------
```

If there's multiple matches of the same pattern you can quickly jump between them using:

- `n` to go to the next match
- `N` to go to the previous match

The `{pattern}` in `/{pattern}` doesn't have to be a string literal. It is a regular expression. Oh the mighty power of regular expressions! e.g. `/## ` to find second level headings in a markdown file.

## Moving Faster With Counts

Counts are numbers which let you multiply the effect of a command:

```
{count}{command}
```

e.g. `2w` to move two words ahead, `5j` to jump file lines below`.

```
type f[;;  ==> vv    v
               [[1], [1, 2], [3]]
               [[1], [1, 2], [3]]
type 3f[  ==>        ^
```

Try jumping to the second cucumber with `2/cuc`:

```
--------------------------
---v--cucumber------v-----
-----------v---cucumber---
-----v-----------v--------
cucumber------------------
```

## And Some More Nifty Core Motions

- Type `gg` to go to the top of the file.
- Use `{line}gg` to go to a specific line.
- Use `G` to go to the end of the file.
- Type `%` jump to matching `({[]})`, i.e. opening and closing bracket.

Try going back to the top of this file with `gg`, then come back with `G`.

And now jump between these two matching brackets until you want to go to sleep:
```typescript
             start here f[%
                 \
                  \
                   v
const bagOfFoods = [["cucumber"], ["tomato", "potato"]];
```