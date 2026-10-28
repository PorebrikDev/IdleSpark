# Idle Spark — мобильная и WebGL idle-игра на Unity

**Idle Spark** — это мобильная и WebGL idle-игра на Unity. Игрок открывает и улучшает 5 заведений, производит валюту автоматически, активирует бусты и покупает монеты через Yandex IAP.

👉 **[Играть в доработанную версию на itch.io](https://porebrikdev.itch.io/idle-spark)**

* **Роль:** Game Designer / Unity Developer
* **Задача:** Реализовать проект с нуля как тестовое задание за ~5 часов

<p align="center">
  <img src="https://github.com/user-attachments/assets/a3f1d6cf-06ef-41a3-a95e-f74639fba20d" width="100%" alt="Геймплей Idle Spark" />
</p>

---

## 🛠 Технический стек
| Технология | Примечание |
|---|---|
| **Unity 6** | 6000.3.22f1 |
| **Язык** | C# |
| **UI** | TextMeshPro |
| **Покупки** | Unity IAP v5 / Yandex IAP |
| **Тесты** | Unity Test Framework (Edit Mode) |
| **Платформы** | Android (APK), WebGL |
| **Сохранения** | JSON (`Application.persistentDataPath`) |

## ✨ Ключевые реализованные системы

- **Игровой цикл:** 5 idle-машин (от Ларька до Ресторана) с автоматическим доходом `CPS × deltaTime`.
- **Экономика:** Прогрессия уровней, рост цены апгрейдов и стоимости открытия новых заведений.
- **Буст:** Временное удвоение дохода (×2 на 5 минут) с привязкой к карточке машины.
- **Монетизация:** Внутриигровые покупки (Consumable-продукт), обработка ошибок и отмен.
- **Аналитика:** Событийная система на базе `IAnalyticsProvider` (готово к интеграции Firebase/AppMetrica).
- **Сохранения:** Автосохранение в JSON при сворачивании игры и ручное после действий.
<p align="center">
  <img src="https://github.com/user-attachments/assets/e033ff59-7a5b-4e9b-8f6b-42bc9a7ff2ea" width="100%" alt="Магазин и покупки" />
</p>

## 🎮 Мини-игры
В доработанной версии добавлены 5 мини-игр для разнообразия геймплея (аркада, сортировка, змейка, раннер, башенки).

<p align="center">
  <img src="https://github.com/user-attachments/assets/9978f3d7-36f9-4bbe-b928-db2a9db93835" width="32%" alt="Мини-игра 1" />
  <img src="https://github.com/user-attachments/assets/ba715f31-34ae-4c6f-85d8-b7ea2fe52c21" width="32%" alt="Мини-игра 2" />
  <img src="https://github.com/user-attachments/assets/b4c63b55-b46b-4bde-9e9c-f877a284619e" width="32%" alt="Мини-игра 3" />
</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/3e16668f-02fb-4a9e-be35-af931cebbe29" width="49%" alt="Мини-игра 4" />
  <img src="https://github.com/user-attachments/assets/c8d0cd04-35ab-4456-80aa-ac18cbeca248" width="49%" alt="Мини-игра 5" />
</p>

---

## Для работодателей и ревьюеров

Этот проект демонстрирует:
- **Понимание Game Design:** проектирование экономики, формул стоимости, кривой прокачки и темпа прогресса.
- **Архитектурный подход:** четкое разделение логики, конфигурации (ScriptableObjects) и UI (MVC-подобная структура).
- **Работа с данными:** JSON-сериализация, обработка офлайн-времени.
- **Качество кода:** покрытие критичной бизнес-логики (экономика) Unit-тестами, использование событийной модели.

<details>
<summary><b>👀 Нажмите, чтобы посмотреть детали архитектуры и ограничения</b></summary>

### Структура проекта
- `Mashine`, `Controller` — чистая логика без Unity UI.
- `DataMashine` — ScriptableObject для базовых параметров.
- `MachineCard`, `FactoryUI` — визуальная часть.
- `SaveService`, `IapService`, `Analytics` — сервисные прослойки.

### Известные ограничения
- Офлайн-доход не начисляется (сохраняется только время выхода).
- Буст не сохраняется при перезапуске.
- Параметры буста захардкожены в коде (вынос в конфиг — в планах).
- Analytics: реализован только console-провайдер.

### Roadmap
1. Внедрение офлайн-прогресса.
2. Вынос настроек буста в ScriptableObject.
3. Интеграция реальных SDK аналитики.
4. Добавление Play Mode тестов.

</details>

---
## 🚀 Запуск и сборка

**В Unity:** Открыть проект → сцена `Assets/Scenes/Main.unity` → Play.
**Android:** File → Build Settings → Switch Platform (Android) → Build (APK).
