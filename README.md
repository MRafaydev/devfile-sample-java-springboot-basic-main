kind: BuildConfig
apiVersion: build.openshift.io/v1
metadata:
  annotations:
    app.openshift.io/vcs-ref: ''
    app.openshift.io/vcs-uri: 'https://github.com/MRafaydev/devfile-sample-java-springboot-basic-main'
    openshift.io/generated-by: OpenShiftWebConsole
  resourceVersion: '2110815399'
  name: devfile-sample-java-springboot-basic-main
  uid: ec73d3bf-854d-48e4-8395-078e0e04c5e5
  creationTimestamp: '2023-02-23T11:20:28Z'
  generation: 5
  managedFields:
    - manager: Mozilla
      operation: Update
      apiVersion: build.openshift.io/v1
      time: '2023-02-23T11:22:31Z'
      fieldsType: FieldsV1
      fieldsV1:
        'f:metadata':
          'f:annotations':
            .: {}
            'f:app.openshift.io/vcs-ref': {}
            'f:app.openshift.io/vcs-uri': {}
            'f:openshift.io/generated-by': {}
          'f:labels':
            .: {}
            'f:app': {}
            'f:app.kubernetes.io/component': {}
            'f:app.kubernetes.io/instance': {}
            'f:app.kubernetes.io/name': {}
            'f:app.kubernetes.io/part-of': {}
        'f:spec':
          'f:output':
            'f:to': {}
          'f:runPolicy': {}
          'f:source':
            'f:contextDir': {}
            'f:git':
              .: {}
              'f:uri': {}
            'f:type': {}
          'f:strategy':
            'f:dockerStrategy':
              .: {}
              'f:dockerfilePath': {}
              'f:env': {}
            'f:type': {}
          'f:triggers': {}
    - manager: openshift-apiserver
      operation: Update
      apiVersion: build.openshift.io/v1
      time: '2023-02-23T11:31:44Z'
      fieldsType: FieldsV1
      fieldsV1:
        'f:status':
          'f:lastVersion': {}
  namespace: at-rafay765-dev
  labels:
    app: devfile-sample-java-springboot-basic-main
    app.kubernetes.io/component: devfile-sample-java-springboot-basic-main
    app.kubernetes.io/instance: devfile-sample-java-springboot-basic-main
    app.kubernetes.io/name: devfile-sample-java-springboot-basic-main
    app.kubernetes.io/part-of: sample-app
spec:
  nodeSelector: null
  output:
    to:
      kind: ImageStreamTag
      name: 'devfile-sample-java-springboot-basic-main:latest'
  resources: {}
  successfulBuildsHistoryLimit: 5
  failedBuildsHistoryLimit: 5
  strategy:
    type: Docker
    dockerStrategy:
      env:
        - name: CACHE_DIR
          value: /tmp/cache
        - name: CACHE_IMAGE_NAME
          value: 'my-cache-image:latest'
      dockerfilePath: docker/Dockerfile
  postCommit: {}
  source:
    type: Git
    git:
      uri: 'https://github.com/MRafaydev/devfile-sample-java-springboot-basic-main'
    contextDir: /
  triggers:
    - type: Generic
      generic:
        secretReference:
          name: devfile-sample-java-springboot-basic-main-generic-webhook-secret
    - type: GitHub
      github:
        secretReference:
          name: devfile-sample-java-springboot-basic-main-github-webhook-secret
    - type: ConfigChange
  runPolicy: Serial
status:
  lastVersion: 3
