## 如何获取实例负载

SGLang提供了/v1/loads接口，可以方便、快速查询实例的负载情况，返回包含正在running的请求数，waiting的请求数，KV Cache预算（总量及剩余量）等等。
调用示例如下所示（暂不考虑某个dp rank的负载情况）：
```bash
curl -sS -H "Authorization: Bearer xxx" "http://127.0.0.1:9001/v1/loads"
```
返回结果示例（无dp group）：
```json
{
    "timestamp": "2026-05-10T05:46:18.697201+00:00",
    "version": "0.5.10rc0",
    "dp_rank_count": 1,
    "loads": [
        {
            "num_running_reqs": 4,
            "num_waiting_reqs": 0,
            "num_used_tokens": 178496,
            "max_total_num_tokens": 545344,
            "token_usage": 0.3273,
            "gen_throughput": 171.81,
            "cache_hit_rate": 0,
            "utilization": 0,
            "max_running_requests": 64,
            "memory": {
                "weight_gb": 89.244,
                "kv_cache_gb": 31.221,
                "graph_gb": 1.32,
                "token_capacity": 545344
            },
            "disaggregation": {
                "mode": "null",
                "prefill_prealloc_queue_reqs": 0,
                "prefill_inflight_queue_reqs": 0,
                "decode_prealloc_queue_reqs": 0,
                "decode_transfer_queue_reqs": 0,
                "decode_retracted_queue_reqs": 0,
                "kv_transfer_speed_gb_s": 0,
                "kv_transfer_latency_ms": 0
            },
            "queues": {
                "waiting": 0,
                "grammar": 0,
                "paused": 0,
                "retracted": 0
            },
            "num_total_reqs": 4
        }
    ],
    "aggregate": {
        "total_running_reqs": 4,
        "total_waiting_reqs": 0,
        "total_reqs": 4,
        "avg_token_usage": 0.3273,
        "avg_throughput": 171.81,
        "avg_utilization": 0
    }
}
```
返回结果示例（dp group & PD disagg）：
```json
{
    "timestamp": "2026-05-10T05:54:55.227211+00:00",
    "version": "0.5.9",
    "dp_rank_count": 8,
    "loads": [
        {
            "dp_rank": 0,
            "num_running_reqs": 0,
            "num_waiting_reqs": 0,
            "num_used_tokens": 0,
            "max_total_num_tokens": 107328,
            "token_usage": 0,
            "gen_throughput": 0,
            "cache_hit_rate": 0,
            "utilization": 0,
            "max_running_requests": 128,
            "memory": {
                "weight_gb": 106.498,
                "kv_cache_gb": 6.147,
                "graph_gb": 0,
                "token_capacity": 107328
            },
            "disaggregation": {
                "mode": "prefill",
                "prefill_prealloc_queue_reqs": 0,
                "prefill_inflight_queue_reqs": 0,
                "decode_prealloc_queue_reqs": 0,
                "decode_transfer_queue_reqs": 0,
                "decode_retracted_queue_reqs": 0,
                "kv_transfer_speed_gb_s": 0,
                "kv_transfer_latency_ms": 0
            },
            "queues": {
                "waiting": 0,
                "grammar": 0,
                "paused": 0,
                "retracted": 0
            },
            "num_total_reqs": 0
        },
        {
            "dp_rank": 3,
            "num_running_reqs": 0,
            "num_waiting_reqs": 0,
            "num_used_tokens": 0,
            "max_total_num_tokens": 107328,
            "token_usage": 0,
            "gen_throughput": 0,
            "cache_hit_rate": 0,
            "utilization": 0,
            "max_running_requests": 128,
            "memory": {
                "weight_gb": 106.498,
                "kv_cache_gb": 6.147,
                "graph_gb": 0,
                "token_capacity": 107328
            },
            "disaggregation": {
                "mode": "prefill",
                "prefill_prealloc_queue_reqs": 0,
                "prefill_inflight_queue_reqs": 0,
                "decode_prealloc_queue_reqs": 0,
                "decode_transfer_queue_reqs": 0,
                "decode_retracted_queue_reqs": 0,
                "kv_transfer_speed_gb_s": 0,
                "kv_transfer_latency_ms": 0
            },
            "queues": {
                "waiting": 0,
                "grammar": 0,
                "paused": 0,
                "retracted": 0
            },
            "num_total_reqs": 0
        },
        {
            "dp_rank": 1,
            "num_running_reqs": 0,
            "num_waiting_reqs": 0,
            "num_used_tokens": 0,
            "max_total_num_tokens": 107328,
            "token_usage": 0,
            "gen_throughput": 0,
            "cache_hit_rate": 0,
            "utilization": 0,
            "max_running_requests": 128,
            "memory": {
                "weight_gb": 106.498,
                "kv_cache_gb": 6.147,
                "graph_gb": 0,
                "token_capacity": 107328
            },
            "disaggregation": {
                "mode": "prefill",
                "prefill_prealloc_queue_reqs": 0,
                "prefill_inflight_queue_reqs": 0,
                "decode_prealloc_queue_reqs": 0,
                "decode_transfer_queue_reqs": 0,
                "decode_retracted_queue_reqs": 0,
                "kv_transfer_speed_gb_s": 0,
                "kv_transfer_latency_ms": 0
            },
            "queues": {
                "waiting": 0,
                "grammar": 0,
                "paused": 0,
                "retracted": 0
            },
            "num_total_reqs": 0
        },
        {
            "dp_rank": 4,
            "num_running_reqs": 0,
            "num_waiting_reqs": 0,
            "num_used_tokens": 0,
            "max_total_num_tokens": 107328,
            "token_usage": 0,
            "gen_throughput": 0,
            "cache_hit_rate": 0,
            "utilization": 0,
            "max_running_requests": 128,
            "memory": {
                "weight_gb": 106.498,
                "kv_cache_gb": 6.147,
                "graph_gb": 0,
                "token_capacity": 107328
            },
            "disaggregation": {
                "mode": "prefill",
                "prefill_prealloc_queue_reqs": 0,
                "prefill_inflight_queue_reqs": 0,
                "decode_prealloc_queue_reqs": 0,
                "decode_transfer_queue_reqs": 0,
                "decode_retracted_queue_reqs": 0,
                "kv_transfer_speed_gb_s": 0,
                "kv_transfer_latency_ms": 0
            },
            "queues": {
                "waiting": 0,
                "grammar": 0,
                "paused": 0,
                "retracted": 0
            },
            "num_total_reqs": 0
        },
        {
            "dp_rank": 5,
            "num_running_reqs": 0,
            "num_waiting_reqs": 0,
            "num_used_tokens": 0,
            "max_total_num_tokens": 107328,
            "token_usage": 0,
            "gen_throughput": 0,
            "cache_hit_rate": 0,
            "utilization": 0,
            "max_running_requests": 128,
            "memory": {
                "weight_gb": 106.498,
                "kv_cache_gb": 6.147,
                "graph_gb": 0,
                "token_capacity": 107328
            },
            "disaggregation": {
                "mode": "prefill",
                "prefill_prealloc_queue_reqs": 0,
                "prefill_inflight_queue_reqs": 0,
                "decode_prealloc_queue_reqs": 0,
                "decode_transfer_queue_reqs": 0,
                "decode_retracted_queue_reqs": 0,
                "kv_transfer_speed_gb_s": 0,
                "kv_transfer_latency_ms": 0
            },
            "queues": {
                "waiting": 0,
                "grammar": 0,
                "paused": 0,
                "retracted": 0
            },
            "num_total_reqs": 0
        },
        {
            "dp_rank": 2,
            "num_running_reqs": 0,
            "num_waiting_reqs": 0,
            "num_used_tokens": 0,
            "max_total_num_tokens": 107328,
            "token_usage": 0,
            "gen_throughput": 0,
            "cache_hit_rate": 0,
            "utilization": 0,
            "max_running_requests": 128,
            "memory": {
                "weight_gb": 106.498,
                "kv_cache_gb": 6.147,
                "graph_gb": 0,
                "token_capacity": 107328
            },
            "disaggregation": {
                "mode": "prefill",
                "prefill_prealloc_queue_reqs": 0,
                "prefill_inflight_queue_reqs": 0,
                "decode_prealloc_queue_reqs": 0,
                "decode_transfer_queue_reqs": 0,
                "decode_retracted_queue_reqs": 0,
                "kv_transfer_speed_gb_s": 0,
                "kv_transfer_latency_ms": 0
            },
            "queues": {
                "waiting": 0,
                "grammar": 0,
                "paused": 0,
                "retracted": 0
            },
            "num_total_reqs": 0
        },
        {
            "dp_rank": 6,
            "num_running_reqs": 0,
            "num_waiting_reqs": 0,
            "num_used_tokens": 0,
            "max_total_num_tokens": 107328,
            "token_usage": 0,
            "gen_throughput": 0,
            "cache_hit_rate": 0,
            "utilization": 0,
            "max_running_requests": 128,
            "memory": {
                "weight_gb": 106.498,
                "kv_cache_gb": 6.147,
                "graph_gb": 0,
                "token_capacity": 107328
            },
            "disaggregation": {
                "mode": "prefill",
                "prefill_prealloc_queue_reqs": 0,
                "prefill_inflight_queue_reqs": 0,
                "decode_prealloc_queue_reqs": 0,
                "decode_transfer_queue_reqs": 0,
                "decode_retracted_queue_reqs": 0,
                "kv_transfer_speed_gb_s": 0,
                "kv_transfer_latency_ms": 0
            },
            "queues": {
                "waiting": 0,
                "grammar": 0,
                "paused": 0,
                "retracted": 0
            },
            "num_total_reqs": 0
        },
        {
            "dp_rank": 7,
            "num_running_reqs": 0,
            "num_waiting_reqs": 0,
            "num_used_tokens": 0,
            "max_total_num_tokens": 107328,
            "token_usage": 0,
            "gen_throughput": 0,
            "cache_hit_rate": 0,
            "utilization": 0,
            "max_running_requests": 128,
            "memory": {
                "weight_gb": 106.498,
                "kv_cache_gb": 6.147,
                "graph_gb": 0,
                "token_capacity": 107328
            },
            "disaggregation": {
                "mode": "prefill",
                "prefill_prealloc_queue_reqs": 0,
                "prefill_inflight_queue_reqs": 0,
                "decode_prealloc_queue_reqs": 0,
                "decode_transfer_queue_reqs": 0,
                "decode_retracted_queue_reqs": 0,
                "kv_transfer_speed_gb_s": 0,
                "kv_transfer_latency_ms": 0
            },
            "queues": {
                "waiting": 0,
                "grammar": 0,
                "paused": 0,
                "retracted": 0
            },
            "num_total_reqs": 0
        }
    ],
    "aggregate": {
        "total_running_reqs": 0,
        "total_waiting_reqs": 0,
        "total_reqs": 0,
        "avg_token_usage": 0,
        "avg_throughput": 0,
        "avg_utilization": 0
    }
}
```
由于PD disagg实现差异，不能直接通过`num_running_reqs`和`num_waiting_reqs`获取Prefill侧正在running和waiting的请求数。然而，`prefill_prealloc_queue_reqs`往往反映的是Decode侧的压力情况，它指的是Prefill侧`Bootstrap`队列里的请求数，当Decode的KV Slot可以成功对其预分配时才会认为`Bootstrap`成功。如果该队列排队请求数较多，说明Decode侧负载较大。而`prefill_inflight_queue_reqs`表示Prefill侧在途即正在向Decode节点做KV Transfer的队列请求数，但在`0.5.9`版本中可能由于实现问题该值一直为0。在Decode节点可以通过`decode_transfer_queue_reqs`获取到正确的数值。