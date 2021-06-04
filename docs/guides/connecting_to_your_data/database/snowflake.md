---
title: How to connect to your data in a Snowflake database
---
import Prerequisites from '../components/prerequisites.jsx'
import WhereToRunCode from '../components/where_to_run_code.md'
import NextSteps from '../components/next_steps.md'
import Congratulations from '../components/congratulations.md'
import DatabaseCredentials from '../components/adding_database_credentials.md'
import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

This guide will help you connect to data in a Snowflake database.
This will allow you to validate and explore your data.

<Prerequisites>

- Have access to data in a Snowflake database

</Prerequisites>

## Steps

### 1. Choose how to run the code in this guide

<WhereToRunCode />

### 2. Install required dependencies

First, install the necessary dependencies for Great Expectations to connect to your Snowflake database by running the following in your terminal:

```console
pip install sqlalchemy
pip install snowflake-connector-python
pip install snowflake-sqlalchemy
```

### 3. Add credentials

<DatabaseCredentials />

For this guide we will use a `connection_string` like this:

```
snowflake://<USER_NAME>:<PASSWORD>@<ACCOUNT_NAME>/<DATABASE_NAME>/<SCHEMA_NAME>?warehouse=<WAREHOUSE_NAME>&role=<ROLE_NAME>
```   

### 4. `[🍏 CORE SKILL ICON]` Instantiate your project's DataContext

Import these necessary packages and modules.

```python file=../../../../tests/integration/docusaurus/connecting_to_your_data/database/snowflake_yaml_example.py#L3-L5
```

Load your DataContext into memory using the `get_context()` method.

```python file=../../../../tests/integration/docusaurus/connecting_to_your_data/database/snowflake_yaml_example.py#L24
```

### 5. Configure your Datasource

<Tabs
  groupId="yaml-or-python"
  defaultValue='yaml'
  values={[
  {label: 'YAML', value:'yaml'},
  {label: 'python', value:'python'},
  ]}>
  <TabItem value="yaml">

Put your connection string in this template:

```python file=../../../../tests/integration/docusaurus/connecting_to_your_data/database/snowflake_yaml_example.py#L26-L40
```
Run this code to test your configuration.
```python file=../../../../tests/integration/docusaurus/connecting_to_your_data/database/snowflake_yaml_example.py#L49
```

</TabItem>
<TabItem value="python">

Put your connection string in this template:

```python file=../../../../tests/integration/docusaurus/connecting_to_your_data/database/snowflake_python_example.py#L27-L44
```
Run this code to test your configuration.
```python file=../../../../tests/integration/docusaurus/connecting_to_your_data/database/snowflake_python_example.py#L50
```

</TabItem>
</Tabs>

You will see your database tables listed as `Available data_asset_names` in the output of `test_yaml_config()`.

Feel free to adjust your configuration and re-run `test_yaml_config` as needed.

### 6. Save the Datasource configuration to your DataContext

Save the configuration into your `DataContext` by using the `add_datasource()` function.

<Tabs
  groupId="yaml-or-python"
  defaultValue='yaml'
  values={[
  {label: 'YAML', value:'yaml'},
  {label: 'python', value:'python'},
  ]}>
  <TabItem value="yaml">

```python file=../../../../tests/integration/docusaurus/connecting_to_your_data/database/snowflake_yaml_example.py#L51
```

</TabItem>
<TabItem value="python">

```python file=../../../../tests/integration/docusaurus/connecting_to_your_data/database/snowflake_python_example.py#L52
```

</TabItem>
</Tabs>

### 7. Test your new Datasource

Verify your new Datasource by loading data from it into a `Validator` using a `BatchRequest`.

<Tabs
  defaultValue='runtime_batch_request'
  values={[
  {label: 'Using a SQL query', value:'runtime_batch_request'},
  {label: 'Using a table name', value:'batch_request'},
  ]}>
  <TabItem value="runtime_batch_request">

Here is an example of loading data by specifying a SQL query.

```python file=../../../../tests/integration/docusaurus/connecting_to_your_data/database/snowflake_yaml_example.py#L54-L68
```

  </TabItem>

  <TabItem value="batch_request">

Here is an example of loading data by specifying an existing table name.

```python file=../../../../tests/integration/docusaurus/connecting_to_your_data/database/snowflake_python_example.py#L72-L83
```

  </TabItem>
</Tabs>

<Congratulations />

## Additional Notes

To view the full scripts used in this page, see them on GitHub:

- [snowflake_yaml_example.py](https://github.com/great-expectations/great_expectations/blob/knoxpod/integration/code/connecting_to_your_data/database/snowflake_yaml_example.py)
- [snowflake_python_example.py](https://github.com/great-expectations/great_expectations/blob/knoxpod/integration/code/connecting_to_your_data/database/snowflake_python_example.py)

## Next Steps

<NextSteps />