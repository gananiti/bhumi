# Bhumi Shashtra Format

So bhumi works on "shashtra", each shashtra is an equivalent to a book or 
documentation of some kind. 

Eventually bhumi will support creation of shashtra in bhumi itself, but for now 
we are not going to work in shastra editor / viewer etc., and mantra editor / 
viewer etc., etc.

But both now and in future we will support shashtras stored in git, Dropbox or
wherever you want to store it. 

Shashtra from bhumi's point of view is just a folder, usually downloaded via
http as a zip files, but in future bhumi will support more protocols, like ftp
or bittorrent or IPFS etc. 

How so ever you download, we will get a `.zip` file (or one of the supported 
archive files, like `.tar.gz` or `.tar.bz2` etc.), and the content of that 
zip/archive file, are documented here. Since the archive file content would
be read by a program, the format should be followed as per this "mantra" else 
bhumi may fail to parse that file.





------

me: 

> So let’s talk about the bare essentials from the outside world perspective. We need a shashtra.zip file format specification that stores mantras, each mantra has 4 names, we can actually pick just one as other names were Sanskrit related, so we make them optional fields, we can even generalise, like every primary named mantra based on the natural language used by authors of those shashtra we can have canonical name in that language and then canonical translation of that name in various languages, again maintained as part of same shashtra.zip. Or we can even create a <shashtra-name>.<lang>.zip. The shashtra can link to other shashtra so we always identify a shashtra by a http url, but within shashtra we create aliases for other linked shashtra at a global level and a shashtra can re-export mantra defined in other linked shashtra (this way say if I want to modify just one mantra from a shashtra, my version will be used, and we can even call such kind of shashtra extension or modification shashtra, all the same mantras should be defined in extension, but extension one can redefine any mantra and export, so most extension mantra will have just a few modified mantra, tiny zip files, even when patching say the entirety of medical science. So for creating a new derived shashtra you have two reasons, either to “refine”/customise it, or to translate it, or both, the <shashtra>.<lang>.zip can become <original-shashtra-name>.<lang code or some tag to identify kind of extension. And we can even use dotting to start from root shashtra to Lang to native cultural customisation to geography overlay etc. lots of zips. Just as convention. For us it is just a zip file, the names are for humans. We will allow people to use shashtra.mantra even tho on runtime it will become shashtra.lang.mantra or whatever “customisations” user has configured in UI or what’s explicitly defined as learning goal. So say you ask for maths and I know your preferred lang is hindi so we download maths.hindi.zip after downloading. For discover we will again use aliasing etc. again let’s not belabour the rules here, this is a specific topic we can iterate on later. Bottoms line is zip files are plain http or ftp ipfs/bittorrent links (and we will have bhumi native way to create distribute zip and video files, in future, def not now. Mantra within a shashtra form a graph, technically dag, but in rare cases I am going to allow cycles as that’s just how we learn something’s a in terms of b and b in terms of a, in case of cycles we will show the cycle to user or just randomly pick from any place in the cycle based on overall dependency completion of each mantra so say if a 5 mantra cycle exists we will first teach the mantra to the student for which the student has learn the maximum number of dependencies (ideally 100% but in this case it can’t be because of cycle, anyways we only want 80%, as that way students start seeing unfamiliar topics early on, before they are taught, this allows student to naturally seek it out, curiosity is our best teacher etc). The zip file will have a folder each mantra or concept and each folder will contain a readme.md so browsing the experience is optimised for most git web browsers, they show readme.md by default. And we can put concept related content like light images or our excalidraw inspired whiteboard.json, which is our innovation, it will precisely track the on the whiteboard where the mantra was mentioned so one can hover over the white board and we show the relevant readme and shashtra etc, so it’s a rich interactive white board and in future it may have interactive elements like sliders, which will control the radius of circle, say this board was for show some circle related concept Let’s call that l interactive white board a chitra file, let’s not try to spec it out now, just note that mantra can contain .chitra files. Similarly mantra will contain quiz banks, so we will have a .quiz file format as well. Each mantra will have a content file, which will link to other content, like YouTube video or some External blog post, these Can also be picked by our bhumi software when deciding what next to show/do for this mantra, so system picks the next piece of thing to show in the UI, we have so many options, the readme, the chitras, the contents, and quizzes. Our system will be in teaching mode or in review mode for each mantra, based on where you are. Since others will be collaborating / writing these shashtra zip files, we have to document the file properly.
