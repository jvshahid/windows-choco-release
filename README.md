## Windows CHOCO Bosh-Release

Provides a colocated job that can be used to install [chocolatey](https://chocolatey.org) packages

### Usage in Cocnourse workers:

``` yaml
  jobs:
  - name: choco
    release: windows-choco
    properties:
      packages:
        - name: golang
          version: 1.8.3
        - name: vcredist2013
          version: 12.0.30501.20150616
        - name: mysql
          version: 5.7.18
      post-install: |+
        mysql -u root -e "CREATE USER 'diego'@'localhost' IDENTIFIED BY 'diego_password'; GRANT ALL PRIVILEGES ON *.* TO 'diego'@'localhost';"
  - name: concourse_windows
    release: concourse-windows-worker
    ...
```
