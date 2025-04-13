# Hairly

💇‍♀️ A LINE bot for personalized haircare product recommendations.

Powered by:
- FastAPI
- OpenAI GPT
- Pinecone for vector search
- LINE Messaging API

## 開發啟動方式

```bash
poetry install --extras "dev"
poetry run uvicorn app.main:app --reload


hairly/
├── README.md
├── .env
├── .env.example
├── pyproject.toml
├── poetry.lock
├── main.py                            ✅ ✅ 建議移進 backend/，保持結構清晰
│
├── backend/                           ✅ 新增 backend/ 作為後端根目錄（未來打包更乾淨）
│   ├── main.py                        ← FastAPI 進入點（移進來）
│   ├── services/
│   │   ├── embedding.py
│   │   ├── recommend.py
│   │   └── pinecone_client.py
│   ├── line/
│   │   ├── router.py
│   │   └── flex_builder.py
│   ├── data/
│   │   ├── products.json
│   │   └── embeddings.json
│   ├── utils/
│   │   └── text_cleaner.py
│   └── tests/
│       └── test_recommend.py
│
├── frontend/                          ← 前端保持原樣
│   ├── package.json
│   ├── vite.config.js / next.config.js
│   └── src/
│       ├── App.vue / index.tsx
│       └── api/
│           └── recommend.ts
│
├── docker-compose.yml
├── Dockerfile                         ✅ Dockerfile 移至 backend/ 或根目錄都 OK（看部署工具）
├── .dockerignore
│
└── .github/
    └── workflows/
        └── deploy.yml

