# Local PDF form sorter

Open `quire.html` in Chrome or Edge. It groups PDFs that are the same form, then different template versions, then suggests a filename from the fields you map.

Nothing is uploaded. Files stay on your computer.

## Use it

1. Download this repo, or just save `quire.html`.
2. Open `quire.html` in Chrome or Edge.
3. **Open folder** (so it can rename in place) or **Add PDFs**.
4. **Run pipeline**.
5. Open a group. On a phone, use the **Map** tab. On a wide screen, the map is the right column.
6. Tap **Last name**, **First name**, **Date**, or **Case**, then tap the PDF field that holds it. The new name updates for every file in that family.
7. Confirm the group, then **Rename**.

**Guess from field names** fills the obvious slots. If a PDF has no form fields, open **Match page text instead** and use a pattern with parentheses around the value you want.

In-place rename needs the folder picker in Chrome or Edge. If you only dropped files in, Rename downloads a plan instead of changing the files.

## Pin a map in the file

Near the top of the script, `PRESET_MAPS` is a list you can edit:

```js
const PRESET_MAPS = [
  { match: "LastName|FirstName", lastname: "LastName", first: "FirstName", date: "", case: "" },
];
```

`match` is field names that must all exist, separated by `|`. The other keys are the PDF field to use for that part of the filename, or `""` to leave it blank.

## What it clusters on

Cheap signals first: form field names, then header text. Layout hash and line profile only for leftovers. OCR only when a page has almost no text.
