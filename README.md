# Repositório central de Helm Charts - Ruan

```cmd
helm create chart-<seu nome>
``` 

```cmd
helm lint <chart>
```

#### Add icon no Chart.yaml

icon: https://seeklogo.com/images/N/nginx-logo-FF65602A76-seeklogo.com.png # http or file

####
- Parametrização da porta do container

```{{ .Values.service.targetPort }}````

```yaml
service:
  type: ClusterIP
  port: 80
  targetPort: 80
````

- Parametrização do liveness e readiness probes

```yaml
          {{- with .Values.livenessProbe }}
          livenessProbe:
            {{- toYaml . | nindent 12 }}
          {{- end }}
          {{- with .Values.readinessProbe }}
          readinessProbe:
            {{- toYaml . | nindent 12 }}
          {{- end }}
```