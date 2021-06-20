# Openmsx-sync

Openmsx-sync is a system for synchronizing multiple instances of OpenMSX.  This
is meant to be used for turning single player games into multi player games.
Example use case: in a game like Maze of Galious, the inventory can be shared.
That way, when one player picks up an item, all players receive it.

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

# Running the server

Simply prepare the games directory and start the executable. It will listen for
network connections on port 4567 by default, but that can be changed using the
--port argument.

# Running the client

Run the executable with --game gamename as an argument. The gamename is the
same as the name of the regions file, without the extension. By default it
connects to localhost port 4567. To change that, use the --port argument, in
the form hostname:port
