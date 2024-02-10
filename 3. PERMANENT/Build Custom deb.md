---
type: conclusion
topic: devops 
---
- Topic : #VeilleIT/devops 
- Tags : #docker #debian

# Idea


## run.sh 

```Bash
#!/bin/sh

PACKAGE_FOLDER_NAME=${APP_NAME}_${MEDTRA_BDS_VERSION}.${MEDTRA_BDS_RELEASE}_all
# Replace space char by underscore char in the package folder name
PACKAGE_FOLDER_NAME=$(echo $PACKAGE_FOLDER_NAME | sed 's/ /_/g')

mkdir -p /home/builder/deb/$PACKAGE_FOLDER_NAME
cp -Rf /home/builder/src/* /home/builder/deb/$PACKAGE_FOLDER_NAME/

ls /home/builder/deb/$PACKAGE_FOLDER_NAME/

# Templating
# For each template file replace the env variables
for file in $(find "/home/builder/deb/$PACKAGE_FOLDER_NAME/DEBIAN" -name "*.template"); do
    # get the file name without folder
    fileName=${file##*/}
    # Copy the template file to the destination in another folder with variable replaced
    echo "$file => /home/builder/deb/$PACKAGE_FOLDER_NAME/DEBIAN/${fileName%.template}"
    envsubst <$file >"/home/builder/deb/$PACKAGE_FOLDER_NAME/DEBIAN/${fileName%.template}"
    chmod 555 "/home/builder/deb/$PACKAGE_FOLDER_NAME/DEBIAN/${fileName%.template}"
    rm -f $file
done

cd /home/builder/deb
dpkg-deb --build $PACKAGE_FOLDER_NAME

cp /home/builder/deb/*.deb /home/builder/out/

# # convert CRLF to LF
# # find /home/builder/sourcefiles -name '*.spec' -print0 | xargs -0 dos2unix
# # find /home/builder/sourcefiles -name '*.sh' -print0 | xargs -0 dos2unix

# # Launch main script
# find /home/builder/sourcefiles -name '*.spec' -print0 | xargs -0 /home/builder/script/rpm-make.sh

exit 0

```

## Dockerfile

```Dockerfile
FROM debian:stable-slim

RUN apt-get update
RUN apt-get install -y build-essential dpkg-dev devscripts dos2unix

RUN useradd builder -u 1000 -m -G users,sudo && \
    # echo "builder ALL=(ALL:ALL) NOPASSWD:ALL" >> /etc/sudoers && \
    # echo "# macros"                      >  /home/builder/.rpmmacros && \
    # echo "%_topdir    /home/builder/rpm" >> /home/builder/.rpmmacros && \
    # #    echo "%_sourcedir %{_topdir}"        >> /home/builder/.rpmmacros && \
    # #    echo "%_builddir  %{_topdir}"        >> /home/builder/.rpmmacros && \
    # #    echo "%_specdir   %{_topdir}"        >> /home/builder/.rpmmacros && \
    # #    echo "%_rpmdir    %{_topdir}"        >> /home/builder/.rpmmacros && \
    # #    echo "%_srcrpmdir %{_topdir}"        >> /home/builder/.rpmmacros && \
    mkdir /home/builder/deb && \
    mkdir /home/builder/src && \
    mkdir /home/builder/out && \
    mkdir /home/builder/deb/DEBIAN && \
    chown -R builder /home/builder


COPY script/* /home/builder/script/
RUN chown -R builder: /home/builder/script \
    && chmod ug+x /home/builder/script/*

RUN dos2unix /home/builder/script/*.sh
USER builder

# ENV FLAVOR=rpmbuild OS=centos DIST=el7

WORKDIR /home/builder

ENTRYPOINT [ "/home/builder/script/run.sh" ]
#ENTRYPOINT ["tail", "-f", "/dev/null"]
```



# Links

Sources :

## West : Similar

## East : Opposite

## North : Theme / Question

[[How to package app]]

## South : What does it lead to



