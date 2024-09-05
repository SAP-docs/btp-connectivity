<!-- loio8f5dd89fb3d349ab81282d0ee33f4f8e -->

# Installation with Operator

Use the operator to install the transparent proxy for Kubernetes.



<a name="loio8f5dd89fb3d349ab81282d0ee33f4f8e__section_dxy_ypw_hcc"/>

## Install/Upgrade

The transparent proxy operator can be installed/upgraded in any Kubernetes cluster using the following yaml configuration:

**operator.yaml**

```
apiVersion: v1
kind: Namespace
metadata:
  labels:
    app.kubernetes.io/component: manager
    app.kubernetes.io/created-by: sap-transp-proxy-operator
    app.kubernetes.io/instance: system
    app.kubernetes.io/managed-by: kustomize
    app.kubernetes.io/name: namespace
    app.kubernetes.io/part-of: sap-transp-proxy-operator
    control-plane: operator
  name: sap-transp-proxy-system
---
apiVersion: apiextensions.k8s.io/v1
kind: CustomResourceDefinition
metadata:
  name: destinations.destination.connectivity.api.sap
spec:
  group: destination.connectivity.api.sap
  names:
    kind: Destination
    listKind: DestinationList
    plural: destinations
    shortNames:
    - dst
    singular: destination
  scope: Namespaced
  versions:
  - additionalPrinterColumns:
    - jsonPath: .metadata.creationTimestamp
      name: Age
      type: date
    - description: The name of the referenced destination from destination service
      jsonPath: .spec.destinationRef.name
      name: DestinationRef
      type: string
    - description: The name of the referenced fragment from destination service
      jsonPath: .spec.fragmentRef.name
      name: FragmentRef
      type: string
    - description: The name of the destination service instance that is used
      jsonPath: .spec.destinationServiceInstanceName
      name: DestinationServiceInstanceName
      type: string
    - jsonPath: .status.conditions[-1].reason
      name: Status
      type: string
    name: v1
    schema:
      openAPIV3Schema:
        properties:
          spec:
            properties:
              destinationRef:
                properties:
                  name:
                    type: string
                required:
                - name
                type: object
              destinationServiceInstanceName:
                type: string
              fragmentRef:
                properties:
                  name:
                    type: string
                type: object
              service:
                properties:
                  port:
                    maximum: 65535
                    minimum: 1
                    type: integer
                type: object
            required:
            - destinationRef
            type: object
          status:
            properties:
              conditions:
                items:
                  properties:
                    lastUpdateTime:
                      type: string
                    message:
                      type: string
                    reason:
                      type: string
                    status:
                      pattern: ^(True|False|Unknown)$
                      type: string
                    type:
                      type: string
                  type: object
                type: array
              tenants:
                items:
                  properties:
                    tenantSubdomain:
                      type: string
                  type: object
                type: array
            type: object
        type: object
    served: true
    storage: true
---
apiVersion: apiextensions.k8s.io/v1
kind: CustomResourceDefinition
metadata:
  annotations:
    controller-gen.kubebuilder.io/version: v0.10.0
  creationTimestamp: null
  name: transparentproxies.operator.kyma-project.io
spec:
  group: operator.kyma-project.io
  names:
    kind: TransparentProxy
    listKind: TransparentProxyList
    plural: transparentproxies
    shortNames:
    - tp
    singular: transparentproxy
  scope: Namespaced
  versions:
  - name: v1alpha1
    schema:
      openAPIV3Schema:
        description: TransparentProxy is the Schema for the transparentproxies API
        properties:
          apiVersion:
            description: 'APIVersion defines the versioned schema of this representation
              of an object. Servers should convert recognized schemas to the latest
              internal value, and may reject unrecognized values. More info: https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#resources'
            type: string
          kind:
            description: 'Kind is a string value representing the REST resource this
              object represents. Servers may infer this from the endpoint the client
              submits requests to. Cannot be updated. In CamelCase. More info: https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#types-kinds'
            type: string
          metadata:
            type: object
          spec:
            description: TransparentProxySpec defines the desired state of TransparentProxy
            properties:
              config:
                properties:
                  integration:
                    properties:
                      connectivityProxy:
                        properties:
                          connectionTimeoutSeconds:
                            type: integer
                          httpPort:
                            type: integer
                          serviceCredentials:
                            properties:
                              privateKey:
                                properties:
                                  secretInternalKey:
                                    type: string
                                  secretName:
                                    type: string
                                type: object
                              secretKey:
                                type: string
                              secretName:
                                type: string
                              secretNamespace:
                                type: string
                            type: object
                          serviceName:
                            type: string
                          tcpPort:
                            type: integer
                        type: object
                      destinationService:
                        properties:
                          connectionTimeoutSeconds:
                            type: integer
                          defaultInstanceName:
                            type: string
                          instances:
                            items:
                              properties:
                                associateWith:
                                  properties:
                                    connectivityProxy:
                                      properties:
                                        locallyConfiguredRegionId:
                                          type: string
                                      required:
                                      - locallyConfiguredRegionId
                                      type: object
                                  required:
                                  - connectivityProxy
                                  type: object
                                name:
                                  type: string
                                serviceCredentials:
                                  properties:
                                    privateKey:
                                      properties:
                                        secretInternalKey:
                                          type: string
                                        secretName:
                                          type: string
                                      type: object
                                    secretKey:
                                      type: string
                                    secretName:
                                      type: string
                                    secretNamespace:
                                      type: string
                                  type: object
                              required:
                              - name
                              - serviceCredentials
                              type: object
                            type: array
                          readTimeoutSeconds:
                            type: integer
                        type: object
                      serviceMesh:
                        properties:
                          istio:
                            properties:
                              istio-injection:
                                type: string
                            type: object
                        type: object
                    type: object
                  logging:
                    properties:
                      level:
                        type: string
                    type: object
                  managedNamespacesMode:
                    type: string
                  manager:
                    properties:
                      executionIntervalMinutes:
                        type: integer
                    type: object
                  security:
                    properties:
                      accessControl:
                        properties:
                          destinations:
                            properties:
                              defaultScope:
                                type: string
                            type: object
                        type: object
                      communication:
                        properties:
                          internal:
                            properties:
                              certManager:
                                properties:
                                  certificate:
                                    properties:
                                      duration:
                                        type: string
                                      privateKey:
                                        properties:
                                          algorithm:
                                            type: string
                                          encoding:
                                            type: string
                                          size:
                                            type: integer
                                        type: object
                                      renewBefore:
                                        type: string
                                    type: object
                                  issuerRef:
                                    properties:
                                      kind:
                                        type: string
                                      name:
                                        type: string
                                      namespace:
                                        type: string
                                    type: object
                                type: object
                              encryptionEnabled:
                                type: boolean
                            type: object
                        type: object
                    type: object
                  tenantMode:
                    type: string
                type: object
              deployment:
                properties:
                  autoscaling:
                    properties:
                      http:
                        properties:
                          horizontal:
                            properties:
                              enabled:
                                type: boolean
                              maxReplicaCount:
                                type: integer
                              metrics:
                                properties:
                                  cpuAverageUtilization:
                                    type: integer
                                  memoryAverageUtilization:
                                    type: integer
                                type: object
                            type: object
                          vertical:
                            properties:
                              enabled:
                                type: boolean
                              maxAllowed:
                                properties:
                                  cpu:
                                    type: number
                                  memory:
                                    type: string
                                type: object
                              minAllowed:
                                properties:
                                  cpu:
                                    type: number
                                  memory:
                                    type: string
                                type: object
                              updateMode:
                                type: string
                            type: object
                        type: object
                      tcp:
                        properties:
                          horizontal:
                            properties:
                              enabled:
                                type: boolean
                              maxReplicaCount:
                                type: integer
                              metrics:
                                properties:
                                  cpuAverageUtilization:
                                    type: integer
                                  memoryAverageUtilization:
                                    type: integer
                                type: object
                            type: object
                          vertical:
                            properties:
                              enabled:
                                type: boolean
                              maxAllowed:
                                properties:
                                  cpu:
                                    type: number
                                  memory:
                                    type: string
                                type: object
                              minAllowed:
                                properties:
                                  cpu:
                                    type: number
                                  memory:
                                    type: string
                                type: object
                              updateMode:
                                type: string
                            type: object
                        type: object
                    type: object
                  image:
                    properties:
                      pullPolicy:
                        type: string
                      pullSecret:
                        type: string
                      registry:
                        type: string
                      repository:
                        type: string
                      tag:
                        type: string
                    type: object
                  replicas:
                    properties:
                      http:
                        type: integer
                      tcp:
                        type: integer
                    type: object
                  resources:
                    properties:
                      http:
                        properties:
                          limits:
                            properties:
                              cpu:
                                type: number
                              memory:
                                type: string
                            type: object
                          requests:
                            properties:
                              cpu:
                                type: number
                              memory:
                                type: string
                            type: object
                        type: object
                      tcp:
                        properties:
                          limits:
                            properties:
                              cpu:
                                type: number
                              memory:
                                type: string
                            type: object
                          requests:
                            properties:
                              cpu:
                                type: number
                              memory:
                                type: string
                            type: object
                        type: object
                    type: object
                type: object
            type: object
          status:
            description: TransparentProxyStatus defines the observed state of TransparentProxy
            properties:
              conditions:
                items:
                  description: "Condition contains details for one aspect of the current
                    state of this API Resource. --- This struct is intended for direct
                    use as an array at the field path .status.conditions.  For example,
                    \n type FooStatus struct{ // Represents the observations of a
                    foo's current state. // Known .status.conditions.type are: \"Available\",
                    \"Progressing\", and \"Degraded\" // +patchMergeKey=type // +patchStrategy=merge
                    // +listType=map // +listMapKey=type Conditions []metav1.Condition
                    `json:\"conditions,omitempty\" patchStrategy:\"merge\" patchMergeKey:\"type\"
                    protobuf:\"bytes,1,rep,name=conditions\"` \n // other fields }"
                  properties:
                    lastTransitionTime:
                      description: lastTransitionTime is the last time the condition
                        transitioned from one status to another. This should be when
                        the underlying condition changed.  If that is not known, then
                        using the time when the API field changed is acceptable.
                      format: date-time
                      type: string
                    message:
                      description: message is a human readable message indicating
                        details about the transition. This may be an empty string.
                      maxLength: 32768
                      type: string
                    observedGeneration:
                      description: observedGeneration represents the .metadata.generation
                        that the condition was set based upon. For instance, if .metadata.generation
                        is currently 12, but the .status.conditions[x].observedGeneration
                        is 9, the condition is out of date with respect to the current
                        state of the instance.
                      format: int64
                      minimum: 0
                      type: integer
                    reason:
                      description: reason contains a programmatic identifier indicating
                        the reason for the condition's last transition. Producers
                        of specific condition types may define expected values and
                        meanings for this field, and whether the values are considered
                        a guaranteed API. The value should be a CamelCase string.
                        This field may not be empty.
                      maxLength: 1024
                      minLength: 1
                      pattern: ^[A-Za-z]([A-Za-z0-9_,:]*[A-Za-z0-9_])?$
                      type: string
                    status:
                      description: status of the condition, one of True, False, Unknown.
                      enum:
                      - "True"
                      - "False"
                      - Unknown
                      type: string
                    type:
                      description: type of condition in CamelCase or in foo.example.com/CamelCase.
                        --- Many .condition.type values are consistent across resources
                        like Available, but because arbitrary conditions can be useful
                        (see .node.status.conditions), the ability to deconflict is
                        important. The regex it matches is (dns1123SubdomainFmt/)?(qualifiedNameFmt)
                      maxLength: 316
                      pattern: ^([a-z0-9]([-a-z0-9]*[a-z0-9])?(\.[a-z0-9]([-a-z0-9]*[a-z0-9])?)*/)?(([A-Za-z0-9][-A-Za-z0-9_.]*)?[A-Za-z0-9])$
                      type: string
                  required:
                  - lastTransitionTime
                  - message
                  - reason
                  - status
                  - type
                  type: object
                type: array
              defaultServiceInstanceInitialized:
                type: boolean
              state:
                description: State signifies current state of Module CR. Value can
                  be one of ("Ready", "Processing", "Error", "Deleting", "Warning").
                enum:
                - Processing
                - Deleting
                - Ready
                - Error
                - Warning
                type: string
            required:
            - state
            type: object
        type: object
    served: true
    storage: true
    subresources:
      status: {}
