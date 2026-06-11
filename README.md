# 🤖 AI-Powered Hybrid Customer Support Bot

Bot Telegram otomatis yang menggabungkan database statis dan AI (LLM) untuk menjawab pertanyaan pelanggan secara cerdas, cepat, dan efisien. Dibangun dengan **n8n workflow automation** dan **100% free-tier services**.

![Status](https://img.shields.io/badge/Status-Inactive%20(Trial%20Ended)-orange)
![Tech Stack](https://img.shields.io/badge/Tech-n8n%20%7C%20Telegram%20%7C%20Google%20Sheets%20%7C%20Groq%20AI-blue)

---

## 🎯 Masalah yang Diselesaikan

1. **Customer service overload** - Pertanyaan FAQ yang berulang memakan waktu tim support
2. **Response time lambat** - Pelanggan harus menunggu untuk jawaban sederhana
3. **Biaya infrastruktur** - Solusi customer service berbasis AI biasanya mahal
4. **Akurasi vs Fleksibilitas** - Database kaku, tapi AI murni bisa berhalusinasi

---

## 💡 Solusi

Sistem **Hybrid Intelligence** yang menggabungkan keunggulan database dan AI:

### **Prioritas 1: Database (Google Sheets)**
- Jawaban 100% akurat untuk pertanyaan FAQ
- Response time < 1 detik
- Mudah diupdate tanpa coding

### **Prioritas 2: AI Fallback (Groq/Llama 3)**
- Menjawab pertanyaan di luar database
- Kontekstual dan natural
- Biaya $0 (menggunakan Groq free tier)

### **Logging & Analytics**
- Semua percakapan tercatat otomatis
- Tracking sumber jawaban (Database vs AI)
- Data untuk continuous improvement

---

## 🛠️ Tech Stack (100% Free Tier)

| Component | Technology | Purpose |
|-----------|-----------|---------|
| **Orchestration** | [n8n](https://n8n.io/) | Workflow automation & integration |
| **Interface** | Telegram Bot API | User interface & messaging |
| **Database** | Google Sheets | FAQ storage & logging |
| **AI/LLM** | [Groq API](https://groq.com/) (Llama 3 70B) | Intelligent fallback responses |
| **Authentication** | OAuth2 & Header Auth | Secure API access |

---

## 📸 Workflow Architecture

![Workflow Architecture](workflow-canvas.png)

### **Alur Logika:**

User → Telegram Message
↓
n8n Trigger
↓
Search in Google Sheets (KnowledgeBase)
↓
┌────┴────┐
│ │
FOUND NOT FOUND
│ │
↓ ↓
TRUE FALSE
│ │
↓ ↓
Send DB Query Groq AI
Answer │
│ ↓
└──→ Send AI Answer
↓
Log to Google Sheets

---

## ✨ Fitur Utama

### 1. **Smart Response Routing**
- Otomatis memilih sumber jawaban terbaik
- Prioritas database untuk akurasi
- Fallback AI untuk fleksibilitas

### 2. **Real-time Logging**
Setiap percakapan dicatat dengan detail:
- **Timestamp**: Waktu pertanyaan
- **User ID**: Identitas penanya
- **Pertanyaan**: Teks pertanyaan
- **Jawaban**: Response yang diberikan
- **Sumber**: Database atau AI Groq

### 3. **Zero-Cost Infrastructure**
- n8n Cloud (14-day trial)
- Google Sheets (Free tier)
- Groq API (Free tier dengan rate limit generous)
- Telegram Bot API (100% free)

### 4. **Easy Maintenance**
- Update FAQ cukup edit Google Sheets
- Tidak perlu deploy ulang
- Tidak perlu coding

---

## 📂 Struktur File
├── workflow.json # n8n workflow (siap import)
├── README.md # Dokumentasi ini
├── workflow-canvas.png # Screenshot workflow
├── telegram-demo.png # Demo percakapan
└── sheets-logging.png # Contoh logging data

---

⚠️ Status Bot: Tidak Aktif (Trial Ended)
Mengapa Bot Tidak Aktif?
Bot ini dibangun menggunakan n8n Cloud Free Trial yang memiliki masa aktif 14 hari. Saat ini trial telah berakhir, sehingga:
❌ Bot tidak dapat membalas pesan secara otomatis
❌ Workflow di n8n berada dalam mode inactive
✅ Semua kode dan workflow TETAP UTUH dan dapat digunakan
✅ File workflow.json dapat di-import ke instance n8n manapun

---

📊 Contoh Penggunaan
Pertanyaan di Database (Jalur TRUE):📊 Contoh Penggunaan
Pertanyaan di Database (Jalur TRUE):
User: jam operasional
Bot: Kami buka setiap hari Senin - Jumat, pukul 09.00 - 17.00 WIB.
[Sumber: Database | Response time: <1s]

Pertanyaan Kompleks (Jalur FALSE - AI):
User: apa itu n8n?
Bot: N8n adalah sebuah platform otomatisasi alur kerja yang memungkinkan 
     pengguna untuk menghubungkan berbagai aplikasi dan layanan secara 
     visual dan membangun alur kerja kustom...
[Sumber: AI Groq/Llama 3 | Response time: ~2s]

---

🔒 Keamanan & Best Practices
✅ API Key disimpan di n8n Credentials (terenkripsi)
✅ Tidak ada secret yang ter-expose di workflow.json
✅ GitHub Secret Scanning passed ✓
✅ Google Sheets OAuth2 authentication
✅ Input sanitization (toLowerCase untuk matching)

---

📈 Metrik & Hasil
| Metric | Value |
| :--- | :--- |
| Response Time (DB) | < 1 detik |
| Response Time (AI) | ~2 detik |
| Accuracy (DB) | 100% |
| Cost | $0 (free tier) |
| Setup Time | < 30 menit |

---

🙏 Acknowledgments
n8n - Workflow automation yang powerful
Groq - AI inference superfast
Telegram - Messaging platform yang reliable
Google Sheets - Database sederhana yang efektif

---

⚡ Dibuat dengan menggunakan n8n & AI
