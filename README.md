# kasa - [figma link](https://www.figma.com/file/7nSuhkrcrSKtzuAlOSAeRf/Card-component?node-id=3%3A55)

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

## The card component:

---

<br />

```html
<Card
  size="xl"
  hideCover
  thumbnailTop
  hideAvatar
  :cardTextContent="{
    url: require('@/assets/room.svg'),
    title: 'Card Title',
    subtitle: 'Card Subtitle'
  }"
>
  <template #body>
    <div>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
      tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
      veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
      commodo consequat.
    </div>
  </template>
  <template #footer>
    Card footer
  </template>
</Card>
```

#### Optional props:

1. `size` (string): The size of the card (`regular` emply / `l` or `L` / `xl` or `XL`).
2. `cardTextContent` (object):
   1. `url` (string): The image url.
   2. `title` (string): The text of the title.
   3. `subtitle` (string): The text of the subtitle.
3. `thumbnailTop` (boolean default: false): The position of the thumbnail.
4. `hideCover` (boolean default: false): In order to display/hide the cover image.
5. `hideAvatar` (boolean default: false): In order to display/hide the avatar image.

#### Slot options:

1. `body`: The content of the card body \
   (it can contain anything: text, button, link, etc.)

```html
<template #body>
  <!-- content -->
</template>
```

2. `footer`: The content of the card footer \
   (it can contain anything: text, button, link, etc.)

```html
<template #footer>
  <!-- content -->
</template>
```

\*\* In case of added click event to one of the slot the `@click` then the trigger needs to be `@click.stop`.
