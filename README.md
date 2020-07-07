# Notes

$ sfdx force:source:retrieve -m "Flow" -u workdc_poc_wdc
$ sfdx force:source:retrieve -m "ExternalDataSource" -u workdc_poc_wdc


# Work.com and Command Center
Where can I get more information about work.com?

For Partners: Go to Work.com for AppExchange Partners Partner Community Chatter Group  : https://partners.salesforce.com/_ui/core/chatter/groups/GroupProfilePage?g=0F93A000000TygB

## What is this repo?
This repo can quickly get you started with Work.com and Command Center managed package(s). Following is what will be included in this repo:
- Work.com PSL (Check config file: https://github.com/forcedotcom/WorkDotCom-Partners/blob/master/config/project-scratch-def.json)
- Command Center Managed Package
- Command Center Un-Managed Package (Emmployee Wellness Survey Templates)
- Quick Start Permission Sets (Make sure to review those as needed)


## How can I use this repo?

1. You can do this locally
   - Clone this project locally:
   - git clone https://github.com/forcedotcom/WorkDotCom-Partners.git
     - Run orgInit.sh file: Check https://github.com/forcedotcom/WorkDotCom-Partners/blob/master/orgInit.sh for commands
     - ./orgInit.sh
2. You can use this via Heroku Deployer because this repo is ADK ready: https://salesforce.quip.com/S6ZvAvaxI1CV

## Does this repo contain test data?
Yes. There are test data scripts for work.com data model objects. You can manually load this data as per https://github.com/forcedotcom/WorkDotCom-Partners/blob/master/dx-utils/load_test_data.sh. Please note that test data will be automatically loaded if you run ./orgInit.sh

## How can view Command Center?
Once your org is ready, you can open "Command Center" app to view default dashboard.

## Will Command Center be completely configured?
No. This repo provides minimum setup needed to view Command Center dashboard (managed package installation, permission set assignment and test data).

If you want to view other components (like Employee Wellness, Surveys, Community for Surveys etc) then you need to go through Command Center Setup guide. One reason is because many steps are not available via metadata and SFDX. For example, Survey and Community link, default page layout assignments etc

Please note extra permissionsets in force-app/main/default/permissionsets
  - Most of those are the same permission from setup guide so you can skip those steps and get right into configuration
  - Let us know if any permission is missing
  - Do not use these in an active org with real user data without reviewing all the permissions


## Are there any sample apps that can help me build an app for work.com?
Appiphony, a PDO, has built an app that you can use to check for code samples. https://github.com/appiphony/building-management-app

We have created custom version of "Command Center" App's Home page and pre-added Appiphony components. You can use above repo to look at the source.

## Can ISVs check what features they may have used in their packages?

Yes, you can check that using ISV TE DX Plugin. ISV TE DX plugin has been updated to look for work.com object usage when you add custom fields on those objects. You will be able to see if your package has added any work.com data model dependencies.

To Install or update the plugin: sfdx plugins:install isvte-sfdx-plugin

When executed against a package with depends on Work.com you will see output similar to:

Feature and License Dependencies:

  Work.com

More information about this plugin can be found at https://medium.com/inside-the-salesforce-ecosystem/build-better-apps-for-your-customers-with-this-new-dx-plug-in-4877fa0fc305


## How can I manually use Test Data Scripts
Sometimes you may want to load test data in existing org. You can run these data scripts using dx-utils/load_test_data.sh.

You will need "testdata" and "dx-utils/apex-scripts" directories and run following commands.

sfdx force:data:tree:import -p ./testdata/InternalOrganizationUnit-Employee-EmployeeCrisisAssessment-plan.json

sfdx force:apex:execute -f ./dx-utils/apex-scripts/updateLocationVisitorAddressId.apex


Please note that we only have Test Data for following objects.

Test data is for following objects
- Location (Core)
- Employee (Core)
- EmployeeCrisisAssessment (Core)
- Internal Organization Unit (Core)
