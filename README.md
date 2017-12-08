# ICP-IBM-Cloud-Private-
Continuous learning with the world of IBM Cloud Private

# Add the chart to the internal repository

After you package the Helm chart, you can add it to the internal repository that is provided with IBM® Cloud Private.

Before you load the chart, complete the following prerequisites:

* Install the IBM® Cloud Private CLI and log in to your cluster. [See Installing the IBM® Cloud Private CLI.](https://www.ibm.com/support/knowledgecenter/SSBS6K_2.1.0/manage_cluster/install_cli.html)
* Add the cluster IP and cluster CA domain to the hosts file as shown in step 1 of [Pushing and pulling images.](https://www.ibm.com/support/knowledgecenter/SSBS6K_2.1.0/manage_images/using_docker_cli.html)

1. Package the Helm chart.

2. If you have not, log in to your cluster from the IBM® Cloud Private CLI and log in to the Docker private image registry.
	``` console
    bx pr login -a https://<cluster_CA_domain>:8443 --skip-ssl-validation
    ```
Where cluster_CA_domain is the certificate authority (CA) domain. If you did not specify a CA domain, the default value is mycluster.icp. See [Specifying your own certificate authority (CA) for IBM® Cloud Private services.](https://www.ibm.com/support/knowledgecenter/SSBS6K_2.1.0/installing/create_ca_cert.html)

3. Install the Helm chart:
	```console
	bx pr load-helm-chart --archive <helm_chart_archive> [--clustername <cluster_CA_domain>]
	```
Where helm_chart_archive is the name of your compressed Helm chart file and <cluster_CA_domain> is the certificate authority (CA) domain.

4. Update the package repository by using the IBM® Cloud Private cluster management console.

	1. From the IBM® Cloud Private management console, click **Menu > Admin > Repositories.**
	2. Click **Sync Repositories.**
	3. Click **Menu > Catalog**

The new Helm charts load into the Catalog, and you can install them into your cluster.

Note: You can only load the Helm charts by using the Catalog. You cannot load the charts by using the Helm CLI.

