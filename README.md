# 📏🔊 Ultrasonic Sensor → TN TN Voice Alert

هذا المشروع يستخدم **حساس الموجات فوق الصوتية Ultrasonic Sensor** مع Arduino لاكتشاف الأشياء القريبة.

عندما تصبح المسافة أقل من **50 cm**، يرسل Arduino إشارة إلى الحاسوب، ثم يمكن لبرنامج Python تشغيل صوت:

🔊 **TN TN**

---

## 🎯 فكرة المشروع

يعمل المشروع بهذه الطريقة:

**Ultrasonic Sensor** 📏
⬇️
يقيس المسافة
⬇️
إذا كانت المسافة أقل من 50 cm
⬇️
Arduino يرسل إشارة
⬇️
💻 Python يشغل صوت **TN TN**

---

## 🧰 المكونات

* Arduino Uno 🤖
* Ultrasonic Sensor HC-SR04 📏
* Breadboard
* Jumper Wires
* USB Cable
* Computer 💻
* Python 🐍
* Audio file 🔊

---

## 🔌 التوصيل

| HC-SR04 | Arduino |
| ------- | ------- |
| VCC     | 5V      |
| GND     | GND     |
| TRIG    | Pin 9   |
| ECHO    | Pin 10  |

---

## 💻 كود Arduino

```cpp
int trigPin = 9;
int echoPin = 10;

long duration;
float distance;

void setup()
{
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);

  Serial.begin(9600);
}

void loop()
{
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);

  distance = duration * 0.034 / 2;

  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  if (distance < 50)
  {
    Serial.println("TN_ALERT");
    delay(1000);
  }

  delay(100);
}
```

---

## 🧠 كيف يعمل؟

Arduino يقيس المسافة باستخدام حساس **HC-SR04**.

إذا كانت:

```text
Distance < 50 cm
```

فهذا يعني أن هناك جسمًا قريبًا.

عندها يرسل Arduino إشارة إلى الحاسوب:

```text
TN_ALERT
```

ويستطيع برنامج Python استقبال هذه الإشارة وتشغيل صوت **TN TN**. 🔊

---

## 🔊 الصوت

يمكن استخدام ملف صوتي مثل:

```text
tn.mp3
```

ويتم تشغيله بواسطة Python عند اكتشاف جسم قريب.

---

## 📚 في كتاب Arduino

هذا المشروع مرتبط بدرس:

**Ultrasonic Sensor → إذا كانت المسافة أقل من 50 cm → صوت TN TN**

---

## 🚀 ماذا تعلمنا؟

من خلال هذا المشروع تعلمنا:

* 📏 قياس المسافة
* 🔌 استخدام HC-SR04
* 💻 إرسال البيانات عبر Serial
* 🧠 استخدام `if`
* 🔊 التحكم في تشغيل صوت من الحاسوب
* 🐍 الربط بين Arduino وPython
