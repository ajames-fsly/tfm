# tfm copy workspaces

`tfm copy workspaces` or `tfm copy ws` creates a workspaces from source to destination org.

After the workspaces are created at the destination, the next step is to copy the rest of the workspaces settings such as [state](copy_workspace_state.md), [variables](copy_workspace_variables.md), [team access](copy_workspace_teamaccess.md) etc using `tfm copy workspace` flags.  


`tfm copy workspaces -h`

```bash
Copy Workspaces from source to destination org

Usage:
  tfm copy workspaces [flags]

Aliases:
  workspaces, ws

Flags:
      --agents                Mapping of source Agent Pool IDs to destination Agent Pool IDs in config file
  -h, --help                  help for workspaces
      --ssh                   Mapping of source ssh id to destination ssh id in config file
      --state                 Copy workspace states
      --teamaccess            Copy workspace Team Access
      --vars                  Copy workspace variables
      --vcs                   Mapping of source vcs Oauth ID to destination vcs Oath in config file
      --workspace-id string   Specify one single workspace ID to copy to destination

Global Flags:
      --config string   Config file, can be used to store common flags, (default is ./.tfm.hcl).
```



## Copy ALL workspaces

Without providing any flags, `tfm copy workspaces` will copy all source workspaces and create them in the destination organization.



## Copy a list of workspaces

As part of the HCL config file (`/home/user/.tfm.hcl`), a list of workspaces from the source TFE can be specified. `tfm` will use this list when running `tfm copy workspaces` and ensure the workspace exists or is created in the target.

``` terraform
#List of Workspaces to create/check are migrated across to new TFC
"workspaces" = [
  "appAFrontEnd",
  "appABackEnd",
  "appBDataLake",
  "appBInfra"
]

```

## Rename Workspaces in destination during a copy

As part of the HCL config file (`/home/user/.tfm.hcl`), a list of `source-workspace-name=destination-workspace-name` can be provided. `tfm` will use this list when running `tfm copy workspace` to look at all workspaces in the source host and rename the destination workspace name. 


!!! note ""
    *NOTE: Using the 'workspace-map' configuration in your HCL config file will take precedence over the other 'workspaces' list feature which only lists source workspace names.*

```terraform
# A list of source=destination workspace names. TFM will look at each source workspace and recreate the workspace with the specified destination name.
"workspace-map" = [
   "tf-demo-workflow=dst-demo-workflow",
   "api-test=dst-api-test"
   ]
```

