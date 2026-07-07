---
title: "Event 2"
date: 2026-06-06
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---


# Bài thu hoạch: "Meetup Event"

## Mục Đích Của Sự Kiện

Sự kiện Meetup vào ngày 6 tháng 6 năm 2026 được tổ chức như một phiên chia sẻ kiến thức cho cộng đồng công nghệ. Sự kiện cung cấp cho người tham dự những hiểu biết thực tế về phát triển phần mềm, điện toán đám mây, an ninh mạng, trí tuệ nhân tạo, hệ thống kiến thức dựa trên đồ thị và phát triển nghề nghiệp trong lĩnh vực Cloud và DevOps.

Sự kiện nhằm mục đích giúp người tham dự hiểu cách các công nghệ hiện đại được ứng dụng trong các hệ thống thực tế. Các chủ đề được đề cập bao gồm Docker cho việc triển khai ứng dụng, AWS WebSocket cho giao tiếp nhiều người chơi, AWS WAF kết hợp Machine Learning để phát hiện cuộc tấn công mạng, AWS Neptune cho GraphRAG và lộ trình nghề nghiệp từ IT Helpdesk đến Cloud/DevOps.

Thông qua các phiên khác nhau, người tham dự có cơ hội học hỏi từ các minh họa thực tế, giải thích kỹ thuật và kinh nghiệm nghề nghiệp thực tế. Sự kiện có giá trị không chỉ về kiến thức kỹ thuật mà còn giúp người tham dự định hình hướng học tập và mục tiêu nghề nghiệp tương lai.

## Thông Tin Chung

* **Tên sự kiện:** Meetup Event
* **Thời gian:** Ngày 6 tháng 6 năm 2026
* **Địa điểm:** Tầng 26, Tòa nhà Bitexco, 02 Đường Hai Triều, Phường Sài Gòn, Thành phố Hồ Chí Minh
* **Vai trò:** Người tham dự

## Diễn Giả / Người Trình Bày Chính

* **Nguyễn Quốc Bảo** – Multiplayer in the Cloud: Connecting Godot Clients with AWS WebSockets
* **Bảo Huỳnh** – Docker: A Containerization Technology
* **Việt Phát** – AWS Neptune for Building a Graph Knowledge Base for GraphRAG
* **Lê Hoàng Gia Đại** – Combining AWS WAF with Machine Learning for Cyber Attack Detection on AWS
* **Trần Trung Vinh** – From IT Helpdesk to Senior Sysadmin: First Steps Toward Cloud and DevOps

## Chủ Đề Chính & Nội Dung Học Được

### Docker và Container hóa

Phiên Docker đã giới thiệu container hóa và giải thích lý do Docker được sử dụng rộng rãi trong phát triển phần mềm hiện đại. Diễn giả đã so sánh máy ảo truyền thống với container, cho thấy container nhẹ hơn, khởi động nhanh hơn và dễ dàng di chuyển giữa các môi trường khác nhau.

Docker giúp đóng gói một ứng dụng cùng với các phụ thuộc, môi trường chạy và cấu hình của nó. Điều này cho phép ứng dụng chạy nhất quán trên máy của nhà phát triển, môi trường kiểm tra hoặc máy chủ sản xuất.

Các khái niệm quan trọng như Docker Image, Docker Container, Dockerfile, các lớp image, build cache và các lệnh Docker cơ bản cũng đã được giới thiệu. Thông qua phiên này, người tham dự hiểu cách Docker hỗ trợ các pipeline CI/CD, microservices, các ứng dụng cloud-native, môi trường kiểm tra và hiện đại hóa các hệ thống cũ.

### Multiplayer trên Cloud với AWS WebSockets

Phiên này tập trung vào việc xây dựng hệ thống nhiều người chơi dựa trên cloud bằng cách sử dụng client Godot và AWS WebSocket. Diễn giả đã giới thiệu các phương pháp giao tiếp khác nhau như UDP/ENet, WebSocket và HTTP Polling.

