# Rate Limiting

API 서비스에 종류에 따라서 특정기간의 호출 가능 건수를 제한 합니다. 

**HTTP 결과값의  header에서 확인 할 수 있습니다.**

```text
HTTP/1.1 200 OK
... other headers here ...
x-rate-period: day
x-rate-limit: 50000
x-rate-value: 3
```

| **`항목`** | **`설명`** |
| :--- | :--- |
| x-rate-period | API 서버스의 호출 건수 제한 기간 \(`day`, month\) |
| x-rate-limit | 최대 호출 가능 건수 |
| x-rate-value | 최종 호출 건수 |

**제한된 기간에 호출건수가 초과되면 API서비스를 제한 합니다.**

```text
HTTP/1.1 429 Too Many Requests
... other headers here ...
x-rate-period: day
x-rate-limit: 50000
x-rate-value: 50001
```

호출건수를 상향 하려면 오픈플랫폼 담당자에게 문의 하세요.



