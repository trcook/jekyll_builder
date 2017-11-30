bootstrap:docker
From:ruby:2.4-alpine


%setup 
mkdir -p ${SINGULARITY_ROOTFS}/work
cp Gemfile ${SINGULARITY_ROOTFS}/work/Gemfile

%files

landing/Gemfile /work
landing/Rakefile /work
landing/_layouts /work
landing/_includes /work
landing/robots.txt /work
landing/_base_config.yml /work
landing/assets /work

%post
export GEM_HOME=/usr/local/bundle
export GEM_HOME=/usr/local/bundle
export BUNDLE_APP_CONFIG=/usr/local/bundle
export BUNDLE_BIN=/usr/local/bundle/bin
export BUNDLE_PATH=/usr/local/bundle
export BUNDLE_SILENCE_ROOT_WARNING=1

apk add --update alpine-sdk
cd /work
adduser -D alpine



chmod -R ugo+rwx /work
chmod -R ugo+rwx /usr/local
chown -R alpine /work
chgrp -R alpine /work
#chown -R alpine /usr/local
#chgrp -R alpine /usr/local
#printenv>>pre_lock

bundle install

#su -c 'bundle install --system' 



%runscript
BACK=$PWD
export BACK
echo $BACK
cp landing/*.md /work
cp -r landing/pages/ /work/pages/
cp -r landing/assets/ /work/assets/
cp landing/_base_config.yml /work
cd /work
echo $(ls)
rake setup local
echo 'deployed'
cp -r _site $BACK/_site
jekyll serve -H 0.0.0.0
