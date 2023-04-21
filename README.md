# Emmy CAS as JavaScript Module
This repository is very small and only contains the shadow-cljs configuration to compile the [Emmy code repository](https://github.com/mentat-collective/emmy).

To build the Emmy module and start a web server, type (you need [Shadow-cljs](https://shadow-cljs.github.io/docs/UsersGuide.html)):
```
emmy-module$ shadow-cljs watch emmy-esm
```

then open in the browser: http://localhost:9000/index.html (there is also scheme160.html and barebones.html, see below)

`index.html` shows how all the parts technically fit together. To gain further insight on what the shown examples mean, look at this [blog post](https://kloimhardt.github.io/blog/hamiltonmechanics/2023/03/20/up-compose.html).

A technical note: in `index.html`, Scheme code is transpiled and executed as JavaScript. For this, we had to patch the JavaScript `eval` function.

```
<script>
     var oldEval = window.eval;
     var newEval = (txt) =>
        txt.substr(0, 2) === ";("
        ? "Transpiled JS: " + expressionToJs(txt.substr(1))
        : txt[0] === "(" && txt[txt.length - 1] != " "
        ? "AST: " + textToJson(txt)
        : txt[0] === "("
        ? oldEval(expressionToJs(txt))
        : txt[txt.length - 1] != ";"
        ? "Add ; to JS: " + txt
        : oldEval(txt);
     window.eval = newEval;
</script>
```

This patch achieves: 1. the code is transpiled and executed whenever the text starts with a ´(´ and ends with a ´blank´ 2. the transpiled code is shown when the text starts with ´;´ 3. the text is executed as JS when it starts with some letter and ends with a ´;´.

You can also produce the release version of the Emmy module (start your own local web-server to open `ìndex.html`).

```
emmy-module$ shadow-cljs release emmy-esm
```

`scheme160.html` shows all examples of part one of the SICM book. For further explanations, look at the [same examples](https://kloimhardt.github.io/blog/html/sicmutils-as-js-book-part1.html) executed with Sicmutils, the predecessor of Emmy. Note that in this older version, Sicmutils is not a JavaScript module but a simple script.

`barebones.html` tests the state-advancer function of Emmy.
