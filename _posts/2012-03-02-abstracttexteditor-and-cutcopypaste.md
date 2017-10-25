---
title: AbstractTextEditor and Cut/Copy/Paste + first keystroke problem
layout: post
tags: eclipse editor plugin rcp
---

If the cut,copy/paste commands don't work in the editor and it doesn't recognize the first keystroke then you should override the `AbstractDocumentProvider`'s `isReadOnly()` method in your document provider. The default implementation always returns true. Change it to false and everything works as expected.

Source:
[http://www.eclipse.org/forums/index.php/t/144925/](http://www.eclipse.org/forums/index.php/t/144925/)