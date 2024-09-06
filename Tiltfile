# Permitir el contexto de Kubernetes 'polar'
allow_k8s_contexts('polar')

# Build
custom_build(
    # Name of the container image
    ref = 'erojas14ths/cf-config-service',
    # Command to build the container image
    # On Windows, replace $EXPECTED_REF with %EXPECTED_REF%
    command = 'gradle bootBuildImage --imageName %EXPECTED_REF%',
    # Files to watch that trigger a new build
    deps = ['build.gradle', 'src']
)

# Deploy
k8s_yaml(['k8s/deployment.yml', 'k8s/service.yml'])

# Manage
k8s_resource('cf-config-service', port_forwards=['8888'])
