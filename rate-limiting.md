# Rate Limiting

API 서비스에 종류에 따라서 특정기간의 호출 가능 건수를 제한 합니다.&#x20;

**HTTP 결과값의  header에서 확인 할 수 있습니다.**

```yaml
HTTP/1.1 200 OK
... other headers here ...
X-RateLimit-Remaining-Day : 49973
X-RateLimit-Limit-Day : 50000
```

| **`항목`**                  | **`설명`**                        |
| ------------------------- | ------------------------------- |
| X-RateLimit-Remaining-Day | 하루 동안 남은 호출 가능한 건수 (GMT+00시 기준) |
| X-RateLimit-Limit-Day     | 하루 rate limit 건수 (GMT+00시 기준)   |

**제한된 기간에 호출건수가 초과되면 API서비스를 제한 합니다.**

```yaml
HTTP/1.1 429 Too Many Requests
{
    "message": "API rate limit exceeded"
}
```

부득이하게 호출건수 상향이 필요한 경우 [오픈API플랫폼 담당자](https://koscom.gitbook.io/open-api/onlineqna)에게 문의 하세요.

