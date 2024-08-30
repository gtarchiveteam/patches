# Making and adding patches
Note that this only really relates to stuff special to our launcher client. We will not explain how to make a private server or implement serversided logic for Gorilla Tag's servers here.

The patches we use are xdelta3 patches with no secondary compression. This boils down to using ``xdelta3 -S -e -s [original assembly] [modified assembly] [output patch]``

Note that you HAVE to make the patches without secondary compression. The xdelta3 library we use in our launcher doesn't support it.

Then you have to modify the JSON file at the repository root - the launcher client uses this and deserializes it into a list of our own custom build classes, and the client uses its response to determine what the name of the build is, the path to install it to, the description, the manifest to download (if relevant) among some other rather important data.

Just look at the existing JSON content, it should be pretty easy to figure out what to do here.
GameLink currently isn't used by anything and all builds should have IsSteam be true.
