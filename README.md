# Open-Falcon HAProxy 采集器

## Usage

### 直接使用

`go build main.go`

### 作为包使用

```
import stats "github.com/cloverstd/open_falcon_haproxy_stats"

func main() {
    stats.Stats()
}
```

## 变量
|环境变量|默认值|说明|
|-------|---|----|
|HAPROXY_STATS_PORT|9000|HAProxy 配置文件中设置的 stats 端口|
|HAPROXY_STATS_HOST|127.0.0.1|HAProxy 配置文件中设置的 stats 地址|
|HAPROXY_STATS_USERNAME||如果没有认证则留空|
|HAPROXY_STATS_PASSWORD||如果没有认证则留空|
|FALCON_AGENT_PORT|1988|Open Falcon Agent 端口|
|FALCON_AGENT_HOST|127.0.0.1|Open Falcon Agent 地址|
|HAPROXY_HOST|127.0.0.1|HAProxy 地址，会作为 Open Falcon 的 endpoint|
|HAPROXY_PORT|20010|HAProxy 端口，会作为 Open Falcon 的 endpoint|
|METRIC|hrsp_1xx,hrsp_2xx,hrsp_3xx,hrsp_4xx,hrsp_5xx,bin,bout|采集的指标|


## Open Falcon

* `endpoint` 为 `haproxy-${HAPROXY_HOST}-${HAPROXY_PORT}`，例如 `haproxy-172.24.4.4-20010`
* `counter` 为 `{metric}/pxname={pxname},svname={svname}`，例如 `hrsp_2xx/pxname=test-cluster,svname=test-172.24.6.6-80`

## HAProxy metric

http://cbonte.github.io/haproxy-dconv/1.6/management.html#9.1
