## Installing unreleased OCS build

1. Download the file [install-ocs.sh](https://github.com/afreen23/dev-setup/blob/main/install-ocs.sh)
  ```bash
    wget https://raw.githubusercontent.com/afreen23/dev-setup/main/install-ocs.sh
    chmod +x install-ocs.sh
  ```

2. Login to your OCP cluster

3. Run the file as `./install-ocs.sh`

4. Go to the console > Operator hub > Storage > Choose the non-GA version to install OCS

## Installing m4.2xlarge cluster for OCS

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

Note: These machines incur more cost hence use wisely. Destroy the cluster when not in use by `openshift-installer destroy cluster --dir mydir`
