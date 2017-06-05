## Input/Output streams, readers, writers

### Input/output streams

- Input streams -- A source to read bytes
- Output streams -- A destination to write bytes

-

#### I/O Streams come from multiple sources

- Come from multiple sources (eg: files, network, memory )
- Not related to the collection Streams API

-
#### I/O Streams vs Readers and writers

- I/O Streams consume and produce (read and write) bytes
- Readers and Writers consume and produce character sequences

-
#### Creating Input Streams with

- `Files.newInputStream(path)`
- `new URL(urlstring).openStream()`
- `new ByteArrayInputStream(byteArray)`

Note: lab idea: read html from a url and extract the comments. Expand by finding
content such as script/noscript/meta tags

-
#### Creating Output Streams

- `Files.newOutputStream(path)`
- `URLConnection.getOutputStream()`
- `new ByteArrayOutputStream()` -- can be converted to `ByteArray` after writing


-
-
#### Know your encoding

Unicode (UTF-8, UTF-16) are common. Many methods have optional encoding and
 default to system encoding.

-
-
## Paths, Files, Directories



-
### Filesystem Utility Classes

- `Files`
- `Paths`

-
### Paths

Path objects represent a route to a file, whether it exists or not. Use them to
 access, create, modify, or delete files and directories.

-
### Define relative or absolute paths

- `Path userDir = Paths.get("/", "users", "username");`
- `Path javaFile = Paths.get("labs", "lab1", "src", "main", "java", "App.java");`
- `Path roundabout = Paths.get("home", ".", "labs", "..", "documents", "..", ".", "Downloads");`

-
### Resolving or normalizing Paths

- `userDir.resolve(javaFile)` resolves to `/users/username/labs/lab1/src/main/java/App.java`
- `roundabout.normalize()` returns `Paths.get("home", "Downloads")`

-
### Directory operations

- `Files.createDirectory(path)` -- like `mkdir path`
- `Files.createDirectories(path)` -- like `mkdir -p path`
- `Files.createFile(path)`
- `Files.exists(path)`

-
-
## URL Connections

-
-
## Serialization
