Mac M4 docker 运行 Teamgram Server  选择 master 分支

## 安装依赖
```
docker compose -f docker-compose-env.yaml up -d
```
```
[+] up 162/162
 ✔ Image kevinwan/go-stash:1.1.1                Pulled                                                                                                                     16.8s
 ✔ Image grafana/grafana:8.0.6                  Pulled                                                                                                                     86.9s
 ✔ Image prom/node-exporter:v1.7.0              Pulled                                                                                                                     31.6s
 ✔ Image apache/kafka:3.9.0                     Pulled                                                                                                                    118.1s
 ✔ Image elasticsearch:8.12.2                   Pulled                                                                                                                    163.9s
 ✔ Image mysql:8.0                              Pulled                                                                                                                    120.9s
 ✔ Image jaegertracing/all-in-one:1.63.0        Pulled                                                                                                                     64.2s
 ✔ Image quay.io/coreos/etcd:v3.5.11            Pulled                                                                                                                     49.2s
 ✔ Image elastic/filebeat:8.12.2                Pulled                                                                                                                     81.2s
 ✔ Image minio/minio:latest                     Pulled                                                                                                                     84.1s
 ✔ Image redis:7-alpine                         Pulled                                                                                                                     43.5s
 ✔ Image minio/mc:latest                        Pulled                                                                                                                     37.8s
 ✔ Image kibana:8.12.2                          Pulled                                                                                                                    160.0s
 ✔ Image prom/prometheus:v2.28.1                Pulled                                                                                                                     76.0s
 ✔ Network teamgram-server_teamgram_net         Created                                                                                                                     0.0s
 ✔ Volume teamgram-server_kafka_data            Created                                                                                                                     0.0s
 ✔ Volume teamgram-server_elasticsearch_data    Created                                                                                                                     0.0s
 ✔ Volume teamgram-server_elasticsearch_plugins Created                                                                                                                     0.0s
 ✔ Container elasticsearch                      Started                                                                                                                     3.4s
 ✔ Container grafana                            Started                                                                                                                     3.4s
 ✔ Container mysql                              Started                                                                                                                     3.3s
 ✔ Container redis                              Started                                                                                                                     3.4s
 ✔ Container etcd                               Started                                                                                                                     3.4s
 ✔ Container node-exporter                      Started                                                                                                                     3.3s
 ✔ Container prometheus                         Started                                                                                                                     3.3s
 ✔ Container kafka                              Started                                                                                                                     3.3s
 ✔ Container minio                              Started                                                                                                                     3.3s
 ✔ Container jaeger                             Started                                                                                                                     3.4s
 ✔ Container kibana                             Started                                                                                                                     3.2s
 ✔ Container filebeat                           Started                                                                                                                     3.1s
 ✔ Container go-stash                           Started                                                                                                                     3.4s
 ✔ Container minio-mc                           Started                                                                                                                     3.0s
```
## 运行程序

```
docker compose up -d
```

