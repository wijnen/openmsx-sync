# Regions definitions

On the server, in a directory named 'games', which is searched for in the same
directory as the server executable, the current working directory, and the data
path as defined by the xdg basedir spec. Any games in any of those locations
are added to the list of playable games.

This file is in that directory in the source, so if you run from the source,
you should put your region definitions in this directory.

In the games directories, there are files named \*.regions. Each of those files
contains a definition for one game.

The first line is the filename of the ROM cartridge. The path is relative to
the games directory. Normally, the rom files will be in that directory, but
they can be in a subdirectory if that is desired.

After that, empty lines and lines starting with # are ignored. (Such lines are
not allowed before the ROM filename.)

Other lines must contain at least two "words" (so len(line.split()) >= 2). The
first two words are interpreted as hex addresses. The first is the start
address of a region, the second is the last address that is still part of the
region. So to monitor a single byte, both words should be equal.

Any extra words on the line are ignored and can be used for documentation.
