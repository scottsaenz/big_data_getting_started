---
title: "22: Getting Started"
---
<img style="display: none;" src="https://static.bc-edx.com/data/dl-1-2/m22/lms/img/banner.jpg" alt="lesson banner" />

This section serves as a tutorial for you to set up the tools you need for this module: PySpark and Databricks.

> **Important** Before installing new tools, open your terminal and make sure that your `dev` Conda environment is activated.

### Installing and Setting up PySpark on macOS

#### Install Java

1. Java is required to run PySpark. Before you install Java, check to see if you have Java installed by running the following in the command line, `java -version`.

2. If Java is not installed, download the x64 Installer from the [Oracle website](https://www.oracle.com/java/technologies/downloads/#jdk19-windows).

    ![Java download](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/Java_download_Mac.png)

3. Or, you can use [Homebrew](https://formulae.brew.sh/formula/openjdk) to install Java. On the terminal, type and run `brew install openjdk` to install Java.

4. After you install Java, you can check your installation by running, `java -version`.

#### Install PySpark

On the terminal, type and run `pip install pyspark==3.3.1"`.

After you have installed PySpark, you can check your installation by running, `spark-submit --version` in the terminal. The output should be similar to the following image:

  ![Spark installation check](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/Mac_Spark_check.png)


#### Install Findspark

On the terminal, type and run `conda install -c conda-forge findspark` to install Findspark.

* **Note:** Findspark adds a startup file to the current IPython profile so that the environment variables will be properly set and `pyspark` will be imported upon IPython startup.

#### Install PyArrow and Fastparquet

On the terminal, type and run `conda install -c conda-forge pyarrow` and `conda install -c conda-forge fastparquet`.

* **Note:** `pyarrow` and `fastparquet` will allow us to read and write parquet-format big data.

After you have installed`pyarrow` and `fastparquet`, you can check your installation by running;
`conda list pyarrow` and `conda list fastparquet`.

#### Running PySpark in Jupyter Notebook

1. In your `dev` Conda environment, launch Jupyter notebook.

2. Select a new notebook with the `dev` kernel.

3. In the new notebook, type and run the following code:

    ```python
    # Import and initialize findspark
    import findspark
    findspark.init()

    # Start Spark session
    from pyspark.sql import SparkSession
    spark = SparkSession.builder.appName("Testing").getOrCreate()

    # Create a Spark DataFrame
    df = spark.createDataFrame([
    (0, "First row"),
    (1, "Second row"),
    (2, "Third row")
    ], ["ids", "rows"])

    df.show()
    ```

4. If your output looks like the following, congratulations!

    | ids | rows |
    | -- | -- |
    | 0  | First row |
    | 1  | Second row |
    | 2  | Third row |


### Installing and Setting up PySpark on Windows

#### Install Java

1. Before you install Java, check to see if you have Java installed by running the following in the command line, `java -version`.

2. If Java is not installed, download the x64 Installer from the [Oracle website](https://www.oracle.com/java/technologies/downloads/#jdk19-windows).

    ![Java download](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/Java_download_Windows.png)

3. After you install Java, you can check your installation by running, `java -version`.

#### Download and Install PySpark

1. From the [Apache Spark](https://spark.apache.org/downloads.html) distribution website, select the Spark 3.3.1 release and the Apache Hadoop 2.7 package.

    ![Download Apache Spark](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/Apache_Spark_download.png)

2. Apache Spark download is a `.tgz` file, which can be unpacked with [7-Zip](https://7-zip.org/download.html).

    * If you don't have 7-Zip, download and install the distribution for your system.

        ![Download 7-Zip](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/7-Zip_Download.png)

3. Next, unpack the `.tgz` file to create the `.tar` file. Then, unpack the `.tar` file with 7-Zip to get the "spark-3.3.1-bin-hadoop2" folder.

    ![Unpacking Spark Hadoop tgz file](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/spark_download.png)


4. Move the "spark-3.3.1-bin-hadoop2" folder into the `C:\Users` folder on your computer.

5. Download the Hadoop binary for Windows, `winutils.exe`, from Steve Loughran’s [GitHub](https://github.com/steveloughran/winutils/).

    * Click on the "hadoop-2.7.1" version, since that is the Hadoop version we downloaded.
    * Open the "bin" folder.
    * Click on the `winutils.exe` file.
    * Click "Download" to download the `winutils.exe` file onto your computer.

        ![winutils.exe Haddoop binary](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/winutils_exe.png)

6. Next, move the `winutils.exe` file into the "bin" folder of the "spark-3.3.1-bin-hadoop2.7" folder.

7. Check the installation of Spark by typing and running `spark-submit --version` in the command line. The output should be similar to the following image:

    ![Spark installation check](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/Win_Spark_check.png)

### Set up the Environment Variables

1. Open the environment variables by typing "env " in the search box, then click "Open".

    ![Environment variables](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/environment_variables.png)

2. In the System Properties, open the "Environment Variables".

    ![System Properties](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/System_Properties_environment_variables.png)

3. In the "User variables", create four new environment variables as follows:

    ![new environment variables](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/new_environment_variables.png)

    * **Note:** If you didn't move the "spark-3.3.1-bin-hadoop" folder into the `C:\Users` folder, you'll have to add the new path as the value.

4. Save all your changes.

    * **Note:**  You may have to restart your computer to update the environment variables.

#### Install Findspark

Activate your `dev` Conda environment and then type and run `conda install -c conda-forge findspark` to install Findspark.

* **Note:** Findspark adds a startup file to the current IPython profile so that the environment variables will be properly set and `pyspark` will be imported upon IPython startup.

#### Install PyArrow and Fastparquet

On the terminal type, run `conda install -c conda-forge pyarrow` and `conda install -c conda-forge fastparquet`.

* **Note:** `pyarrow` and `fastparquet` will allow us to read and write parquet-format big data.

#### Running PySpark in Jupyter Notebook

1. Open the Anaconda prompt and activate your `dev` Conda environment, then launch Jupyter notebook.

2. Select a new notebook with the `dev` kernel.

3. In the new notebook, type and run the following code:

    ```python
    # Import and initialize findspark
    import findspark
    findspark.init()

    # Start Spark session
    from pyspark.sql import SparkSession
    spark = SparkSession.builder.appName("Testing").getOrCreate()

    # Create a Spark DataFrame
    df = spark.createDataFrame([
    (0, "First row"),
    (1, "Second row"),
    (2, "Third row")
    ], ["ids", "rows"])

    df.show()
    ```

4. If your output looks like the following, congratulations you are all set!

    | ids | rows |
    | -- | -- |
    | 0  | First row |
    | 1  | Second row |
    | 2  | Third row |


### Creating a Databricks Account.

> **Important** The Databricks Community Edition is good for 14-days. We suggest that you to create an account the day before you use Databricks in the course. <br>
**We will use Databricks on 5/25/2023**

This guide reviews the steps for creating a Databricks Community Edition account and using Databricks.

#### Create an Account

1. Go to the [Databricks Community Edition site](https://docs.databricks.com/getting-started/community-edition.html) and click “Try Databricks!”.

2. On the next page, fill out the required information and click "Get Started For Free."

    ![databricks signup form for required information](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/databricks_signup_form.png)

3. You will be redirected to sign up for the standard Databricks account. Do NOT click any of the cloud provider options. To use the Community Edition, click "Get started with Community Edition."

    ![databricks getting started with the community edition](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/databricks_getstartedwithCE.png)

4. Follow the onscreen prompts to verify your account.

    ![Verify your databricks account](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/verifying_databricks_account.png)

5. When prompted, check your email and click the link to verify your account and reset your password. Once you reset your password, you can log into the Community Edition.

#### Navigate the Community Edition

When you log into your Databricks Community Edition account, you'll see the Data Science and Engineering landing page:

![databricks community edition landing page](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/databricks_landing_page.png)

On the landing page, you can choose from four options:

1. A quick start tutorial to help you create a cluster, attach a notebook to your cluster, create a table for a dataset, query the table using SQL, create a table and a graph, and create a DataFrame.

2. Create a new notebook, such as a Jupyter notebook.

3. Import data.

4. Connect to external software, like Tableau, Power BI, and more. **Note:** The Community Edition does not allow connections to external software.

You can use the quick start tutorial to familiarize yourself Databricks, or proceed to the following steps to start using Databricks.

#### Using Databricks

Follow these steps to get started using Databricks.

1. Before you create a notebook, you have to create a cluster. On the navigation pane on the left side of the landing page, click "+" and select Cluster.

    ![Create a databricks cluster](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/databricks_create_cluster.png)

2. Use the default runtime settings, `11.3 LTS (Scala 2.12, Spark 3.3.0)`, or select an alternate version.

    ![Chose runtime settings for your cluster](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/databricks_select_cluster.png)

3. Enter a name for your cluster.

    ![Name your cluster](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/databricks_name_cluster.png)

4. Click the "Create Cluster" button at the top of the "Create Cluster" page.

    ![Create your cluster](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/create_databricks_cluster.png)

5. After clicking "Create Cluster", a progress circle icon will spin while the cluster is being created. This may take a few minutes.

    ![creation of cluster instance](https://static.bc-edx.com/data/dl-1-2/m22/lms/img/databricks_first_cluster.png)

You’re now ready to use Databricks!