---
apiVersion: v1
kind: ServiceAccount
metadata:
  labels:
    app.kubernetes.io/component: rbac
    app.kubernetes.io/created-by: sap-transp-proxy-operator
    app.kubernetes.io/instance: operator-sa
    app.kubernetes.io/managed-by: kustomize
    app.kubernetes.io/name: serviceaccount
    app.kubernetes.io/part-of: sap-transp-proxy-operator
  name: sap-transp-proxy-operator
  namespace: sap-transp-proxy-system
---
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  labels:
    app.kubernetes.io/component: rbac
    app.kubernetes.io/created-by: sap-transp-proxy-operator
    app.kubernetes.io/instance: leader-election-role
    app.kubernetes.io/managed-by: kustomize
    app.kubernetes.io/name: role
    app.kubernetes.io/part-of: sap-transp-proxy-operator
  name: sap-transp-proxy-leader-election-role
  namespace: sap-transp-proxy-system
rules:
- apiGroups:
  - ""
  resources:
  - configmaps
  verbs:
  - get
  - list
  - watch
  - create
  - update
  - patch
  - delete
- apiGroups:
  - coordination.k8s.io
  resources:
  - leases
  verbs:
  - get
  - list
  - watch
  - create
  - update
  - patch
  - delete
- apiGroups:
  - ""
  resources:
  - events
  verbs:
  - create
  - patch
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  creationTimestamp: null
  name: sap-transp-proxy-manager-role