```
[+] Building 206.2s (17/17) FINISHED                                                                                                                                            
 => [internal] load local bake definitions                                                                                                                                 0.0s
 => => reading from stdin 568B                                                                                                                                             0.0s
 => [internal] load build definition from Dockerfile                                                                                                                       0.0s
 => => transferring dockerfile: 324B                                                                                                                                       0.0s
 => [internal] load metadata for docker.io/library/golang:1.23.0                                                                                                           2.7s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                                                           2.7s
 => [internal] load .dockerignore                                                                                                                                          0.0s
 => => transferring context: 2B                                                                                                                                            0.0s
 => [builder 1/4] FROM docker.io/library/golang:1.23.0@sha256:acfb46be39840f8c2a6b9efdd673c6627011200c73bab4e6d18b8b9ab4641c46                                            33.7s
 => => resolve docker.io/library/golang:1.23.0@sha256:acfb46be39840f8c2a6b9efdd673c6627011200c73bab4e6d18b8b9ab4641c46                                                     0.0s
 => => sha256:753b8657f07ae087e9b23b29b60ea9dc8fa3be812e08d477ea6eda5a1f7d2039 126B / 126B                                                                                 0.4s
 => => sha256:73f9ed64c24993ada6c5d1b00ea7fbf5720c6cc30c9ae14d18134989fa7a08a7 70.61MB / 70.61MB                                                                          29.9s
 => => sha256:ecb27c98d5b9e78892d876693427ae0a01e3113b36989718360a5aa9e319fd80 86.29MB / 86.29MB                                                                          31.7s
 => => sha256:843b1d8321825bc8302752ae003026f13bd15c6eef2efe032f3ca1520c5bbc07 64.00MB / 64.00MB                                                                          13.6s
 => => sha256:364d19f59f69474a80c53fc78da91f85553e16e8ba6a28063cbebf259821119e 23.59MB / 23.59MB                                                                           5.4s
 => => sha256:56c9b9253ff98351db158cb6789848656b8d54f411c0037347bf2358efb18f39 49.59MB / 49.59MB                                                                          15.6s
 => => extracting sha256:56c9b9253ff98351db158cb6789848656b8d54f411c0037347bf2358efb18f39                                                                                  0.5s
 => => extracting sha256:364d19f59f69474a80c53fc78da91f85553e16e8ba6a28063cbebf259821119e                                                                                  0.2s
 => => extracting sha256:843b1d8321825bc8302752ae003026f13bd15c6eef2efe032f3ca1520c5bbc07                                                                                  0.7s
 => => extracting sha256:ecb27c98d5b9e78892d876693427ae0a01e3113b36989718360a5aa9e319fd80                                                                                  0.7s
 => => extracting sha256:73f9ed64c24993ada6c5d1b00ea7fbf5720c6cc30c9ae14d18134989fa7a08a7                                                                                  0.9s
 => => extracting sha256:753b8657f07ae087e9b23b29b60ea9dc8fa3be812e08d477ea6eda5a1f7d2039                                                                                  0.0s
 => => extracting sha256:4f4fb700ef54461cfa02571ae0db9a0dc1e0cdb5577484a6d75e68dc38e8acc1                                                                                  0.0s
 => [internal] load build context                                                                                                                                          2.9s
 => => transferring context: 477.06MB                                                                                                                                      2.9s
 => [stage-1 1/5] FROM docker.io/library/ubuntu:latest@sha256:b7f48194d4d8b763a478a621cdc81c27be222ba2206ca3ca6bc42b49685f3d9e                                            14.1s
 => => resolve docker.io/library/ubuntu:latest@sha256:b7f48194d4d8b763a478a621cdc81c27be222ba2206ca3ca6bc42b49685f3d9e                                                     0.0s
 => => sha256:ade0b5cbf7f1ac2f5ced1ed952e889f07199006cfbb44f6e2c7b85df005259ca 392B / 392B                                                                                 0.3s
 => => sha256:b2b4144bf8691339f4f1011754b5ed314a4cb9c03e57af4c022301022f36b79a 40.71MB / 40.71MB                                                                          13.5s
 => => extracting sha256:b2b4144bf8691339f4f1011754b5ed314a4cb9c03e57af4c022301022f36b79a                                                                                  0.5s
 => => extracting sha256:ade0b5cbf7f1ac2f5ced1ed952e889f07199006cfbb44f6e2c7b85df005259ca                                                                                  0.0s
 => [stage-1 2/5] RUN apt update -y && apt install -y ffmpeg psmisc && apt-get clean                                                                                     162.1s
 => [builder 2/4] WORKDIR /app                                                                                                                                             0.2s
 => [builder 3/4] COPY . .                                                                                                                                                 0.4s
 => [builder 4/4] RUN ./build.sh                                                                                                                                         120.4s
 => [stage-1 3/5] WORKDIR /app                                                                                                                                             0.1s 
 => [stage-1 4/5] COPY --from=builder /app/teamgramd/ /app/                                                                                                                1.3s 
 => [stage-1 5/5] RUN chmod +x /app/docker/entrypoint.sh                                                                                                                   0.2s 
 => exporting to image                                                                                                                                                    25.4s 
 => => exporting layers                                                                                                                                                   20.0s 
 => => exporting manifest sha256:ce82fa11177d9a0f2e9978a089d199a02c206b993907688de30e10516d9e15e2                                                                          0.0s 
 => => exporting config sha256:76d70d7e4ed9e59d91d36a7692fbfa1edd381c8bf8b8e4be01f8479f292f92c7                                                                            0.0s 
 => => exporting attestation manifest sha256:0c3a9513a9e30983c8ac1ae8368556234f341da306fd5f264a47a4a6a023beb8                                                              0.0s 
 => => exporting manifest list sha256:5c1e32a5fc82973e08522073bd70907be917aed219bdf0832f8ca2dc7de559e6                                                                     0.0s 
 => => naming to docker.io/library/teamgram-server-teamgram:latest                                                                                                         0.0s 
 => => unpacking to docker.io/library/teamgram-server-teamgram:latest                                                                                                      5.4s 
 => resolving provenance for metadata file                                                                                                                                 0.0s 
WARN[0206] Found orphan containers (minio-mc, kibana, jaeger, go-stash, filebeat, mysql, prometheus, etcd, grafana, redis, minio, node-exporter, elasticsearch, kafka) for this project. If you removed or renamed this service in your compose file, you can run this command with the --remove-orphans flag to clean it up. 
[+] up 2/2
 ✔ Image teamgram-server-teamgram       Built                                                                                                                             206.3s
 ✔ Container teamgram-server-teamgram-1 Started                           

```

## 查看运行结果

```

```
