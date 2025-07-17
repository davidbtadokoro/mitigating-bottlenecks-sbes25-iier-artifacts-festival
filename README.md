# Linux statistics

A repository to reproducibly generate some statistics about Linux kernel
development. The statistics generated are physical lines of code, maintainers,
and commits across Linux versions; these are outputted as a CSV and as plots.

This is a modified version of the original repository to fit
the requirements for the **Available** and **Functional** badges as described in
the [call for the Artifacts Festival of CBSoft
2025](https://cbsoft.sbc.org.br/2025/artefatos/?lang=en).

### Repository organization

- `README.md`: README file
- `LICENSE`: file containing the project license, the *GNU General Public License Version 3* (GPL-3.0)
- `pre-print.pdf`: PDF file with pre-print version of the paper
- `Dockerfile`: recipe for container that generates statistics 
- `docker-compose.yaml`: file to configure container
- `run_experiments.sh`: script that effectively executes experiments and generates the data
- `utils.sh`: file with utilities for experiments
- `plot.py`: script to produce plots from generated data

### Requirements

To run the containerized application, you need `docker` and `docker-compose`
installed on your system. The image and container created after running the
application occupy around 5 GB of disk space.

There are no hardware requirements, yet, as the experiments demand a heavy load
on the CPU, the more powerful the CPU, the faster they will run. Also, due to
the cloning of the mainline, a good Internet connection is recommended.

### How to run experiments

With the docker daemon running and at the root of the repository, run the below
command to create and execute the image (ensuring it is a fresh container)

```shell
docker-compose up --force-recreate
```

The `data.csv` and the plots in `.pdf` format will be created at
`linux-stats/output/`.

By default, the version span is from v3.19 to v6.13. Unfortunately, to customize
this, you will need to adjust the `CMD` directive in the `Dockerfile`.
