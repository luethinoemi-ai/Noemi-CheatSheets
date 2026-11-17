# Reactivity Fundamentals

## ref()

Mit ref() erstellt man eine reaktive Variable.

## Beispiel

```js
const count = ref(0)
```

Wenn sich count ändert, aktualisiert Vue die Oberfläche automatisch.

## Eigene Notizen

- ref() macht Daten reaktiv
- Zugriff im Script mit .value
- Im Template kein .value notwendig
