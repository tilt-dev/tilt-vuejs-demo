repo = local_git_repo('.')

k8s_yaml('serve.yaml')

# Start with a base Dockerfile with none of our source code,
# and an entry point that starts a server.

docker_build('tilt-vuejs-demo', '.',
  live_update=[
    # when package.json changes, we need to do a full build
    fall_back_on(['package.json', 'package-lock.json']),
    # Map the local source code into the container under /app
    sync('.', '/app'),
  ])

k8s_resource('tilt-vuejs-demo', port_forwards=8080)
