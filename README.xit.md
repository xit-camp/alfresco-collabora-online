# notes for `alfresco-collabora-online`

1. compilation
  `JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64 mvn -Dmaven.test.skip clean`
  `JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64 ./run.sh build_image`

1. collabora test

    ```sh
    docker run -t -p 9980:9980 -e 'username=admin' -e 'password=password' -e "extra_params=--o:ssl.enable=false" --restart always --cap-add MKNOD collabora/code
    ```

1. zmeny oproti lool

    ```yaml
      lool:
        # 21.11.5.1.1
        image: collabora/code
        # https://sdk.collaboraonline.com/docs/installation/CODE_Docker_image.html#setting-the-application-configuration-dynamically-via-environment-variables
        environment:
          extra_params: '--o:ssl.enable=false --o:ssl.termination=true'
          dictionaries: 'en_GB en_US sk'
          server_name: 'lool.dev.***.sk'
          domain: 'wopi.dev.***.sk'
    ```
