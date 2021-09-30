FROM cimg/android:2021.09.1
ENV PATH="/usr/local/bin/flutter/bin:${PATH}"
# Install and pre-cache Flutter.
RUN sudo wget https://storage.googleapis.com/flutter_infra_release/releases/stable/linux/flutter_linux_2.5.1-stable.tar.xz && \
  sudo tar xf flutter_linux_2.5.1-stable.tar.xz -C /usr/local/bin && \
  sudo rm flutter_linux_2.5.1-stable.tar.xz
RUN sudo chown -R $(whoami) /usr/local/bin/flutter/
#try chown on everything
RUN sudo chown -R $(whoami) /var
RUN sudo /usr/local/bin/flutter/bin/flutter precache --no-web --no-linux --no-windows --no-fuchsia --no-ios --no-macos
RUN sudo apt update
#needs lcov https://stackoverflow.com/a/53663093/9481613
# output coverage artifacts to circleci, download or send to Slack with 
#build results
RUN sudo apt-get update -qq -y
RUN sudo apt-get install lcov -y
RUN sudo apt install -y ruby ruby-dev rubygems
# Install fastlane.
RUN sudo gem install fastlane -NV
