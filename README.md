# envsubst-docker

A small Docker image with the [`envsubst`](https://linux.die.net/man/1/envsubst) utility.

This may be useful as an `initContainer` for a Kubernetes deployment, to inject secrets into configuration files for applications that don't support reading them from the environment. See [kubernetes/kubernetes#79224](http://github.com/kubernetes/kubernetes/issues/79224) for more.

## Usage

The entrypoint of this image is `/bin/sh -c`.

```console
$ docker run bfogarty/envsubst "envsubst --help"

Usage: envsubst [OPTION] [SHELL-FORMAT]

Substitutes the values of environment variables.

Operation mode:
  -v, --variables             output the variables occurring in SHELL-FORMAT

Informative output:
  -h, --help                  display this help and exit
  -V, --version               output version information and exit

In normal operation mode, standard input is copied to standard output,
with references to environment variables of the form $VARIABLE or ${VARIABLE}
being replaced with the corresponding values.  If a SHELL-FORMAT is given,
only those environment variables that are referenced in SHELL-FORMAT are
substituted; otherwise all environment variables references occurring in
standard input are substituted.

When --variables is used, standard input is ignored, and the output consists
of the environment variables that are referenced in SHELL-FORMAT, one per line.

Report bugs in the bug tracker at <https://savannah.gnu.org/projects/gettext>
or by email to <bug-gettext@gnu.org>.
```
