# S3 - Simple Storage Service Performance Optimization #

S3 can handle very high request rates by default. If >100 PUT/LIST/DELETE requests per second or >300 GET requests per second, S3 can be optimized further.

- GET-Intensive Workloads
    - Use Cloudfront

- Mixed Request Type
    - Key names impact performance
    - Key names determine physical partition
    - Sequential key names could cause I/O slowdown, contention
    - Use random prefix for key name to minimize collisions

```
mybucket/2018-03-04/image1.png
mybucket/2018-03-04/image2.png
mybucket/2018-03-04/image3.png
```

 The above is ***not optimal*** because of the repeated prefix `2018-03-04`. This will cause objects to be stored on the same partition, causing I/O issues at high loads.

```
mybucket/7eh4-2018-03-04/image1.png
mybucket/h35d-2018-03-04/image2.png
mybucket/o3n6-2018-03-04/image3.png
```

This example uses randomly generated hashes ( **7eh4** instead of 2018-03-04 ) to prevent prefix collisions and improve performance. Any random sequence could be used.
