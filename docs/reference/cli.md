# MLServer CLI

The MLServer package includes a `mlserver` CLI designed to help with some of
the common tasks involved with a model's lifecycle.
Below, you can find the full list of supported subcommands.
Note that you can also get a similar high-level outline at any time by running:

```bash
mlserver --help
```

## Commands

### mlserver¶

Command-line interface to manage MLServer models.

```sh
mlserver [OPTIONS] COMMAND [ARGS]...
```

**Options**

```sh
--version¶
```

Show the version and exit.


#### build

Build a Docker image for a custom MLServer runtime.

```sh
mlserver build [OPTIONS] FOLDER
```

**Options**

```sh
-t, --tag <tag>¶
```

```sh
--no-cache¶
```

**Arguments**

```
FOLDER
```

Required argument

dockerfile¶

Generate a Dockerfile
```sh
mlserver dockerfile [OPTIONS] FOLDER
```
Options
```sh
-i, --include-dockerignore¶
```

Arguments

`FOLDER`

Required argument
```sh
infer
```

Execute batch inference requests against V2 inference server (experimental).
```sh
mlserver infer [OPTIONS]
```

Options
```sh
-u, --url <url>¶
```

URL of the MLServer to send inference requests to. Should not contain http or https.

-m, --model-name <model_name>¶
Required Name of the model to send inference requests to.

-i, --input-data-path <input_data_path>¶
Required Local path to the input file containing inference requests to be processed.

-o, --output-data-path <output_data_path>¶
Required Local path to the output file for the inference responses to be written to.

-w, --workers <workers>¶
-r, --retries <retries>¶
-s, --batch-size <batch_size>¶
Send inference requests grouped together as micro-batches.

-b, --binary-data¶
Send inference requests as binary data (not fully supported).

-v, --verbose¶
Verbose mode.

-vv, --extra-verbose¶
Extra verbose mode (shows detailed requests and responses).

-t, --transport <transport>¶
Transport type to use to send inference requests. Can be ‘rest’ or ‘grpc’ (not yet supported).

Options:
rest | grpc

-H, --request-headers <request_headers>¶
Headers to be set on each inference request send to the server. Multiple options are allowed as: -H ‘Header1: Val1’ -H ‘Header2: Val2’. When setting up as environmental provide as ‘Header1:Val1 Header2:Val2’.

--timeout <timeout>¶
Connection timeout to be passed to tritonclient.

--batch-interval <batch_interval>¶
Minimum time interval (in seconds) between requests made by each worker.

--batch-jitter <batch_jitter>¶
Maximum random jitter (in seconds) added to batch interval between requests.

--use-ssl¶
Use SSL in communications with inference server.

--insecure¶
Disable SSL verification in communications. Use with caution.

Environment variables

MLSERVER_INFER_URL
Provide a default for --url

MLSERVER_INFER_MODEL_NAME
Provide a default for --model-name

MLSERVER_INFER_INPUT_DATA_PATH
Provide a default for --input-data-path

MLSERVER_INFER_OUTPUT_DATA_PATH
Provide a default for --output-data-path

MLSERVER_INFER_WORKERS
Provide a default for --workers

MLSERVER_INFER_RETRIES
Provide a default for --retries

MLSERVER_INFER_BATCH_SIZE
Provide a default for --batch-size

MLSERVER_INFER_BINARY_DATA
Provide a default for --binary-data

MLSERVER_INFER_VERBOSE
Provide a default for --verbose

MLSERVER_INFER_EXTRA_VERBOSE
Provide a default for --extra-verbose

MLSERVER_INFER_TRANSPORT
Provide a default for --transport

MLSERVER_INFER_REQUEST_HEADERS
Provide a default for --request-headers

MLSERVER_INFER_CONNECTION_TIMEOUT
Provide a default for --timeout

MLSERVER_INFER_BATCH_INTERVAL
Provide a default for --batch-interval

MLSERVER_INFER_BATCH_JITTER
Provide a default for --batch-jitter

MLSERVER_INFER_USE_SSL
Provide a default for --use-ssl

MLSERVER_INFER_INSECURE
Provide a default for --insecure

init¶
Generate a base project template

mlserver init [OPTIONS]
Options

-t, --template <template>¶
start¶
Start serving a machine learning model with MLServer.

mlserver start [OPTIONS] FOLDER
Arguments

FOLDER¶
Required argument
