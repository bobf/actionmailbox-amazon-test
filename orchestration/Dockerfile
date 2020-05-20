FROM ruby:2.6.5
ARG BUNDLE_BITBUCKET__ORG
ARG BUNDLE_GITHUB__COM
ARG GIT_COMMIT
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash - \
 && apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y \
      nodejs \
      gosu \
      sendmail \
 && rm -rf /var/lib/apt/lists/* \
 && gem install bundler \
 && mkdir /app
WORKDIR /app
COPY .build/Gemfile .build/Gemfile.lock ./
RUN bundle install --without development test --deployment
ADD .build/context.tar .

RUN echo "${GIT_COMMIT}" > /app/GIT_COMMIT
HEALTHCHECK --interval=30s \
            --timeout=30s \
            --start-period=5s \
            --retries=3 \
            CMD ["bundle","exec","rake","orchestration:healthcheck"]
ENTRYPOINT ["/app/orchestration/entrypoint.sh"]
CMD ["bundle","exec","puma","-C","config/puma.rb"]