rules:
- apiGroups:
  - ""
  resources:
  - configmaps
  - serviceaccounts
  - services
  verbs:
  - '*'
- apiGroups:
  - ""
  resources:
  - events
  verbs:
  - '*'
- apiGroups:
  - ""
  resources:
  - namespaces
  verbs:
  - '*'
- apiGroups:
  - ""
  resources:
  - secrets
  verbs:
  - get
  - list
  - watch
- apiGroups:
  - apiextensions.k8s.io
  resources:
  - customresourcedefinitions
  verbs:
  - '*'
- apiGroups:
  - apps
  resources:
  - deployments
  verbs:
  - '*'
- apiGroups:
  - apps
  resources:
  - replicasets
  verbs:
  - list
- apiGroups:
  - cert-manager.io
  resources:
  - certificates
  verbs:
  - '*'
- apiGroups:
  - cert-manager.io
  resources:
  - clusterissuers
  - issuers
  verbs:
  - get
  - list
  - watch
- apiGroups:
  - cert.gardener.cloud
  resources:
  - certificates
  verbs:
  - '*'
- apiGroups:
  - cert.gardener.cloud
  resources:
  - issuers
  verbs:
  - get
  - list
  - watch
- apiGroups:
  - certificates.cert-manager.io
  resources:
  - customresourcedefinitions
  verbs:
  - get
  - list
  - watch
