# Thunderstore Mod CI

This is a templatable CI that will 

1. Automatically generate and upload a thunderstore mod on creation of a release branch using semver (release/x.x.x)
2. Once pushed to thunderstore, the pipeline runs on an hourly cron and will update the dependencies, push a new patch release branch, and upload that to thunderstore with the patch version.

## Requirements 

1. Update mod.json with the necessary parameters, such that 
```
"name" is the name of the mod, as a string
"author_name" is the name of the author, as a string
"has_nsfw_content" is a boolean true or false
"categories" is an array of categories which can be grabbed from here https://thunderstore.io/api/experimental/community/{community}/category/
"communities" is an array of communities which can be grabbed from here https://thunderstore.io/api/experimental/community/
"website_url" is the url to a website, as a string
"description" is the description for your mod, as a string
"dependencies" is an array of json objects containing a name and author for all dependencies
```

2. Put your own icon.png (256x256) in resources/ 

3. You must add a repository secret under Settings > Secrets and variables > Actions > Repository secret with your Thunderstore service account token which can be generated here https://thunderstore.io/settings/teams/{team}/service-accounts/

4. Your GitHub actions runner should have the permission to "Allow all actions and reusable workflows" under Settings > Actions > General
