# Base image
FROM ruby:2.6.0 as build1
COPY Gemfile-1 Gemfile
RUN bundle install

FROM ruby:2.6.0 as build2
COPY Gemfile-2 Gemfile
RUN bundle install && touch /usr/local/bundle/.wh..wh..opq
RUN echo "Need on more layer" > /tmp/test

FROM scratch
COPY --from=build1 /usr/local/bundle /usr/local/bundle
COPY --from=build2 /usr/local/bundle /usr/local/bundle
COPY --from=build2 /tmp/test /tmp/test
