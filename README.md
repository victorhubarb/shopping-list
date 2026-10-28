# Shopping List

A shopping list in plain JavaScript. You can add items, check them off to move them to a "purchased" section, rename them, and delete them. Each item shows the day and time it was added or last edited. There is no framework and no build step.

**Live demo:** [shopping-list-two-gamma.vercel.app](https://shopping-list-two-gamma.vercel.app)

## What's inside

Every list item is built in JavaScript with `createElement`, with no HTML template, and the code is split into ES modules with one job each:

| Module | Job |
|---|---|
| `adicionarItem` | Rejects empty input and adds the new item |
| `criarItemDaLista` | Builds an item: custom checkbox, name, edit and delete buttons, timestamp |
| `editarItem` | Renames an item through `prompt`, keeps its checked state, refreshes the timestamp |
| `excluirItem` | Asks for `confirm`, then removes the item |
| `gerarDiaDaSemana` | Formats the date and time in Portuguese (`toLocaleDateString("pt-BR")`) |
| `verificarListaVazia` / `verificarListaComprados` | Show or hide the empty-state message and the purchased section |

The checkbox is a real, hidden `<input>` tied to a `<label for>` with a unique id per item, with the visible box drawn in CSS, so it works with the keyboard and screen readers.

The interface is in Portuguese.

## Run it

ES modules do not load from a `file://` address, so use any local server:

```bash
git clone https://github.com/victorhubarb/shopping-list.git
cd shopping-list
python3 -m http.server 8000     # then open http://localhost:8000
```

## Known gaps

- The list is not saved, so a reload clears it. Storing it in `localStorage` is the natural next step.
- Every item's name element uses the same `id="item-titulo"`, which is invalid HTML, and a class would be the right choice.
- Editing and deleting use the browser's `prompt` and `confirm` dialogs.
- There are no media queries, so the layout is built for desktop-width screens.

---

Victor Hugo Barbosa · [GitHub](https://github.com/victorhubarb) · [LinkedIn](https://www.linkedin.com/in/victorhbarbosa/)
