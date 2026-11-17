# Computed Properties

## Was ist computed()?

Computed Properties berechnen Werte automatisch neu, wenn sich abhängige Daten ändern.

## Beispiel

```js
const textColor = computed(() => {
  if (count.value < 5) {
    return 'blue'
  }

  return 'green'
})
```

## Eigene Notizen

- computed ist reaktiv
- wird automatisch aktualisiert
- gut für Farben, Texte und Berechnungen
