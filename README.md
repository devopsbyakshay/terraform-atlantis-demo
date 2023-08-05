# terraform-atlantis-demo

##### All the commands/links are mentioned below which were used to setup an Atlantis server


#### Generate random webhook secret
```
openssl rand -base64 20
```

#### download the Atlantis binary from the Atlantis release page

[Atlantis Release Page](https://github.com/runatlantis/atlantis/releases)

#### Download the Atlantis binary using the wget command.
Please get the latest binary Url from the release page. I am mentioning the one which I used in the demo.
```
wget https://github.com/runatlantis/atlantis/releases/download/v0.24.4/atlantis_linux_386.zip
```

#### Unzip the downloaded binary and move it to /usr/local/bin
```
unzip atlantis_linux_386.zip
sudo mv atlantis /usr/local/bin/
```

#### Environment variables which we need to expose before starting the server
```
export TOKEN=<ghp_YOUR_GITHUB_TOKEN_HERE>
export URL=<YOUR_ATLANTIS_URL>
export USERNAME=<YOUR_GITHUB_USERNAME>
export SECRET=<WEBHOOK_SECRET_GENERATED_FROM_OPENSSL_COMMAND>
export REPO_ALLOWLIST=<YOUR_GITHUB_REPO>
export TF_VERSION=v1.5.4
```

#### Command to start atlantis server
```
atlantis server \
--atlantis-url="$URL" \
--gh-user="$USERNAME" \
--gh-token="$TOKEN" \
--gh-webhook-secret="$SECRET" \
--repo-allowlist="$REPO_ALLOWLIST" \
--default-tf-version=$TF_VERSION
```
