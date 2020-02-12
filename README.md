# git-versioning
.Net Core with GitVersion

Run commands to set Assmebly Version as environment variable so it can be used by CI/CD

```
	dotnet-gitversion > gitversion.txt
	sed -i '1d;26d;s/  //;s/"//g;s/,//;s/:/=/' gitversion.txt
	export $(grep AssemblySemVer gitversion.txt | xargs)	
```
