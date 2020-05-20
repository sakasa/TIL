## WebサイトのHTTPS対応パターン
https://recipe.kc-cloud.jp/archives/11067
1. ELB(+証明書)→EC2
2. EC2(+外部SSL証明書)
3. ELB(+証明書)→EC2(+外部SSL証明書)
4. NLB→EC2(+外部SSL証明書)
5. CloudFront(+証明書)→S3
6. CloudFront(+証明書)→ELB→EC2
7. CloudFront(+証明書)→EC2
8. Lightsail(+証明書)
9. S3のみ
