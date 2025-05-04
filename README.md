# Robograph Project Planning

Planning, work tracking, design, and discussion for Robograph Project

## About Robograph Project

A collection of repositories with the goal of providing a declarative specification framework for robotics sotfware projects.

Focused primarily on, but not limited to
1. ROS 2 applications
2. running on a single computer host

This repository and README tracks new development and notes on preexisting tools.

See [the backlog](https://github.com/orgs/robograph-project/projects/1) for an overview of work in progress.

## Motivation

Imperative and dynamic application graphs allow for misconfiguration that cannot be discovered until either a complex integration test run or actual runtime.

In most cases, the full desired state of the graph is actually known by the developer before running a build. The goal is to declare most of these values ahead of time instead of creating them imperatively at runtime.

This could give us the following benefits:
- Automate setup to reduce boilerplate and inconsistency
- Autogenerate documentation so that configuration and interfaces for all components of the application are clear without getting out of sync or requiring constant developer effort, just as in a Doxygen API
- Perform simple graph analysis to pre-detect basic logical errors: Topic mismatches (types, QoS) & graph discontinuities (unsubscribed/unpublished topics)
- Help understand graph topology at builld time to inform use of components, namespaces, cgroups, etc
- Generate source of truth expectations for runtime health monitoring to validate actual observed graph against


## Topics Of Interest

- [Node configuration](#node-configuration-parameters)
- [Node interface](#node-interface-topics)
- [Graph specification](#graph-specification)
- [Graph configuration](#graph-configuration)

### Node Configuration: Parameters

- Current state of the art is https://github.com/PickNikRobotics/generate_parameter_library
- Adoption/Usage: Medium, definitely being used in the wild

### Node Interface: Topics

- Current state of the art: https://github.com/ubuntu-robotics/nodl
- Adoption/Usage: Low/None

### Graph Specification: Launch

ROS 2 graphs are created dynamically by one or more `launch` files, and user or dynamically-created Nodes.

While the launchfiles are theoretically "somewhat declarative" - given that the Python launch API is by far the most used and the amount of flexibilty that affords makes launchfiles hard/impossible to analyze at build time.

### Graph Configuration

How does one think about configuration an entire application (graph)?

There is not a good answer now.

Consider supporting:
- Default parameters specification
- Layers of overrides with clear precedence, for either sites, vehicle types, individual computers, etc. This renders into a single inspectable configuration artifact for a system to start with.

