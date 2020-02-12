# git-versioning
.Net Core with GitVersion

Run commands to set Assmebly Version as environment variable so it can be used by CI/CD

```
	dotnet-gitversion > gitversion.json
```
extract the variable as the following
```
	
	sed -i '1d;26d;s/  //;s/"//g;s/,//;s/:/=/' gitversion.json
	export $(grep AssemblySemVer gitversion.json | xargs)
```
or you can use jq as
```
	cat gitversion.json
        apt update
        apt install -y jq
        export MajorMinorPatch=$(jq -r '.MajorMinorPatch' gitversion.json)
        export BuildMetaData=$(jq -r '.BuildMetaData' gitversion.json)
        export PreReleaseTag=$(jq -r '.PreReleaseTag' gitversion.json)
```
