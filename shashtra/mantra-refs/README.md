# Mantra Referencing

When writing a mantra, we often want to refer to other mantras, either in the
same shashtra, or in another. We have different ways to do that, depending on
the context, you can pick among them.



## Full Path

The full of a mantra is of the format 
`bhumi://<shashtra-download-url|domain|alias>/<mantra-name>`.

This defines a new "protocol", "bhumi://", and if the user has the bhumi app 
installed, and their OS supports this feature, they click on a bhumi:// link,
and it will open the right mantra.

### Alias Handling

If the alias is used instead of @`shashtra-download-url`, and if the user has
not already used that alias in the past, the system will ask the user to enter
the @`shashtra-download-url`, so we can download it.

### Domain Handling

If the domain is used, bhumi will do a DNS lookup, and look for BHUMI tagged
TXT record, if found, that will be assumed to contain the 
@`shashtra-download-url`.

### `shashtra-download-url` Handling

If a download URL is given, and we infer that splitting the full path on slash,
and look for the last shash, anything beyond that is mantra-name, which also
means mantra names can't contain slashes.

This means mantras must be organised as flat list of mantras, instead of mantra 
hierarchy, which has no meaning in @`gananiti`@.




## Mantra: @`bridge-url`

A mantra can be referred by a http or https URL, we call it bridge url, which
is useful to link to bhumi content from regular net, so from Facebook, WhatsApp,
Emails, web pages etc. if you want to link to us, you can use the @`bridge-url`.


## Mantra: @`relative-references`

Most of the time we want to mention other mantras from the same shashtra, for which
we will be using the at the rate sign, `@`, followed by the mantra name in 
"backticks".

We could have used `@relative-references` also, without the backticks, slightly
easier to type, but then it conflicts with the @username convention, that you
may still want to use, so in other software like Git, Slack etc you can continue
to use `@username` semantics, that is quite widely supported, but mantras follow
the @-backticked-mantra semantics, which distinguishes us. 

The backtick also means Markdown aware software will show the mantra name in
slightly different font. This makes it easier to emphasize that this is special 
word, please read the definition to make sure you are using the right definition 
and not using world knowedge to deduce things, which can cause confusion in 
communication.

## Mantra: @`shashtra-refs`

Like mantra, shashtra also need referencing syntax. Each shashtra also has a
`refs.md`, which defines all the shashtras referred in that shashtra.

## Shashtra: @`bhumi-shashtra`@

In this case we are referring the shashtra with an alias `bhumi-shashtra`. The
aliases are themselves defined in the `refs.md` of the shashtra, so you can open
this shashtra's `refs.md` file to check.

We add `@` both at the beginning and at the end to indicate this is a shashtra.