- apiGroups:
  - certificates.cert.gardener.cloud
  resources:
  - customresourcedefinitions
  verbs:
  - get
  - list
  - watch
- apiGroups:
  - destination.connectivity.api.sap
  resources:
  - destinations
  verbs:
  - create
- apiGroups:
  - networking.k8s.io
  resources:
  - networkpolicies
  verbs:
  - '*'
- apiGroups:
  - operator.kyma-project.io
  resources:
  - transparentproxies
  verbs:
  - '*'
- apiGroups:
  - operator.kyma-project.io
  resources:
  - transparentproxies/finalizers
  verbs:
  - '*'
- apiGroups:
  - operator.kyma-project.io
  resources:
  - transparentproxies/status
  verbs:
  - '*'
- apiGroups:
  - rbac.authorization.k8s.io
  resources:
  - clusterrolebindings
  - clusterroles
  - rolebindings
  - roles
  verbs:
  - '*'
- apiGroups:
  - services.cloud.sap.com
  resources:
  - servicebindings
  - serviceinstances
  verbs:
  - create
  - get
  - list
  - watch
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  labels:
    app.kubernetes.io/component: kube-rbac-proxy
    app.kubernetes.io/created-by: sap-transp-proxy-operator
    app.kubernetes.io/instance: metrics-reader
    app.kubernetes.io/managed-by: kustomize
    app.kubernetes.io/name: clusterrole
    app.kubernetes.io/part-of: sap-transp-proxy-operator
  name: sap-transp-proxy-metrics-reader
rules:
- nonResourceURLs:
  - /metrics
  verbs:
  - get
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  labels:
    app.kubernetes.io/component: kube-rbac-proxy
    app.kubernetes.io/created-by: sap-transp-proxy-operator
    app.kubernetes.io/instance: proxy-role
    app.kubernetes.io/managed-by: kustomize
    app.kubernetes.io/name: clusterrole
    app.kubernetes.io/part-of: sap-transp-proxy-operator
  name: sap-transp-proxy-proxy-role
rules:
- apiGroups:
  - authentication.k8s.io
  resources:
  - tokenreviews
  verbs:
  - create
- apiGroups:
  - authorization.k8s.io
  resources:
  - subjectaccessreviews
  verbs:
  - create
---
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  labels:
    app.kubernetes.io/component: rbac
    app.kubernetes.io/created-by: sap-transp-proxy-operator
    app.kubernetes.io/instance: leader-election-rolebinding
    app.kubernetes.io/managed-by: kustomize
    app.kubernetes.io/name: rolebinding
    app.kubernetes.io/part-of: sap-transp-proxy-operator
  name: sap-transp-proxy-leader-election-rolebinding
  namespace: sap-transp-proxy-system
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: Role
  name: sap-transp-proxy-leader-election-role
