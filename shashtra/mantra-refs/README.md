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
Emails, web pagees etc if you want to link to us, you can use the @`bridge-url`.
