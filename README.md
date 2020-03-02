# babashka.curl

A tiny [curl](https://curl.haxx.se/) wrapper via idiomatic Clojure, inspired by [clj-http](https://github.com/dakrone/clj-http#philosophy), [Ring](https://github.com/ring-clojure/ring) and friends.

This library may end up in [babashka](https://github.com/borkdude/babashka/) but for now it can be used as a library.

## Status

Work in progress, early days, far from finished. Breaking changes will happen. Contributions welcome.

## Usage

``` clojure
(require '[babashka.curl])

(curl/get "https://httpstat.us/200")
;;=> "200 OK"

(curl/get "https://httpstat.us/200" {:headers {"Accept" "application/json"}})
;;=> "{\"code\": 200, \"description\": \"OK\"}"
```

Passing raw arguments to `curl` can be done with `:raw-args`:

``` clojure
(curl/post "https://postman-echo.com/post"
                  {:body "From Clojure"
                   :raw-args ["-D" "-"]})
;;=> "HTTP/1.1 200 OK\r\nContent-Type: application/json; ..."
```

## Test

``` clojure
$ clj -A:test
```

## License

Copyright © 2020 Michiel Borkent

Distributed under the EPL License, same as Clojure. See LICENSE.