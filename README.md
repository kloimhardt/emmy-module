# Emmy CAS as JavaScript Module
This repository contains the shadow-cljs configuration to compile [Emmy](https://github.com/mentat-collective/emmy). It is not a code repository.

To start a web server type:
```
shadow-cljs watch emmy-esm
```

then open in the browser: http://localhost:9000/index.html

`index.html` shows how all the parts technically fit together. The examples are explained [here](https://kloimhardt.github.io/blog/hamiltonmechanics/2023/03/20/up-compose.html).

You can also produce the release version, you need to start your own local web-server.
```
shadow-cljs release emmy-esm
```

All examples of part one of the SICM book are schown in `scheme160.html`. For further explanations, look at the [same examples](https://kloimhardt.github.io/blog/html/sicmutils-as-js-book-part1.html) executed with Sicmutils, the predecessor of Emmy. Note that in this older version, Sicmutils is not a JavaScript module but a simple script.
