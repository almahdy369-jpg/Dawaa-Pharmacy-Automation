# Dawaa Pharmacy Automation

نظام حجز أدوية عبر واتساب مبني بـ n8n. العميل يبعت اسم الدواء والكمية، والنظام يتحقق من المخزون ويحجز تلقائياً، والحالات الصعبة تتحول لصيدلي عبر تليجرام.

**Live page:** https://almahdy369-jpg.github.io/Dawaa-Pharmacy-Automation/

## Workflows

| Workflow | Trigger | What it does |
|---|---|---|
| dawaa-main | WhatsApp + Telegram | يستقبل رسالة العميل، يستخرج الأدوية بالـ AI، يطابقها مع الكتالوج ويسجل الحجز، ثم قرار الصيدلي (Approve / Reject) وخصم المخزون والرد على العميل |
| dawaa-errors-and-schedules | Error Trigger + Schedule | تصنيف الأخطاء وتنبيهات، إرجاع المخزون للحجوزات المنتهية كل 15 دقيقة، قايمة إعادة الطلب يومياً 10 مساءً |

## Services

n8n (Docker) · ngrok · WhatsApp Business Cloud API · Telegram Bot · Google Sheets · Gmail · Gemini / Groq

## Import steps

1. شغّلي n8n بـ Docker وعيّني `WEBHOOK_URL` على دومين ngrok.
2. استوردي الملفات من فولدر `workflows` (Import from File).
3. أنشئي الـ Credentials: Google Sheets, Gmail, Telegram, WhatsApp, Gemini/Groq.
4. اختاري ملفات الـ Google Sheets بتاعتك في كل نود (الكتالوج والحجوزات).
5. ضبطي Error workflow على `dawaa-errors-and-schedules` في كل workflow.
6. فعّلي الـ workflows.

## Notes

المشروع شغال على WhatsApp Test Number، فلتجربته لازم رقمك يتضاف في Allowed List من Meta.