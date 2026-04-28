

#define SIZE 5
قمت بتحديد حجم الـ Buffer ليكون 5 خانات فقط،
وذلك ليكون أصغر من حجم النص المدخل بهدف إثبات عمل الالتفاف (Wrap Around).
typedef struct {
    char buffer[SIZE];
    int head;
    int tail;
    int count;
} CircularBuffer;
يحتوي الهيكل على:
buffer: مصفوفة تخزن البيانات.
head: مؤشر القراءة (أول عنصر جاهز للقراءة).
tail: مؤشر الكتابة (أول مكان فارغ للكتابة).
count: عدد العناصر الحالية داخل البافر.

void init(CircularBuffer *cb)
تقوم بإعادة ضبط البافر إلى حالته الابتدائية:
تعيين head = 0
تعيين tail = 0
تعيين count = 0
bool isFull(CircularBuffer *cb)
تعيد true إذا كان عدد العناصر يساوي حجم البافر.

bool isEmpty(CircularBuffer *cb)
تعيد true إذا لم يكن هناك أي عنصر داخل البافر.

void writeBuffer(CircularBuffer *cb, char data)
تقوم بإضافة عنصر جديد إلى البافر:
التحقق إذا كان ممتلئًا.
تخزين العنصر في موقع tail.

tail = (tail + 1) % SIZE;
وهذا يحقق الالتفاف عند الوصول لنهاية المصفوفة
char readBuffer(CircularBuffer *cb)
تقوم بإزالة عنصر من البافر:
التحقق إذا كان فارغًا.
قراءة العنصر عند head.
تحريك head بنفس آلية الالتفاف.
آلية عمل البرنامج الرئيسي

scanf("%99s", name);
يطلب البرنامج من المستخدم إدخال اسمه.
strcpy(finalText, name);
strcat(finalText, "CE-ESY");
يتم دمج اسم المستخدم مع النص الثابت "CE-ESY"
for (...)
يقوم البرنامج بإدخال الأحرف واحدًا تلو الآخر داخل البافر.

if (isFull(&cb))
يقوم البرنامج بقراءة عنصر لإفراغ مكان قبل إدخال عنصر جديد.

while (!isEmpty(&cb))
بعد انتهاء الإدخال، تتم قراءة وطباعة كل العناصر المتبقية داخل البافر.
مفهوم الالتفاف (Wrap Around)

(index + 1) % SIZE
فعند وصول المؤشر إلى آخر خانة:
يعود تلقائيًا إلى بداية المصفوفة.

