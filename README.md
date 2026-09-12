#  Driving Handbook RAG Assistant

یک پروژه‌ی **Retrieval-Augmented Generation (RAG)** برای ساخت دستیار هوشمند مبتنی بر کتاب قوانین و مقررات رانندگی.

هدف پروژه، پیاده‌سازی یک سیستم Question Answering است که به‌جای تکیه بر دانش عمومی مدل زبانی، پاسخ‌ها را از یک **Knowledge Base اختصاصی** بازیابی کرده و بر اساس آن تولید می‌کند.

## 💡 ایده و معماری

مسیر پردازش سؤال به شکل زیر است:

```text
PDF
 ↓
OCR
 ↓
Text Chunking
 ↓
Qwen3-VL-Embedding-2B
 ↓
Qdrant Vector Database
 ↓
Semantic Retrieval
 ↓
Reranking
 ↓
Context Construction
 ↓
OpenRouter LLM
 ↓
Streaming Answer
 ↓
Gradio
```

برای افزایش دقت، ابتدا چندین نتیجه از Vector Database بازیابی شده و سپس با **Reranking** مرتبط‌ترین بخش‌ها انتخاب می‌شوند. این Context به مدل زبانی داده می‌شود تا پاسخ بر اساس محتوای واقعی کتاب تولید شود.

همچنین **شماره صفحات منابع** به پاسخ اضافه می‌شود تا نتیجه قابل بررسی و Traceable باشد.

##  نکات فنی

- OCR برای پردازش PDF اسکن‌شده
- Semantic Search با Embedding Model
- Qdrant به عنوان Vector Database
- Two-Stage Retrieval با Reranking
- LLM Generation از طریق OpenRouter API
- Streaming Response
- رابط کاربری Gradio
- Source Attribution با شماره صفحات
- طراحی Stateless؛ هر سؤال مستقل پردازش می‌شود

##  Tech Stack

**Python · Google Colab · Hugging Face · Qwen · Qdrant · OpenRouter · Gradio · OCR**

##  محیط توسعه

کل فرآیند توسعه و اجرای پروژه در **Google Colab** انجام شده است.

به دلیل حجم و ماهیت PDF، Pipeline پردازش سند، Embedding و Vector Search در محیط Colab پیاده‌سازی شده‌اند.

برای مشاهده نتیجه اجرای پروژه و نمونه خروجی رابط کاربری، تصاویر در پوشه‌ی:

```text
samples/
```

قرار داده شده‌اند.

##  هدف پروژه

این پروژه صرفاً یک Chatbot ساده نیست؛ هدف آن نمایش توانایی طراحی و پیاده‌سازی یک **End-to-End RAG Pipeline** از مرحله‌ی پردازش Document تا Retrieval، Reranking و LLM Generation است.

این پروژه نمونه‌ای عملی از کار با **LLM Applications، Information Retrieval، Embeddings و Vector Databases** و نحوه اتصال این اجزا برای حل یک مسئله واقعی است.

