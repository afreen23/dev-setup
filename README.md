## Installing unreleased OCS build

1. Download the file [install.sh](https://github.com/afreen23/dev-setup/blob/main/install-ocs.sh)

2. Login to your OCP cluster

3. Run the file as `./install.sh`

4. Go to the console > Operator hub > Storage > Choose the non-GA version to install OCS

## Installing m4.2xlarge cluster for OCS

1. Install the `openhisft-installer`
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
