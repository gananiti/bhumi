# Bridge URL For A Mantra

https://chatgpt.com/share/68fe5e48-34cc-8000-b3b5-40ef51230c4b

`bhumi://` may not be supported everywhere, so it is better to not share the
mantra full url, but the bridge URL for the mantra. To construct a bridge URL,
you have to find a bridge you trust first, say https://amitu.com/bhumi/ is one
such bridge.

The purpose of the bridge is to connect the @`plain-net` with the @`bhumi-jal`,
which is the peer to peer version of internet that powers bhumi.

You can run your own bridge if you do not trust amitu.com for example, the code
of bhumi is open source, and to deploy it you need minimal setup, just a static
site hosting. You do not even need static site hosting, you can just download
the code of bhumi and run it on your laptop, with no deployment needed, in this
case you local bhumi will have a URL like `http://localhost:<port>`.

So the general format for the bridge URL is `<bridge-url>#<mantra-ref>`, so for
example this mantra that you are studying right now has the bridge url of
`https://amitu.com/bhumi/#bhumi://github.com/gananiti/bhumi/archive/refs/heads/main.zip/mantra-refs`.

The bridge URL can be freely shared on the @`plain-net`, and all bridges connect
with the same @`bhumi-jal`, and it does not matter, not would even be known to
anyone, which bridge URL you used.

If the bhumi app is installed, the https://amitu.com/bhumi/ will be registered
as `apple-app-site-association` or `Universal Links` (iOS) or `App Links`
(Android). Which means you should prefer this bridge, as users with bhumi
installed will see the bhumi app launch when bridge url for some mantra using
`amitu.com/bhumi` bridge is clicked, the bhumi app will launch.
