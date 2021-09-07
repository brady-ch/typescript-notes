# Getting Started

The following are instructions for adding typescript to a project and watching the changes
 1.  Install Typescript using your package manager `npm install -g typescript`, `yarn add typescript`
 2.  You can boot up a server to run your typescript in real time, (I used lite-server), then add a script for lite-server to boot it up.
 3.  run `tsc --init` to create a [[Compiler and Configuration#tsconfig json | tsconfig.json]] file which will indicate to the project that the project is managed by Typescript. This will allow you to just run tsc which will compile all of your Typescript files to Javascript.
 4.  Run `tsc -w` to enter watch mode and it will recompile all of your Typescript files to Javascript without running the command whenever you save.