WebSocket được trình bày như một lựa chọn phù hợp cho các trò chơi theo lượt, hệ thống phòng chơi, tính năng chat và các trò chơi thời gian thực nhẹ. Kiến trúc đề xuất bao gồm Godot Client, API Gateway WebSocket, AWS Lambda, DynamoDB và CloudWatch.

DynamoDB được sử dụng để lưu trữ thông tin kết nối và trạng thái người chơi, trong khi Lambda xử lý các sự kiện kết nối, sự kiện ngắt kết nối, ghép cặp người chơi, lựa chọn của người chơi và kết quả trò chơi. Demo cho thấy hai client kết nối đến hệ thống, được ghép cặp với nhau, gửi lựa chọn Kéo-Búa-Bao và nhận kết quả trong thời gian thực.

Phiên này giúp người tham dự hiểu cách các dịch vụ AWS serverless có thể hỗ trợ các ứng dụng thời gian thực đơn giản mà không cần quản lý máy chủ backend truyền thống.

### AWS WAF và Machine Learning cho Phát Hiện Tấn Công Mạng

Phiên an ninh mạng đã giải thích cách AWS WAF có thể được kết hợp với Machine Learning để cải thiện phát hiện cuộc tấn công mạng. AWS WAF thường được sử dụng để bảo vệ các ứng dụng web khỏi các cuộc tấn công phổ biến bằng cách sử dụng bảo vệ dựa trên quy tắc và chữ ký.

Tuy nhiên, các quy tắc cố định có thể không phải lúc nào cũng phát hiện được các mẫu tấn công mới, phức tạp hoặc bất thường. Vì vậy, Machine Learning có thể được sử dụng để hỗ trợ phát hiện bất thường và cải thiện khả năng xác định hành vi đáng ngờ.

Diễn giả đã giới thiệu một mô hình Hệ thống Phát Hiện Xâm Nhập Mạng sử dụng bộ dữ liệu CSE-CIC-IDS2018. Phiên này cũng đề cập đến các công cụ và dịch vụ như Python, scikit-learn, pandas, AWS WAF, Amazon S3, AWS Lambda, Kinesis Data Firehose, GuardDuty, Security Hub và CloudWatch.

Các vấn đề quan trọng như bảng điều khiển thời gian thực, trực quan hóa cảnh báo, mất cân bằng lớp, false positives và tối ưu hóa mô hình cũng đã được thảo luận. Từ phiên này, người tham dự học được rằng an ninh mạng nên được thiết kế theo nhiều lớp, kết hợp bảo vệ dựa trên quy tắc, giám sát, ghi nhật ký và phát hiện thông minh.

### AWS Neptune và GraphRAG

Phiên AWS Neptune đã giới thiệu GraphRAG và giải thích cách cơ sở dữ liệu đồ thị có thể cải thiện các hệ thống AI dựa trên kiến thức. Diễn giả trước tiên giải thích Retrieval-Augmented Generation, cho phép các mô hình ngôn ngữ lớn truy xuất kiến thức bên ngoài trước khi tạo phản hồi.

RAG truyền thống hữu ích cho việc truy xuất văn bản liên quan, nhưng có thể có hạn chế khi các câu hỏi yêu cầu hiểu các mối quan hệ giữa nhiều thực thể. GraphRAG cải thiện điều này bằng cách lưu trữ các thực thể và mối quan hệ trong một cấu trúc đồ thị, cho phép suy luận nhiều bước tốt hơn.

AWS Neptune được trình bày như một dịch vụ cơ sở dữ liệu đồ thị có thể được sử dụng để xây dựng cơ sở kiến thức đồ thị. Diễn giả đã giới thiệu hai cách tiếp cận triển khai có thể: sử dụng Amazon Bedrock Knowledge Bases với Neptune Analytics hoặc xây dựng một pipeline tùy chỉnh với các công cụ như LlamaIndex và lưu trữ dữ liệu đồ thị trong Amazon Neptune.

