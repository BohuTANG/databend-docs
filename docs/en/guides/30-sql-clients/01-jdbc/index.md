---
title: DBeaver
---

import StepsWrap from '@site/src/components/StepsWrap';
import StepContent from '@site/src/components/Steps/step-content';

[DBeaver](https://dbeaver.com/) supports connecting to Databend using a built-in driver categorized under **Analytical**, available starting from **version 24.3.1**.

![](@site/static/img/connect/dbeaver.png)

## Prerequisites

- DBeaver 24.3.1 or later version installed
- For self-hosted Databend: [Docker](https://www.docker.com/) installed (if using Docker deployment)

## User Authentication

If you are connecting to a self-hosted Databend instance, you can use the admin users specified in the [databend-query.toml](https://github.com/databendlabs/databend/blob/main/scripts/distribution/configs/databend-query.toml) configuration file, or you can connect using an SQL user created with the [CREATE USER](/sql/sql-commands/ddl/user/user-create-user) command.

For connections to Databend Cloud, you can use the default `cloudapp` user or an SQL user created with the [CREATE USER](/sql/sql-commands/ddl/user/user-create-user) command. Please note that the user account you use to log in to the [Databend Cloud console](https://app.databend.com/) cannot be used for connecting to Databend Cloud.

## Connecting to Self-Hosted Databend

<StepsWrap>
<StepContent number="1">

### Start Databend (Docker)

Run the following command to launch a Databend instance:

:::note
If no custom values for `QUERY_DEFAULT_USER` or `QUERY_DEFAULT_PASSWORD` are specified when starting the container, a default `root` user will be created with no password.
:::

```bash
docker run -d --name databend \
  -p 3307:3307 -p 8000:8000 -p 8124:8124 -p 8900:8900 \
  datafuselabs/databend:nightly
```

</StepContent>
<StepContent number="2">

### Configure Connection

1. In DBeaver, go to **Database** > **New Database Connection** to open the connection wizard, then select **Databend** under the **Analytical** category.

![alt text](@site/static/img/connect/dbeaver-analytical.png)

2. Enter `root` for the **Username** (or your configured username).

![alt text](@site/static/img/connect/dbeaver-user-root.png)

3. Click **Test Connection** to verify the connection. If this is your first time connecting to Databend, you will be prompted to download the driver. Click **Download** to proceed.

![alt text](@site/static/img/connect/dbeaver-download-driver.png)

Once the download is complete, the test connection should succeed:

![alt text](@site/static/img/connect/dbeaver-success.png)

</StepContent>
</StepsWrap>

## Connecting to Databend Cloud

<StepsWrap>
<StepContent number="1">

### Obtain Connection Information

Log in to Databend Cloud to obtain connection information. For more information, see [Connecting to a Warehouse](/guides/cloud/using-databend-cloud/warehouses#connecting).

![alt text](@site/static/img/connect/dbeaver-connect-info.png)

:::note
If your `user` or `password` contains special characters, you need to provide them separately in the corresponding fields (e.g., the `Username` and `Password` fields in DBeaver). In this case, Databend will handle the necessary encoding for you. However, if you're providing the credentials together (e.g., as `user:password`), you must ensure that the entire string is properly encoded before use.
:::

</StepContent>
<StepContent number="2">

### Configure Connection

1. In DBeaver, go to **Database** > **New Database Connection** to open the connection wizard, then select **Databend** under the **Analytical** category.

![alt text](@site/static/img/connect/dbeaver-analytical.png)

2. In the **Main** tab, enter the **Host**, **Port**, **Username**, and **Password** based on the connection information obtained in the previous step.

![alt text](@site/static/img/connect/dbeaver-main-tab.png)

3. In the **Driver properties** tab, enter the **Warehouse** name based on the connection information obtained in the previous step.

![alt text](@site/static/img/connect/dbeaver-driver-properties.png)

4. In the **SSL** tab, select the **Use SSL** checkbox.

![alt text](@site/static/img/connect/dbeaver-use-ssl.png)

5. Click **Test Connection** to verify the connection. If this is your first time connecting to Databend, you will be prompted to download the driver. Click **Download** to proceed. Once the download is complete, the test connection should succeed:

![alt text](@site/static/img/connect/dbeaver-cloud-success.png)

</StepContent>
</StepsWrap>
