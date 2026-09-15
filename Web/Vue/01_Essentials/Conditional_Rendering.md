# Conditional Rendering

## v-if

Zeigt ein Element an wenn eine Bedingung wahr ist.

```html
<p v-if="count > 0">
  Hallo
</p>
```

## v-else-if

Weitere Bedingung.

```html
<p v-else-if="count > 5">
```

## v-else

Wird ausgeführt wenn keine Bedingung zutrifft.

```html
<p v-else>
```

## v-show

Element bleibt vorhanden und wird nur versteckt oder angezeigt.

```html
<p v-show="awesome">
  Vue ist awesome
</p>
```

## Eigene Notizen

- v-if erstellt oder entfernt Elemente
- v-show versteckt nur Elemente
- gut für Bedingungen
