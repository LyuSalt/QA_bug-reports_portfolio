Название: XSS уязвимость через API регистрации + слабая валидация

Описание ошибки: Сервер принимает и сохраняет XSS payload <script>alert('XSS')</script> в поле имени + невалидный email 123@lmail.ru без ошибок валидации.

Шаги воспроизведения:	
1. Перейти на сайт по ссылке: https://cozy-studio.ru/
2. Выбрать "Записаться онлайн"
3. Выбрать "Личный кабинет"
4. Выбрать "Регистрация"
5. Ввести: Имя: <script>
           Телефон: +7(999)999 99 99
           Email: 123@lmail.ru
6. Поставить галочку напротив "Я соглашаюсь с условиями Пользовательского соглашения" и подтвердить регистрацию.
    
Ожидаемый результат:	
400 Bad Request {
    "error": {
        "name": "Invalid characters",
        "email": "Invalid format"
    }

Фактический результат:
200 OK {
    "message": {
        "code": 200,
        "message": "user registered",
        "type": "existed device"
    }
}

Severity: Critical  
Priority: High 

Окружение:	Яндекс Браузер [Версия 25.12.3.1126 (64-bit)]

Вложения DevTools:
<img width="1920" height="1080" alt="2026-02-16_15-47-57" src="https://github.com/user-attachments/assets/eb3bfe08-697c-4e89-8035-0e7a6b30db35" />

<img width="1920" height="1080" alt="2026-02-16_15-48-04" src="https://github.com/user-attachments/assets/ee56afe0-aa1f-42d9-a099-49179f3a7749" />

<img width="1920" height="1080" alt="2026-02-16_15-48-24" src="https://github.com/user-attachments/assets/93d66ae2-4699-4732-b7fa-1850b76e0b2d" />

<img width="1920" height="1080" alt="2026-02-16_15-51-25" src="https://github.com/user-attachments/assets/5aaa5e06-d10d-471f-9d64-df95ea3b9464" />

Вложения Postman:

<img width="1920" height="1080" alt="2026-02-16_20-43-10" src="https://github.com/user-attachments/assets/a337045b-807f-43be-ac79-53804acfd61d" />