Phiên này giúp người tham dự hiểu rằng các hệ thống kiến thức không chỉ về lưu trữ tài liệu mà còn về mô hình hóa các mối quan hệ giữa các điểm dữ liệu.

### Lộ Trình Nghề Nghiệp Từ IT Helpdesk Đến Cloud và DevOps

Phiên cuối cùng đã chia sẻ một lộ trình nghề nghiệp thực tế từ IT Helpdesk đến Senior Sysadmin và sau đó hướng tới Cloud/DevOps. Diễn giả giải thích rằng Helpdesk là một điểm khởi đầu quan trọng vì nó xây dựng kỹ năng khắc phục sự cố, kỹ năng giao tiếp, kinh nghiệm hỗ trợ người dùng và kiến thức vận hành IT cơ bản.

Khi các chuyên gia chuyển hướng đến vai trò Quản trị viên Hệ thống, họ cần kiến thức mạnh hơn về máy chủ, mạng, giám sát, cập nhật, sao lưu, an ninh và tự động hóa.

Đối với các vai trò Cloud và DevOps, diễn giả nhấn mạnh tư duy cloud, kiến thức cơ bản về AWS, khả năng mở rộng linh hoạt, giá trả theo sử dụng, các dịch vụ quản lý, Infrastructure as Code với Terraform, kiểm soát phiên bản, CI/CD, Docker, giám sát và văn hóa DevOps.

Phiên này cũng nhấn mạnh tầm quan trọng của các dự án thực tế, một danh mục đầu tư rõ ràng và học tập thực hành liên tục. Nó giúp người tham dự hiểu rằng một nghề nghiệp Cloud/DevOps yêu cầu cả độ sâu kỹ thuật và kinh nghiệm vận hành thực tế.

## Điều Rút Ra Chính

### Docker và Tính Nhất Quán Trong Triển Khai

Docker giúp các ứng dụng chạy nhất quán trên các môi trường khác nhau. Điều này hữu ích cho phát triển, kiểm tra, triển khai và cộng tác nhóm.

### Kiến Trúc Cloud Thời Gian Thực

AWS WebSocket, Lambda và DynamoDB có thể được sử dụng để xây dựng các hệ thống thời gian thực đơn giản như ứng dụng chat, hệ thống phòng chơi, trò chơi theo lượt và các tính năng nhiều người chơi nhẹ.

### Tư Duy An Ninh Theo Nhiều Lớp

AWS WAF có thể chặn các mối đe dọa đã biết, trong khi Machine Learning có thể hỗ trợ phát hiện hành vi bất thường. Một hệ thống an ninh nên kết hợp lọc, ghi nhật ký, giám sát, cảnh báo và phát hiện bất thường.

### Giá Trị Của GraphRAG

GraphRAG hữu ích khi một hệ thống cần hiểu các mối quan hệ giữa các thực thể. Nó phù hợp cho các ứng dụng dựa trên kiến thức, chatbot nội bộ, phân tích mối quan hệ và các hệ thống hỏi đáp tài liệu.

### Hướng Nghề Nghiệp Cloud và DevOps

Một nền tảng vững chắc về khắc phục sự cố, mạng, Linux, máy chủ, Docker, tự động hóa, giám sát và AWS là quan trọng trước khi đi sâu hơn vào Cloud và DevOps.

## Ứng Dụng Vào Công Việc

Kiến thức từ Meetup này có thể được áp dụng cho việc học tập, các dự án cá nhân và phát triển nghề nghiệp tương lai.

Docker có thể được sử dụng để container hóa các ứng dụng web, API và cơ sở dữ liệu, làm cho các dự án dễ chạy hơn, chia sẻ và triển khai. Điều này đặc biệt hữu ích khi làm việc nhóm hoặc chuẩn bị một dự án cho demo hoặc sản xuất.

