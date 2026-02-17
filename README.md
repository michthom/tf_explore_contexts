# Exploring GitHub Contexts

A simple action to report on the state of various contexts for corresponding GitHub events.

| Workflow | Trigger Event | base_ref | environment set to | Action to perform | 
| - | - | - | - | - |
| 00_Plan_only | Pull Request (not closed) | dev | dev | Terraform plan all layers |
| 00_Plan_only | Pull Request (not closed) | main | stg | Terraform plan all layers |
| 10_Apply_changes | Pull Request (closed and merged) | dev | dev | Terraform apply all layers with auto-approve |
| 10_Apply_changes | Pull Request (closed and merged) | main | stg | Terraform apply all layers with auto-approve |
| 20_Deploy_production | Release published | main | prd | Terraform plan and then approve layers in turn with auto approve |
| Reusable_Terraform_workflow | workflow_call | any | any | any |

| Workflow | Selected environment | Action to perform | base_ref set to |
| - | - | - | - |
| Manual | dev | plan |  HEAD of dev branch |
| Manual | dev | apply | HEAD of dev branch |
| Manual | dev | destroy | HEAD of dev branch |
| Manual | stg | plan | HEAD of main branch |
| Manual | stg | apply | HEAD of main branch |
| Manual | stg | destroy | HEAD of main branch |
| Manual | prd | plan    | Latest Release tag on main branch |
| Manual | prd | apply   | Latest Release tag on main branch |
| Manual | prd | destroy | Latest Release tag on main branch |
