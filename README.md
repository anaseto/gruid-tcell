**Migrated to https://codeberg.org/anaseto/gruid-tcell because of new 2FA requirement**

# gruid-tcell

[![pkg.go.dev](https://pkg.go.dev/badge/github.com/anaseto/gruid-tcell.svg)](https://pkg.go.dev/github.com/anaseto/gruid-tcell)
[![godocs.io](https://godocs.io/github.com/anaseto/gruid-tcell?status.svg)](https://godocs.io/github.com/anaseto/gruid-tcell)

The *gruid-tcell* module provides a [gruid](https://github.com/anaseto/gruid)
Driver for building terminal full-window applications.

The provided driver tcell package depends on the
[tcell](https://github.com/gdamore/tcell) terminal library, which uses the
permissive enough [Apache License
v2](https://github.com/gdamore/tcell/blob/master/LICENSE). The library is pure
Go, so no special steps are required to install it, and it allows for easy
cross-compilation.

You only need to look into the `tcell.Style` type documentation to define the
styling that has to be used by the Driver.

Note that the terminal grid is not a true grid: some characters are two-cell
wide (such as wide east-asian characters). The character width can be computed
thanks to the [go-runewidth](https://github.com/mattn/go-runewidth) package, so it
can be taken into account, but it is a bit cumbersome and ad hoc with respect
to the graphical drivers which could handle this problem more easily (the tile
width can be adjusted to fit any wanted character). Currently, runes with zero
value are ignored by this terminal driver, so they can be placed after a wide
character. A portable solution is to always pass wide-characters twice, but
with different attributes, and then handle this in each driver, either
replacing the second one with a zero rune (for this driver), or a different
image (for graphical drivers).
