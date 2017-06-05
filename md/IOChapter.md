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

-
-
## Paths, Files, Directories

-
-
## URL Connections

-
-
## Serialization
