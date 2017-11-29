bootstrap:docker
From:ruby/2.4-alpine

%setup 
mkdir -p ${SINGULARITY_ROOTFS}/work
cp Gemfile ${SINGULARITY_ROOTFS}/work/Gemfile
%post
apk add --update alpine-sdk
