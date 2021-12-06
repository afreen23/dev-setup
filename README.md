## Installing unreleased ODF build

### Requirements
 - [jq](https://stedolan.github.io/jq/) should be present
 - Export an environment variable by name `ODF_PULL_SECRET` having the odf pull secret. 

   For example:
     
    ```
    # Edit bashrc
    bash vi ~/.bashrc

    #Add pull secret ODF_PULL_SECRET
    export ODF_PULL_SECRET=<odf-pull-secret>
    ```
  _Note: Make sure to use `ODF_PULL_SECRET` as the name of the variable in order to get the script working_


### Installation

1. Download the file [install-ocs.sh](https://github.com/afreen23/dev-setup/blob/main/install-ocs.sh)
  ```bash
    wget https://raw.githubusercontent.com/afreen23/dev-setup/main/install-ocs.sh
    chmod +x install-ocs.sh
  ```
2. Login to your OCP cluster
3. Run the file as `./install-ocs.sh`
4. Pass the token secret when asked and wait for script to finish.
5. Go to the console > Operator hub > Storage > Choose the non-GA version to install ODF

Note: _It can take upto 7-10 minutes to get the pull secret updated and hence the ODF catalog to appear in hub_

## Installing m4.2xlarge cluster for ODF

1. Install the `openshift-installer`
2. Create install config
```bash
 ./openshift-installer create install-config --dir my-dir
```
3. Provide all inputs
4. Edit the `platform` field for worker nodes in install config as
```yaml
platform:
  aws: 
    type: m4.2xlarge
```
Save the changes.
5. Create cluster
```bash
./openshift-installer create cluster --dir my-dir
```

_Note: These machines incur more cost hence use wisely. Destroy the cluster when not in use by `openshift-installer destroy cluster --dir mydir`_
