# Emmy CAS as JavaScript Module
This repository contains no Clojure code. It is a shadow-cljs configuration to compile Emmy.

To start a web server type:
```
shadow-cljs watch emmy-esm
```

then open in the browser: http://localhost:9000/scheme160.html

You can also produce the release version, but you need to start your own local web-server somehow:
```
shadow-cljs release emmy-esm
```
