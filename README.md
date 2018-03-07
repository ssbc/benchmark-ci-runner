# Benchmark ci runner

This repo contains code for running benchmarks. It uses the
[nci](https://github.com/node-ci/nci) framework.

## Usage

After installation you can run the following command to continuously
look for changes:

  node_modules/.bin/forever start -l `pwd`/app.log -a node_modules/.bin/nci

Or for a single go, just

  node_modules/.bin/nci

A web UI should be available here for viewing the results:

http://localhost:3000/

Builds can be triggered from the UI, or from command line:

curl http://127.0.0.1:3000/api/0.1/builds -d '{"project": "benchmark-ci"}'

A specific revision can be built using:

curl http://127.0.0.1:3000/api/0.1/builds -d '{"project": "benchmark-ci", "buildParams": { "scmRev": "dfe086054e984f5bdf31331f26173c8e03239618" } }'

Nci uses the current node version when running, so if you want to run
the benchmarks with a different node version use nvm first.

## Configuration

Projects are configured using config.yaml files. Currently only
bench-ssb is configured in the data/projects/bench-ssb/config.yaml.
