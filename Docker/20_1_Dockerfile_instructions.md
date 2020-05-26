### Dockerfile instructions:

These recommendations are designed to help you create an efficient and maintainable Dockerfile.

#### FROM :

------

-  `FROM` instruction initializes a new build stage and sets the base image for subsequent instructions. 
-  a valid `Dockerfile` must start with a `FROM` instruction. 
-  The image can be any valid image – it is especially easy to start by **pulling an image** from the public repositories.
- Usage: FROM  <image_name>:[<tag>] 
-  ex:  FROM ubuntu:18.04

#### RUN:

------

- The `RUN` instruction will execute any commands in a new layer on top of the current image and commit the results. 

- The resulting committed image will be used for the next step in the Dockerfile.

- Split long or complex `RUN` statements on multiple lines separated with backslashes to make your `Dockerfile` more readable, understandable, and maintainable.

- Usage:

  RUN  [any_ executable_ cmd]

- Example:

  Dockerfile1:

  ```
  FROM ubuntu:18.04
  RUN apt-get update
  RUN apt-get install -y curl
  ```

  Dockerfile2:

  ```
  FROM ubuntu:18.04
  RUN apt-get update && apt-get install -y
  ```

  In the first file 2 layers created above base image layer but in second file only 1 layer crated above base layer.

#### LABEL:

------

- You can add labels to your image to help organise images by project, record licensing information, to aid in automation, or for other reasons.

- For each label, add a line beginning with `LABEL` and with one or more key-value pairs.

- Usage: LABEL <key>=<value>

- Example: 

  ```
  # Set one or more individual labels
  LABEL com.example.version="0.0.1-beta"
  LABEL vendor1="ACME Incorporated"
  LABEL vendor2=ZENITH\ Incorporated
  LABEL com.example.release-date="2015-02-12"
  LABEL com.example.version.is-production=""
  ```

- An image can have more than one label. it was recommended to combine all labels into a single `LABEL` instruction, to prevent extra layers from being created.

  ```
  # Set multiple labels on one line
  LABEL com.example.version="0.0.1-beta" com.example.release-date="2015-02-12"
  ```

### CMD:

------

- The `CMD` instruction should be used to run the software contained in your image, along with any arguments.

- The `CMD` instruction has three forms:

  1.  `CMD ["executable", "param1", "param2"…]` (*exec* form, this is the preferred form)
  2. `CMD ["param1","param2"]` (as *default parameters to ENTRYPOINT*)
  3. `CMD command param1 param2` (*shell* form)

- If you use the *shell* form of the `CMD`, then the `` will execute in `/bin/sh -c

- Example:

  - ```
    CMD echo "This is a test." | wc -
    ```

### EXPOSE:

------

- The `EXPOSE` instruction informs Docker that the container listens on the specified network ports at runtime.

- You can specify whether the port listens on TCP or UDP, and the default is TCP if the protocol is not specified.

- Usage:

  - ```
    EXPOSE <port> [<port>/<protocol>...]
    ```

- Example:

  - ```
    EXPOSE 80/tcp
    EXPOSE 80/udp
    ```

### ENV:

------

- To make new software easier to run, you can use `ENV` to update the `PATH` environment variable for the software your container installs. For example, `ENV PATH /usr/local/nginx/bin:$PATH` ensures that `CMD ["nginx"]` just works.

- The `ENV` instruction is also useful for providing required environment variables specific to services you wish to containerize, such as Postgres’s `PGDATA`.

- Lastly, `ENV` can also be used to set commonly used version numbers so that version bumps are easier to maintain

- Usage:

  - ```
    ENV <key> <value>
    ENV <key>=<value> ...
    ```

- Example:

  - ```
    ENV PG_MAJOR 9.3
    ENV PG_VERSION 9.3.4
    RUN curl -SL http://example.com/postgres-$PG_VERSION.tar.xz | tar -xJC /usr/src/postgress && …
    ENV PATH /usr/local/postgres-$PG_MAJOR/bin:$PATH
    ```

#### ADD:

------

- The `ADD` instruction copies new files, directories or remote file URLs from <src> and adds them to the filesystem of the image at the path <dst>

- Multiple <scr> resources may be specified but if they are files or directories, their paths are interpreted as relative to the source of the context of the build.

- Each `` may contain wildcards and matching will be done using Go’s [filepath.Match](http://golang.org/pkg/path/filepath#Match) rules. For example:

- ADD has two forms

  - ```
    ADD [--chown=<user>:<group>] <src>... <dest>
    ADD [--chown=<user>:<group>] ["<src>",... "<dest>"]
    ```

- Example:

  To add all files starting with “hom”:

  ```
  ADD hom* /mydir/
  ```



For more information about Docker file instructions [clickhere](https://docs.docker.com/engine/reference/builder/).

