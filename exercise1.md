<img src="https://github.com/openfaas/media/raw/master/OpenFaaS_Magnet_3_1_png.png" width="500px"></img>

Before starting this lab, create a new folder for your files:

```sh
$ mkdir -p lab2 \
   && cd lab2
```

## Use the UI Portal

You can now test out the OpenFaaS UI:

If you have set an `$OPENFAAS_URL` then get the URL and then click on it:

```sh
echo $OPENFAAS_URL
http://127.0.0.1:31112
```

If you haven't set an `$OPENFAAS_URL` then the default is normally: [http://127.0.0.1:8080](http://127.0.0.1:8080).

## Learn about the CLI

You can now test out the CLI, but first a note on alternate gateways URLs:

If your *gateway is not* deployed at http://127.0.0.1:8080 then you will need to specify the alternative location. There are several ways to accomplish this:

1. Set the environment variable `OPENFAAS_URL` and the `faas-cli` will point to that endpoint in your current shell session. For example: `export OPENFAAS_URL=http://openfaas.endpoint.com:8080`. This is already set in [Lab 1](./lab1.md) if you are following the Kubernetes instructions.
2. Specify the correct endpoint inline with the `-g` or `--gateway` flag: `faas deploy --gateway http://openfaas.endpoint.com:8080`
3. In your deployment YAML file, change the value specified by the `gateway:` object under `provider:`.

### List the deployed functions

This will show the functions, how many replicas you have and the invocation count.

```sh
$ faas-cli list
```

You should see the *markdown* function as `markdown` and the *figlet* function listed too along with how many times you've invoked them.

Now try the verbose flag

```sh
$ faas-cli list --verbose
```
or

```sh
$ faas-cli list -v
```

You can now see the Docker image along with the names of the functions.

### Invoke a function

Pick one of the functions you saw appear on `faas-cli list` such as `markdown`:

```sh
$ faas-cli invoke markdown
```

You'll now be asked to type in some text. Hit Control + D when you're done.

Alternatively you can use a command such as `echo` or `uname -a` as input to the `invoke` command which works through the use of pipes.

```sh
$ echo Hi | faas-cli invoke markdown

$ uname -a | faas-cli invoke markdown
```

You can even generate a HTML file from this lab's markdown file with the following:

```sh
$ git clone https://github.com/openfaas/workshop \
   && cd workshop

$ cat lab2.md | faas-cli invoke markdown
```

NEXT: [Exercise 2: Creating Functions](./creating-functions.md)
