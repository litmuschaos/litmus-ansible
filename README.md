# litmus-ansible

[![Slack Channel](https://img.shields.io/badge/Slack-Join-purple)](https://slack.litmuschaos.io)
![GitHub Workflow](https://github.com/litmuschaos/litmus-ansible/actions/workflows/build.yml/badge.svg?branch=master)
[![Docker Pulls](https://img.shields.io/docker/pulls/litmuschaos/ansible-runner.svg)](https://hub.docker.com/r/litmuschaos/ansible-runner)
[![GitHub issues](https://img.shields.io/github/issues/litmuschaos/litmus-ansible)](https://github.com/litmuschaos/litmus-ansible/issues)
[![Twitter Follow](https://img.shields.io/twitter/follow/litmuschaos?style=social)](https://twitter.com/LitmusChaos)
[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/5300/badge)](https://bestpractices.coreinfrastructure.org/projects/5300)
[![YouTube Channel](https://img.shields.io/badge/YouTube-Subscribe-red)](https://www.youtube.com/channel/UCa57PMqmz_j0wnteRa9nCaw)
<br><br>

This repo consists of Litmus Chaos Experiments written as ansible playbooks. The examples in this repo are good indicators 
of how to construct the experiments in ansible: complete with steady state checks, chaosresult generation, chaos injection,
post chaos checks, event & and reports generation etc.,   

**NOTE**

- litmus-ansible is very similar in purpose to and therefore a sister repo of [litmus-python](https://github.com/litmuschaos/litmus-python) & [litmus-go](https://github.com/litmuschaos/litmus-go) which contain experiment business logic written in python & golang respectively.

## Litmus SDK

The Litmus SDK provides a simple way to bootstrap your experiment and helps create the aforementioned artifacts in the appropriate directory (i.e., as per the chaos-category) based on an attributes file provided as input by the chart-developer. The scaffolded files consist of placeholders which can then be filled as desired.

It generates the custom chaos experiments with some default Pre & Post Chaos Checks (AUT & Auxiliary Applications status checks). It can use the existing chaoslib (present inside /chaoslib directory), if available else It will create a new chaoslib inside the corresponding directory.

Refer [Litmus-SDK](https://github.com/litmuschaos/litmus-ansible/blob/master/contribute/developer_guide/README.md) for more details.

## How to get started?

Refer the LitmusChaos documentation [litmus docs](https://docs.litmuschaos.io)

## How do I contribute?

You can contribute by raising issues, improving the documentation, contributing to the core framework and tooling, etc.

Head over to the [Contribution guide](CONTRIBUTING.md)

