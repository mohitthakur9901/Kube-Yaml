## Deployment Configuration

The `deployment.yaml` file contains the configuration for the Pod with two containers:

1. **Main Application Container (`main-app`)**:

   - **Image**: `my-main-app-image:latest`
   - **Purpose**: Generates log entries.
   - **VolumeMount**: Mounts a shared volume at `/var/log` to store log files.

2. **Sidecar Container (`log-collector`)**:

   - **Image**: `my-log-collector-image:latest`
   - **Purpose**: Collects logs from the main container and writes them to a separate log file.
   - **VolumeMount**: Also mounts the shared volume at `/var/log`.

3. **Shared Volume (`log-volume`)**:
   - **Type**: `emptyDir`
   - **Purpose**: Provides a shared directory between the main and sidecar containers.

## Steps to Deploy

1. **Save the YAML Configuration**: Ensure that the `deployment.yaml` file is in your working directory.

2. **Apply the Configuration**:

   ```sh
   kubectl apply -f deployment.yaml
   
   kubect get pods

   kubectl logs <pod-name> -c log-collector

   kubectl logs <pod-name> -c main-app
   ```

```
This README file provides instructions for setting up and using the sidecar container to collect logs from the main application container. You can adjust the container images and commands based on your specific use case and application requirements.
```