subjects:
- kind: ServiceAccount
  name: sap-transp-proxy-operator
  namespace: sap-transp-proxy-system
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  labels:
    app.kubernetes.io/component: rbac
    app.kubernetes.io/created-by: sap-transp-proxy-operator
    app.kubernetes.io/instance: manager-rolebinding
    app.kubernetes.io/managed-by: kustomize
    app.kubernetes.io/name: clusterrolebinding
    app.kubernetes.io/part-of: sap-transp-proxy-operator
  name: sap-transp-proxy-manager-rolebinding
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: sap-transp-proxy-manager-role
subjects:
- kind: ServiceAccount
  name: sap-transp-proxy-operator
  namespace: sap-transp-proxy-system
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  labels:
    app.kubernetes.io/component: kube-rbac-proxy
    app.kubernetes.io/created-by: sap-transp-proxy-operator
    app.kubernetes.io/instance: proxy-rolebinding
    app.kubernetes.io/managed-by: kustomize
    app.kubernetes.io/name: clusterrolebinding
    app.kubernetes.io/part-of: sap-transp-proxy-operator
  name: sap-transp-proxy-proxy-rolebinding
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: sap-transp-proxy-proxy-role
subjects:
- kind: ServiceAccount
  name: sap-transp-proxy-operator
  namespace: sap-transp-proxy-system
---
apiVersion: v1
data:
  change-log-level: |
    #!/bin/sh
 
    accepted_values="trace debug info warn error fatal"
    input=$(echo "$1" | tr '[:upper:]' '[:lower:]')
    if echo "$accepted_values" | grep -wq "$input"; then
      echo "log:" > /etc/logging/logger-config.yaml
      echo "  level: $input" >> /etc/logging/logger-config.yaml
      echo "Successfully changed log levels to $input"
    else
      echo "$1 is not an accepted log level. Accepted log levels are $accepted_values"
    fi
  logger-config.yaml: |
    log:
      level: info
kind: ConfigMap
metadata:
  name: sap-transp-proxy-sap-transp-proxy-operator-logging-config
  namespace: sap-transp-proxy-system
---
apiVersion: v1
kind: Service
metadata:
  labels:
    app.kubernetes.io/component: kube-rbac-proxy
    app.kubernetes.io/created-by: sap-transp-proxy-operator
    app.kubernetes.io/instance: operator-metrics-service
    app.kubernetes.io/managed-by: kustomize
    app.kubernetes.io/name: service
    app.kubernetes.io/part-of: sap-transp-proxy-operator
    control-plane: operator
  name: sap-transp-proxy-operator-metrics-service
  namespace: sap-transp-proxy-system
spec:
  ports:
  - name: https
    port: 8443
    protocol: TCP
    targetPort: https
  selector:
    control-plane: operator
---
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app.kubernetes.io/component: manager
    app.kubernetes.io/created-by: sap-transp-proxy-operator
    app.kubernetes.io/instance: operator
    app.kubernetes.io/managed-by: kustomize
    app.kubernetes.io/name: deployment
    app.kubernetes.io/part-of: sap-transp-proxy-operator
    control-plane: operator
    transparent-proxy.connectivity.api.sap/component: operator
  name: sap-transp-proxy-operator
  namespace: sap-transp-proxy-system
