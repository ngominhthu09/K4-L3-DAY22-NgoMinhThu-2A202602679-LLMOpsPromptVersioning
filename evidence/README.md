# Báo cáo nộp bài — Day 22: LangSmith & Prompt Versioning

## LangSmith project

Project `day22-lab` có **100 traces** trong ảnh minh chứng:

[LangSmith — day22-lab]: https://smith.langchain.com/public/2e0454f9-271c-404b-bab6-9d9df8637f45/r/01a11c09-e118-7a62-983d-cd1cd4cdc166?start_time=2026-10-08T15%3A02%3A51.925296Z

## So sánh RAGAS: Prompt V1 và V2

Các điểm dưới đây được đọc từ [03_ragas_report.json](03_ragas_report.json), kết quả đánh giá 50 câu hỏi cho mỗi prompt.

| Chỉ số            | Prompt V1 | Prompt V2 | Nhỉnh hơn |
| ----------------- | --------: | --------: | --------- |
| Faithfulness      |    0.9455 |    0.9428 | V1        |
| Answer relevancy  |    0.9155 |    0.8916 | V1        |
| Context recall    |    1.0000 |    1.0000 | Hòa       |
| Context precision |    0.9450 |    0.9473 | V2        |

Cả hai phiên bản đều đạt faithfulness trên 0.9 (vượt ngưỡng yêu cầu 0.8); báo cáo đánh dấu `target_met: true`. V1 nhỉnh hơn về faithfulness và answer relevancy, còn V2 nhỉnh hơn nhẹ về context precision. Context recall bằng nhau, phù hợp với việc hai phiên bản dùng cùng pipeline truy xuất.

## Minh chứng

- `01_langsmith_100_traces.png` — project LangSmith hiển thị 100 traces cho `step1 OR step2`.
- `01_langsmith_traces.png` — traces của RAG pipeline.
- `02_prompt_hub_v1.png`, `02_prompt_hub_v2.png` — hai prompt trên LangSmith Prompt Hub.
- `02_ab_routing_log.txt` — kết quả định tuyến 50 câu hỏi giữa V1/V2.
- `03_ragas_scores.png`, `03_ragas_report.json` — bảng điểm và dữ liệu RAGAS.
- `04_pii_demo_log.txt`, `04_json_demo_log.txt` — kết quả kiểm thử PII redaction và JSON validation.

## Kết luận

Đã hoàn thành bốn checkpoint: RAG tracing, Prompt Hub/A-B routing, đánh giá RAGAS và Guardrails validators. Nộp trên LMS **URL GitHub repository public** và **URL project LangSmith** ở trên; giữ `.env` và API keys ngoài Git.
