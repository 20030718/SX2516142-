# Medical-QA-System：基于RAG的医学问答系统

## 项目简介
本项目是一套基于**检索增强生成（RAG）** 的医学问答系统，核心整合百度翻译API、FAISS向量检索、DeepSeek大模型，实现「中文医学问题→英文文献检索→精准医学回答」的端到端流程。

## 核心功能
1. **医学文本翻译**：封装百度通用翻译API，实现中文医学问题到英文的精准翻译（术语适配）；
2. **RAG检索**：基于FAISS构建医学文献向量库，支持不同相似度阈值下的精准检索；
3. **大模型问答**：调用DeepSeek API，结合检索结果生成专业医学回答；

## 目录结构
```
medical-qa-system/
├── src/                        # 源代码文件夹
│   ├── model/                  # 核心模型模块
│   │   ├── llm_api.py          # 大模型问答逻辑（DeepSeek API调用）
│   │   ├── rag.py              # RAG检索实现（FAISS构建、索引构建、相似度检索）
│   │   ├── translate.py        # 百度通用翻译封装（医学文本中英互译）
│   ├── util/                   # 工具模块
│   │   └── download_pubmed.py  # PubMed 文献数据下载与预处理
│   ├── chat_web.py                 # 前端页面
│   ├── pubmed.json                 # PubMed 医学文献语料库
│   └── requirements.txt            # 依赖库列表
├── results/                    # 实验结果
│   ├── medical_translation_report.txt        # 翻译结果对比文件
│   └── medical_translation_response_time.txt # 翻译时间折线图
├── scripts/                    # 运行脚本
│   └── run.sh                  # 一键运行脚本
└── README.md                   # 说明文档
```
## 运行

见scripts/run.sh 
第一次拉取需自行生成向量数据库，使用脚本即可自动构建。
