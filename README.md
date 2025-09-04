# config-center

English | [中文](README_zh.md)

## Design

### Deployment

Configure 2 pods with `maxSkew` to ensure deployment on different nodes, preventing a single point of failure while enabling horizontal scaling. Since the request volume is predictable, there is no need for autoscaling; operators can manually scale horizontally as needed.