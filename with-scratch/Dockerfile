# Base image
FROM alpine as build
# multistage build first images layers dont matter docker export and save only care about last image
RUN mkdir -p /tmp/nothing-folder && touch /tmp/nothing-folder/some-other-file

FROM scratch as main
#------Copy needed bash commands----
COPY --from=build /lib/ld-musl-x86_64.so.1 /lib/ld-musl-x86_64.so.1
COPY --from=build /bin/sh /bin/rm /bin/mkdir /bin/ln /bin/echo /bin/

#-----Setup folders and needed files------
RUN mkdir -p /tmp/overwrite && mkdir -p /tmp/long-names && mkdir -p /tmp/to-delete && echo "to-delete-file" > /tmp/to-delete/file && echo "to-delete-by-folder" > /tmp/to-delete/by-folder && echo "dont delete me!" > /tmp/to-delete-but-not-this && mkdir -p /tmp/symlinks && echo "symlink" > /tmp/symlinks/file

#------Test files be overwritten-----
RUN echo "layer1" >> /tmp/overwrite/a-layer && echo "layer1" > /tmp/overwrite/layer && echo "layer1" > /tmp/overwrite/layer1
RUN echo "layer2" >> /tmp/overwrite/a-layer && echo "layer2" > /tmp/overwrite/layer && echo "layer2" > /tmp/overwrite/layer2
RUN echo "layer3" >> /tmp/overwrite/a-layer && echo "layer3" > /tmp/overwrite/layer && echo "layer3" > /tmp/overwrite/layer3

#------Test sym links and long sym link names-----
RUN ln -s /tmp/symlinks/file /tmp/symlinks/sym-file

#------Test long file names-----
RUN echo "long-name" > /tmp/long-names/this-is-a-really-long-name-that-is-hopefully-to-long-to-use-in-a-tar-so-we-will-see-how-that-does-because-its-gonna-be-hard-to-get-longer-than-100-characters-unless-i-can-keep-going-with-this-we-will-see-how-long-this-is-cool-its-long-enough-now
RUN ln -s /tmp/long-names/this-is-a-really-long-name-that-is-hopefully-to-long-to-use-in-a-tar-so-we-will-see-how-that-does-because-its-gonna-be-hard-to-get-longer-than-100-characters-unless-i-can-keep-going-with-this-we-will-see-how-long-this-is-cool-its-long-enough-now /tmp/long-names/this-is-a-really-long-SYM-name-that-is-hopefully-to-long-to-use-in-a-tar-so-we-will-see-how-that-does-because-its-gonna-be-hard-to-get-longer-than-100-characters-unless-i-can-keep-going-with-this-we-will-see-how-long-this-is-cool-its-long-enough-now

#------Test `.wh.file-name/folder-name` files-----
RUN rm /tmp/to-delete/file
RUN rm -r /tmp/to-delete

#------Test `.wh..wh..opq` files-----
# TODO cant figure out how to do it when files actually exist
