# Openmsx-sync

Openmsx-sync is a system for synchronizing multiple instances of OpenMSX.  This
is meant to be used for turning single player games into multi player games.
Example use case: in a game like Maze of Galious, the inventory can be shared.
That way, when one player picks up an item, all players receive it.

Note that this is not meant for cheating: when one player loses an item, it is
also lost by everyone. And in particular, when one player dies in a game that
causes you to lose all your gear, that happens to all other players as well.
This is intentional: it means you need to help each other, because all problems
are shared.

The system contains a server and a client. One server needs to be started on a
computer that can be reached by all players' computers. The server defines one
or more games that can be started, including the memory regions that are to be
shared.

Each player starts a client, which will receive the ROM file from the server.
It uses OpenMSX to start it. It will also monitor the memory regions that were
defined in the server and notify the server when any of them is written to, as
well as write contents back to them when the server sends an update.

# Regions definitions

See the README in the games/ directory for a description of the regions file
format.

# Prerequisites

To run, the system needs three modules that I wrote. They are currently only on
github, named python-fhs, python-network and python-websocketd, all in my
account (https://github.com/wijnen/).

You only need the \*.py file from each of them. Place those in the same
directory as the openmsx-sync-\* executables.

# Running the server

Simply prepare the games directory and start the executable. It will listen for
network connections on port 4567 by default, but that can be changed using the
--port argument.

# Running the client

Run the executable with --game gamename as an argument. The gamename is the
same as the name of the regions file, without the extension. By default it
connects to localhost port 4567. To change that, use the --port argument, in
the form hostname:port

# Issues

There are some, for sure! I'd like to keep them all in one place, so please
check the github page for the current state. And if you find something that
isn't listed, please report it.

# Contact

You can contact me at Bas Wijnen <wijnen@debian.org>.
