FROM node:16.3.0-alpine3.13 as builder

ENV VERSION=1.4.9

RUN mkdir /empty

RUN npm install -g @defasm/core@$VERSION esbuild pkg

# Bundle defasm so it can be pkg'd
RUN esbuild --bundle --outfile=defasm.js --platform=node /usr/local/bin/defasm \
 && pkg -t alpine defasm.js

FROM scratch

COPY --from=0 /lib/ld-musl-x86_64.so.1 /lib/
COPY --from=0 /empty                   /proc
COPY --from=0 /empty                   /tmp
COPY --from=0 /defasm                  /usr/bin/
