# CloudBees Sample Go App

This is a simple demo app that can be used to identify the different build versions of the application as well as the environment they are running in.  

## Prerequisites

- Go 1.18 or newer
- (Optional) Docker

## Install Dependencies

```
go get github.com/gin-gonic/gin
go get github.com/rollout/rox-go/v5/server
```

## How to Build

A Dockerfile is included so you can build container images. Alternatively, you can use Go to build it:

```
go build -o demo-app
```

## How to Run

1. Create a `sha.txt` file in the project root with your commit SHA or any string:
   ```
   echo "dummysha123456" > sha.txt
   ```
2. (Optional) Set the `ENVIRONMENT` environment variable to alter the name that appears in the application:
   ```
   export ENVIRONMENT=production
   ```
3. Run the app:
   ```
   ./demo-app
   ```

The app will be available at http://localhost:8080

## Feature Flags

This app uses the CloudBees/Rox feature flag SDK. The color logic is controlled by the `EnableTutorial` flag. If the flag is enabled, the color is generated from the SHA; otherwise, a default gray color (`#CCCCCC`) is used.

## .gitignore

A `.gitignore` file is included to exclude binaries, logs, editor files, and more. Uncomment `sha.txt` in `.gitignore` if you do not want to commit it.

## Notes
- If you see an error about `sha.txt` missing, create the file as described above.
- For more info on feature flags, see the [CloudBees documentation](https://docs.cloudbees.com/docs/feature-management/latest/).
