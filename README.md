```javascript
function dailyLog202() {
  const requests = [
    { endpoint: "/api/users", responseTime: 120 },
    { endpoint: "/api/products", responseTime: 450 },
    { endpoint: "/api/orders", responseTime: 820 },
    { endpoint: "/api/login", responseTime: 95 },
    { endpoint: "/api/reports", responseTime: 1200 },
  ];

  const slowRequests = requests.filter(
    request => request.responseTime > 500
  );

  const averageTime =
    requests.reduce(
      (total, request) => total + request.responseTime,
      0
    ) / requests.length;

  console.log("=== API Performance Report ===");
  console.log(`Total Requests: ${requests.length}`);
  console.log(`Average Response Time: ${averageTime.toFixed(2)} ms`);
  console.log(`Slow Requests: ${slowRequests.length}`);

  slowRequests.forEach(request => {
    console.log(
      `⚠️ ${request.endpoint}: ${request.responseTime} ms`
    );
  });

  console.log(
    slowRequests.length === 0
      ? "✅ All requests are performing well!"
      : "🔧 Consider optimizing slow endpoints."
  );
}

dailyLog202();
```
