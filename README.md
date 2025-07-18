# 📱 Інструмент пакувальника v3.0

Професійна програма для сканування штрихкодів з автоматичними скриншотами через RTSP реєстратори та IP камери.

## 🌟 Основні функції

- **📊 Сканування штрихкодів** - підтримка усіх стандартних форматів
- **📸 Автоматичні скриншоти** - з RTSP реєстраторів та IP камер
- **📱 Telegram інтеграція** - миттєві повідомлення та фото
- **📊 Excel звіти** - автоматичне ведення журналів
- **👥 Управління пакувальниками** - система ID та штрихкодів
- **🎥 Підтримка RTSP** - Hikvision, Dahua, Axis, Foscam та інші
- **🗂️ Організація файлів** - автоматичне створення сесій та папок

## 🛠️ Встановлення

### 1. Завантажте репозиторій
```bash
git clone https://github.com/dabik1/ScanF.git
cd ScanF
```

### 2. Встановіть залежності
```bash
pip install -r requirements.txt
```

### 3. Запустіть програму
```bash
python main.py
```

## 📋 Системні вимоги

- **Python** 3.7 або новіше
- **Windows/Linux/macOS** - кросплатформенність
- **Мережеве підключення** - для роботи з камерами та Telegram

## 🚀 Швидкий старт

### 1. Налаштування Telegram
1. Створіть бота через [@BotFather](https://t.me/BotFather)
2. Отримайте токен бота
3. Дізнайтеся Chat ID вашого чату
4. Введіть дані в розділі "📱 Основні налаштування"

### 2. Налаштування камери/реєстратора
1. Перейдіть в розділ "🎥 RTSP реєстратор"
2. Введіть IP адресу, логін та пароль
3. Оберіть виробника (Hikvision, Dahua, тощо)
4. Натисніть "🔍 Тест RTSP" для перевірки

### 3. Додавання пакувальників
1. В розділі "📱 Основні налаштування"
2. Натисніть "➕ Додати"
3. Введіть 3-значний ID та ім'я
4. Використовуйте "📊 Показати код" для генерації штрихкода

### 4. Початок роботи
1. Перейдіть в розділ "📊 Сканування"
2. Спочатку проскануйте ID пакувальника (3 цифри)
3. Потім скануйте штрихкоди товарів
4. Натискайте Enter після кожного сканування

## 🎯 Принцип роботи

1. **Авторизація пакувальника** - сканування 3-значного ID
2. **Створення сесії** - автоматична папка з часом та іменем
3. **Сканування товарів** - кожен штрихкод → скриншот → Telegram → Excel
4. **Організація файлів** - всі дані зберігаються в структурованому вигляді

## 📁 Структура файлів

```
SkanerFoto/
├── sessions/                    # Папки сесій пакувальників
│   ├── 2024-12-15_10-30-00_Іван_123/
│   │   ├── session_log.xlsx     # Excel журнал
│   │   ├── товар1_timestamp.jpg # Фото з підписами
│   │   └── товар2_timestamp.jpg
│   └── temp/                    # Тимчасові файли
├── config.json                  # Налаштування (автосоздається)
└── app.log                     # Журнал програми
```

## 🔧 Налаштування RTSP

### Підтримувані виробники:
- **Hikvision** - `rtsp://admin:password@IP:554/Streaming/Channels/101`
- **Dahua** - `rtsp://admin:password@IP:554/cam/realmonitor?channel=1&subtype=0`
- **Axis** - `rtsp://admin:password@IP:554/axis-media/media.amp`
- **Foscam** - `rtsp://admin:password@IP:554/videoMain`
- **Загальний** - `rtsp://admin:password@IP:554/live/ch1`

### Рекомендації:
- Використовуйте **основний потік** для кращої якості
- **Порт 554** - стандартний для RTSP
- **Канал 1** - зазвичай основна камера
- Перевірте **мережеві налаштування** та **фаєрвол**

## 📨 Telegram повідомлення

### Автоматичні повідомлення:
- 🧑‍🏭 **Початок роботи** - коли пакувальник входить в систему
- 📦 **Кожен товар** - фото + штрихкод + час + пакувальник

### Ручні повідомлення:
- 🕐 **Перерва на обід** 
- ✅ **Кінець зміни**
- 🚨 **Проблеми**
- 📦 **Товар відсутній**

## 📊 Excel звіти

Автоматично створюються файли `session_log.xlsx` з даними:
- **Час** сканування
- **Штрихкод** товару
- **Пакувальник** (з сесії)

## 🛡️ Безпека

- **Локальне зберігання** - всі дані на вашому комп'ютері
- **Шифрування паролів** - в інтерфейсі (зірочки)
- **Приватні налаштування** - config.json не включається в Git
- **Очищення** - автоматичне видалення старих файлів (2 тижні)

## 🧹 Обслуговування

### Автоматичне очищення:
- **Тимчасові файли** - видаляються через 1 годину
- **Старі сесії** - можна видалити через 2 тижні
- **Логи** - ведуться в app.log

### Ручне очищення:
- Розділ "📊 Сканування" → "🗑️ Видалити файли старше 2 тижнів"

## 🔍 Діагностика проблем

### Проблеми з камерою:
1. **Тест підключення** - кнопка "🔍 Тест" у налаштуваннях
2. **Перевірте IP адресу** - пінг до камери
3. **Логін/пароль** - права доступу
4. **Мережа** - фаєрвол та VPN

### Проблеми з RTSP:
1. **Тест RTSP** - кнопка "🔍 Тест RTSP"
2. **Виробник** - оберіть правильний шаблон
3. **Канал** - перевірте номер каналу
4. **OpenCV** - встановіть `pip install opencv-python`

### Проблеми з Telegram:
1. **Токен бота** - перевірте правильність
2. **Chat ID** - має бути числом
3. **Інтернет** - перевірте підключення
4. **Блокування** - деякі корпоративні мережі блокують Telegram

## 📝 Журнали

Всі події записуються в `app.log`:
```
2024-12-15 10:30:00 [INFO] Запущено GUI додаток
2024-12-15 10:30:15 [INFO] Обрано пакувальника: Іван (ID 123)
2024-12-15 10:30:30 [INFO] Оброблено штрихкод: 1234567890123
```

## 🔄 Оновлення

Для оновлення програми:
```bash
git pull origin main
pip install -r requirements.txt --upgrade
```

## 🤝 Підтримка

### При проблемах:
1. **Перевірте логи** - файл `app.log`
2. **Тести підключення** - використовуйте вбудовані тести
3. **Перезапуск** - закрийте та запустіть програму знову
4. **Переустановка** - `pip install -r requirements.txt --force-reinstall`

### Вимоги до звернень:
- Опис проблеми
- Скриншот помилки
- Фрагмент з app.log
- Версія Python (`python --version`)

## 📈 Можливі покращення

- 🔔 **Push-повідомлення** в реальному часі
- 📊 **Аналітика продуктивності** пакувальників
- 🏭 **Багато складів** одночасно
- 📱 **Мобільний додаток** для менеджерів
- 🤖 **Штучний інтелект** для розпізнавання товарів
- ☁️ **Хмарна синхронізація** даних

## 📄 Ліцензія

Проект розроблений для внутрішнього використання.

## 🏷️ Версії

- **v3.0** - RTSP підтримка, покращений інтерфейс
- **v2.x** - Telegram інтеграція, Excel звіти  
- **v1.x** - Базове сканування штрихкодів

---

**Автор:** dabik1  
**Репозиторій:** https://github.com/dabik1/ScanF  
**Останнє оновлення:** Грудень 2024
