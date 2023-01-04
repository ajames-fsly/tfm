# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased] (November 24, 2022)

**Added**
- initial repository layout/boiler plate created
- copy teams subcommand
- list orgs subcommand
- list teams subcommand


**Changed**
- structure of `cmd` and its subcommands. Each sub command is now its in own directory and considered a package the `cmd` package imports in. 
- `tfclient` pkg created at top level, not related to `cmd` package 

**Removed**