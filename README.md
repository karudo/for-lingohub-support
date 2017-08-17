# for-lingohub-support


At the very beginning, we have only `app.js`

Then we do
```
xgettext --language=JavaScript --from-code=utf-8 -o app.pot ./app.js
```
for extract phrases to `app.pot`


If we look in app.pot we will see
```
"Plural-Forms: nplurals=INTEGER; plural=EXPRESSION;\n"

#: app.js:3
msgid "%{ count } car"
msgid_plural "%{ count } cars"
msgstr[0] ""
msgstr[1] ""
```

Then we do
```
msginit --no-translator  --locale=en --input=app.pot --output=app.en.po
msginit --no-translator  --locale=ru --input=app.pot --output=app.ru.po
msginit --no-translator  --locale=fr --input=app.pot --output=app.fr.po
```

Look at the resulting .po files
For example in `app.ru.po` we have
```
"Plural-Forms: nplurals=3; plural=(n%10==1 && n%100!=11 ? 0 : n%10>=2 && n"
"%10<=4 && (n%100<10 || n%100>=20) ? 1 : 2);\n"

#: app.js:3
msgid "%{ count } car"
msgid_plural "%{ count } cars"
msgstr[0] ""
msgstr[1] ""
msgstr[2] ""
```

`msginit` automatically adds correct `Plural-Forms` header for language, also automatically adds needed quantity of `msgstr` (for russian we need 3 `msgstr`, because `nplurals=3`)

Can LingoHub do something like this?
