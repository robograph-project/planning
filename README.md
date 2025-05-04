# Robograph Project Planning

Planning, work tracking, design, and discussion for Robograph Project

## About Robograph Project

A collection of repositories with the goal of providing a declarative specification framework for robotics sotfware projects.

Focused primarily on
1. ROS 2 applications
2. running on a single computer host

This is an idea in active evolution.

This repository and README tracks new development and notes on preexisting tools to meet the following goals.

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

### Graph Specification

Currently the ROS 2 launch system is the way that this is handled.

While the launchfiles are theoretically "somewhat declarative" - given that the Python launch API is by far the most used and the amount of flexibilty that affords makes launchfiles hard/impossible to analyze at build time.

### Graph Configuration

The ability to have glabal-default parameterss, with group- & individual-level overrides to generate a tree of configuration that renders into one global parameter spec for a concrete application, that could be analyzed ahead of time for type consistency and general debugging introspection.

