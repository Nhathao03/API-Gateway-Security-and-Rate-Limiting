---
title : "Kiểm tra các function"
weight : 3
chapter : false
pre : " <b> 2.3. </b> "
---

## Giới thiệu đề tài

Trong bối cảnh các hệ thống hiện đại ngày càng phụ thuộc vào API để giao tiếp giữa các dịch vụ, việc đảm bảo an toàn cho các API trở thành một nhiệm vụ thiết yếu. Một API không được bảo vệ đúng cách có thể trở thành điểm yếu khiến cả hệ thống bị tấn công, gây mất dữ liệu, gián đoạn dịch vụ hoặc vi phạm tuân thủ bảo mật.

**Đề tài “API Security Gateway với Advanced Protection”** hướng đến việc triển khai một kiến trúc API Gateway bảo mật cao cấp trên nền tảng **AWS**, tích hợp đầy đủ các lớp bảo vệ hiện đại và quy chuẩn an ninh, bao gồm:

- **Threat Protection**: Bảo vệ chống lại các cuộc tấn công như DDoS, SQL injection, XSS...
- **Rate Limiting**: Giới hạn tốc độ truy cập API theo IP hoặc theo người dùng.
- **Authentication**: Cơ chế xác thực mạnh mẽ, hỗ trợ OAuth2, JWT, SSO...
- **Authorization**: Phân quyền chi tiết theo vai trò, nhóm người dùng.
- **Monitoring & Logging**: Giám sát thời gian thực, alert, truy vết sự cố.
- **Operational Readiness**: Triển khai, bảo trì và quản lý vận hành thuận tiện.
- **Developer Integration**: Hỗ trợ tốt cho việc tích hợp frontend/backend và CI/CD.

---

## Mục tiêu triển khai

Hướng dẫn sẽ tập trung vào việc cấu hình và triển khai các dịch vụ **native của AWS** để đạt được các yêu cầu sau:

| Yêu cầu kỹ thuật                      | Dịch vụ sử dụng trên AWS                       |
|--------------------------------------|------------------------------------------------|
| Threat Protection                    | AWS Shield, AWS WAF                           |
| DNS Protection + Entry Point         | Amazon Route 53                               |
| API Gateway Management               | Amazon API Gateway                            |
| Authentication / Authorization       | Amazon Cognito, JWT, IAM                      |
| Rate Limiting                        | AWS WAF Rate-based rules, API Gateway quotas |
| Business Logic                       | AWS Lambda                                    |
| Data Storage                         | Amazon S3, DynamoDB, Aurora Serverless        |
| Monitoring / Alerting                | Amazon CloudWatch, X-Ray                      |

---

## Kiến trúc hệ thống
Hệ thống được thiết kế theo hướng **zero-trust**, với các lớp bảo vệ theo chiều sâu từ lớp biên (network) đến ứng dụng và dữ liệu.

---

## Nội dung blog gồm 3 phần chính

1. **Giới thiệu đề tài** (bạn đang xem)
2. **Hướng dẫn triển khai chi tiết trên AWS Console**:
    - Cấu hình từng thành phần như Shield, WAF, Cognito, API Gateway, v.v.
    - Kết nối và tích hợp giữa các dịch vụ.
3. **Dọn dẹp tài nguyên sau triển khai**:
    - Hướng dẫn xóa các dịch vụ đã sử dụng để tránh phát sinh chi phí.

---

## Yêu cầu trước khi bắt đầu

- Một tài khoản AWS với quyền quản trị hoặc IAM đủ quyền thao tác.
- Kiến thức cơ bản về REST API, bảo mật web (JWT, OAuth2, IAM).
- Một tên miền nếu bạn muốn cấu hình với Route 53 và CloudFront.
- Cài đặt sẵn `AWS CLI` nếu muốn thao tác kết hợp terminal.

---

## Kết luận

Hướng dẫn này phù hợp cho cả:
- Nhà phát triển đang xây dựng hệ thống API trên AWS
- DevOps hoặc Security Engineer triển khai mô hình bảo mật phân lớp
- Học viên hoặc kỹ sư muốn tìm hiểu kiến trúc bảo mật API hiện đại
