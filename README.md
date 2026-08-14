# Mon book
```dataviewjs
const pages = dv.pages('"book-1"');

dv.table(
    ["Fichier", "Taille", "Auteur", "Rating", "Créé le"],
    pages.map(p => {
        const file = app.vault.getAbstractFileByPath(p.file.path);

        // Si pas de fichier ou pas de stat
        if (!file || !file.stat) {
            return [
                p.file.link,
                "—",
                p.author ?? "—",
                p.Rating ?? "—",
                p.Date ?? "—"
            ];
        }

        const size = file.stat.size;

        // Formatage intelligent
        const displaySize =
            size < 1024
                ? size + " B"
                : size < 1024 * 1024
                    ? (size / 1024).toFixed(1) + " KB"
                    : (size / 1024 / 1024).toFixed(2) + " MB";

        return [
            p.file.link,
            displaySize,
            p.author ?? "—",
            p.Rating ?? "—",
            p.Date ?? "—"
        ];
    })
);

```