Phiên AWS WebSocket đã cho ý tưởng về việc xây dựng các tính năng thời gian thực như phòng chat, phòng nhiều người chơi, hệ thống thông báo hoặc các trò chơi trực tuyến đơn giản bằng cách sử dụng các dịch vụ AWS serverless.

Phiên AWS WAF và Machine Learning đã cải thiện tư duy an ninh của tôi. Khi thiết kế các ứng dụng web, tôi không chỉ nên tập trung vào các tính năng mà còn xem xét lọc yêu cầu, thu thập nhật ký, giám sát, cảnh báo và phát hiện hành vi bất thường.

Phiên AWS Neptune và GraphRAG đã gợi ý một hướng để xây dựng các hệ thống dựa trên kiến thức, chatbot nội bộ, công cụ phân tích tài liệu hoặc các hệ thống cần hiểu các mối quan hệ giữa dữ liệu.

Phiên chia sẻ nghề nghiệp đã giúp tôi xây dựng một lộ trình học tập rõ ràng hơn. Tôi nên tập trung vào Linux, mạng, Git, Docker, kiến thức cơ bản về AWS, CI/CD, giám sát, Infrastructure as Code và các dự án thực hành thực tế.

## Kế Hoạch Hành Động Cá Nhân

* Thực hành Docker bằng cách container hóa một ứng dụng web nhỏ và cơ sở dữ liệu.
* Xây dựng một demo thời gian thực đơn giản sử dụng các khái niệm WebSocket.
* Tìm hiểu thêm về AWS WAF, CloudWatch, GuardDuty và Security Hub.
* Học các khái niệm cơ bản về RAG, GraphRAG và cơ sở dữ liệu đồ thị.
* Khám phá Amazon Neptune hoặc mô hình hóa đồ thị thông qua một dự án cơ sở kiến thức nhỏ.
* Cải thiện kỹ năng Cloud/DevOps thông qua Linux, mạng, Git, Docker, CI/CD và Terraform.
* Xây dựng một dự án danh mục đầu tư thể hiện triển khai cloud, giám sát và tự động hóa.

## Suy Ngẫm Cá Nhân

Sự kiện Meetup vào ngày 6 tháng 6 năm 2026 là một trải nghiệm giá trị vì nó bao gồm nhiều chủ đề công nghệ hiện đại theo cách thực tế. Các phiên đã giúp tôi hiểu rằng các hệ thống thực tế thường yêu cầu nhiều công nghệ làm việc cùng nhau, bao gồm triển khai ứng dụng, giao tiếp thời gian thực, an ninh, mô hình hóa dữ liệu và vận hành cloud.

Một bài học quan trọng tôi nhận được là một hệ thống tốt không chỉ nên chạy chính xác mà còn phải ổn định, an ninh, có thể mở rộng, dễ bảo trì và phù hợp với nhu cầu người dùng thực tế. Điều này đã thay đổi cách tôi nghĩ về việc xây dựng các dự án phần mềm.

Phiên nghề nghiệp cũng có ý nghĩa vì nó cho thấy con đường hướng tới Cloud và DevOps yêu cầu một nền tảng vững chắc và thực hành liên tục. Thay vì chỉ học lý thuyết, tôi cần xây dựng các dự án thực tế, khắc phục các vấn đề thực tế và dần cải thiện kỹ năng kỹ thuật của mình.

Sau sự kiện, tôi cảm thấy có động lực hơn để tiếp tục học AWS, Docker, Kiến Trúc Cloud, DevOps, an ninh mạng và các hệ thống kiến thức liên quan đến AI.

> Tổng thể, sự kiện Meetup rất thực tế và có ý nghĩa. Nó cung cấp kiến thức hữu ích về triển khai phần mềm, kiến trúc cloud, an ninh mạng, GraphRAG và phát triển nghề nghiệp Cloud/DevOps. Sự kiện đã giúp tôi có được cả kiến thức kỹ thuật và một hướng rõ ràng hơn cho việc học tập trong tương lai.