spec:
  replicas: 1
  selector:
    matchLabels:
      control-plane: operator
  template:
    metadata:
      annotations:
        kubectl.kubernetes.io/default-container: manager
      labels:
        control-plane: operator
        transparent-proxy.connectivity.api.sap/component: operator
    spec:
      affinity:
        nodeAffinity:
          requiredDuringSchedulingIgnoredDuringExecution:
            nodeSelectorTerms:
            - matchExpressions:
              - key: kubernetes.io/arch
                operator: In
                values:
                - amd64
                - arm64
                - ppc64le
                - s390x
              - key: kubernetes.io/os
                operator: In
                values:
                - linux
      containers:
      - args:
        - --secure-listen-address=0.0.0.0:8443
        - --upstream=http://127.0.0.1:8080/
        - --logtostderr=true
        - --v=0
        image: gcr.io/kubebuilder/kube-rbac-proxy:v0.13.1
        name: kube-rbac-proxy
        ports:
        - containerPort: 8443
          name: https
          protocol: TCP
        resources:
          limits:
            cpu: 500m
            memory: 128Mi
          requests:
            cpu: 5m
            memory: 64Mi
        securityContext:
          allowPrivilegeEscalation: false
          capabilities:
            drop:
            - ALL
      - args:
        - --health-probe-bind-address=:8081
        - --metrics-bind-address=127.0.0.1:8080
        - --leader-elect
        command:
        - /manager
        image: sapse/sap-transp-proxy-operator:1.6.0
        imagePullPolicy: Always
        livenessProbe:
          httpGet:
            path: /healthz
            port: 8081
          initialDelaySeconds: 15
          periodSeconds: 20
        name: manager
        readinessProbe:
          httpGet:
            path: /readyz
            port: 8081
          initialDelaySeconds: 5
          periodSeconds: 10
        resources:
          limits:
            cpu: 500m
            memory: 512Mi
          requests:
            cpu: 500m
            memory: 512Mi
        securityContext:
          allowPrivilegeEscalation: false
          capabilities:
            drop:
            - ALL
        volumeMounts:
        - mountPath: /etc/logging
          name: sap-transp-proxy-operator-logging-config-volume
          readOnly: false
      initContainers:
      - command:
        - sh
        - -c
        - touch /etc/logging/logger-config.yaml && cat /etc/conf/logger-config.yaml
          > /etc/logging/logger-config.yaml && touch /etc/logging/change-log-level
          && cat /etc/conf/change-log-level > /etc/logging/change-log-level && adduser
          --disabled-password tpproxy && chown tpproxy /etc/logging/logger-config.yaml
          && chown tpproxy /etc/logging/change-log-level && chmod +x /etc/logging/change-log-level
        image: alpine:3.15.4
        imagePullPolicy: IfNotPresent
        name: config-init
        securityContext:
          readOnlyRootFilesystem: false
        volumeMounts:
        - mountPath: /etc/logging
          name: sap-transp-proxy-operator-logging-config-volume
          readOnly: false
        - mountPath: /etc/conf
          name: sap-transp-proxy-operator-logging-config
          readOnly: false
      serviceAccountName: sap-transp-proxy-operator
      terminationGracePeriodSeconds: 10
      volumes:
      - emptyDir: {}
        name: sap-transp-proxy-operator-logging-config-volume
      - configMap:
          name: sap-transp-proxy-sap-transp-proxy-operator-logging-config
        name: sap-transp-proxy-operator-logging-config

```

Put the above content in a YAML file and execute: \(example if file is named operator.yaml\)

> ### Sample Code:  
> ```
> kubectl apply -f operator.yaml
> ```

This will create/update the *sap-transp-proxy-system* namespace along with the necessary deployment and RBAC configuration for the transparent proxy operator.

**Transparent Proxy Custom Resource** 

To install the transparent proxy, you must create a custom resource.

Example transparent proxy custom resource configuration:

> ### Sample Code:  
> ```
> apiVersion: operator.kyma-project.io/v1alpha1
> kind: TransparentProxy
> metadata:
>   name: transparent-proxy
>   namespace: sap-transp-proxy-system
> spec:
>   config:
>     security:
>       communication:
>         internal:
>           encryptionEnabled: true
>     integration:
>       serviceMesh:
>         istio:
>           istio-injection: enabled
> ```

You may update it to suit to your requirements. To do this, either use *kubectl edit* or create a YAML file containing the transparent proxy custom resource and edit the *spec* section with values according to the [Configuration Guide](configuration-guide-2a22cd7.md).

**Applying a Transparent Proxy CR** 

> ### Sample Code:  
> ```
> kubectl apply -f <fileName> -n sap-transp-proxy-system
> ```



<a name="loio8f5dd89fb3d349ab81282d0ee33f4f8e__section_sy1_zpw_hcc"/>

## Uninstall

Make sure you delete all transparent proxy custom resources in advance, otherwise the uninstallation will be stuck until their deletion.

> ### Sample Code:  
> ```
> kubectl delete -f operator.yaml // referring to the same file used for the install
> ```

> ### Caution:  
> All resources created in *sap-transp-proxy-system*, including the namespace, will be deleted. This also includes the default Destination service instance, if created initially.



<a name="loio8f5dd89fb3d349ab81282d0ee33f4f8e__section_jfs_ypw_hcc"/>

## Troubleshooting

In case of issues, refer to [Transparent Proxy Custom Resource Conditions](transparent-proxy-custom-resource-conditions-d75e31e.md).

