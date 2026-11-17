# List Rendering

## v-for

Mit v-for können Listen angezeigt werden.

## Beispiel

```js
const fruits = [
  'Apple',
  'Banana',
  'Orange'
]
```

```html
<li v-for="fruit in fruits">
  {{ fruit }}
</li>
```

## Index

```html
<li v-for="(fruit, index) in fruits">
  {{ index + 1 }}. {{ fruit }}
</li>
```

## key

```html
<li
  v-for="fruit in fruits"
  :key="fruit"
>
```

key hilft Vue die Elemente eindeutig zu erkennen.

## Eigene Notizen

- v-for wird für Listen verwendet
- item = aktuelles Element
- items = komplette Liste
- oft zusammen mit key
