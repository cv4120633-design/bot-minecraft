# Sweet PvP Bot — مود Fabric لـ Minecraft 26.1.2

مود بيضيف بوت اسمه **Sweet**:
- بيقاتل PvP (بيهاجم أقرب لاعب، ماسك سيف، مقاوم للاشتعال بالشمس).
- بيرد بالكلام عن طريق ذكاء اصطناعي حقيقي (API متوافق مع OpenAI Chat Completions).

## الأوامر
- `/sweet spawn` — يستدعي Sweet جنبك.
- `/sweet chat <رسالة>` — يبعت رسالتك لأقرب Sweet وياخد رد من الـ AI في الشات.

## الإعداد قبل التشغيل
1. شغّل السيرفر مرة عشان يتعمل الملف `config/sweetpvpbot.json` تلقائيًا.
2. افتح الملف وحط الـ API Key بتاعك:
```json
{
  "apiEndpoint": "https://api.openai.com/v1/chat/completions",
  "apiKey": "ضع_مفتاحك_هنا",
  "model": "gpt-4o-mini"
}
```
3. لو بتستخدم مزود API تاني (غير OpenAI) غيّر `apiEndpoint` و `model` على حسب توثيق المزود، طالما الصيغة متوافقة مع Chat Completions.

## ⚠️ ملاحظة مهمة جدًا عن الإصدار 26.1.2
لعبة Minecraft ابتداءً من نسخة **26.1** بقت **غير مشفّرة (unobfuscated)**، وبقى الموددرز
بيستخدموا **أسماء موجانج الرسمية (Official Mappings)** مباشرة بدل Yarn. ده تغيير كبير حصل
بعد آخر تحديث لمعلوماتي، فالكود ده اتكتب بمنطق ومنهجية صحيحة (goals، attributes، entity
registration، commands...) لكن بأسماء كلاسات على طريقة Yarn القديمة المعروفة زي:
`ZombieEntity`, `PlayerEntity`, `ServerWorld`, `EntityType`...

**قبل الـ build لازم:**
- تفتح المشروع في IntelliJ IDEA (بعد `./gradlew genSources` أو حسب توثيق Loom لإصدار 26.1.2).
- تخلي الـ IDE يقترح عليك الأسماء الصحيحة الرسمية (ممكن تكون اتغيرت زي `Zombie` بدل
  `ZombieEntity`، `Level` بدل `World`، `Player` بدل `PlayerEntity`).
- تصلّح أي `import` أو اسم كلاس/ميثود ما يتلاقيش، والـ IDE هيوجهك تلقائيًا.

ده أمر طبيعي ومتوقع لأي مود بيتعمل على 26.1+ حاليًا، مش خطأ في المنطق نفسه.

## البناء
```bash
./gradlew build
```
الملف الناتج هيكون في `build/libs/sweet-pvp-bot-1.0.0.jar`.

## متطلبات
- Java 25+
- Fabric Loader 0.19.3+
- Fabric API 0.154.2+26.1.2
