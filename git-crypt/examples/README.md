# git-crypt builder

This builder can be used to execute simple git-crypt commands.

This assumes you have already built the `git-crypt` build step and pushed it to
`gcr.io/$PROJECT_ID/git-crypt`.

## Executing the builder

Inside this directory, run the following command:

```
gcloud container builds submit --config=cloudbuild.yaml .
```

The encrypted "secret.txt" file will be unencrypted.