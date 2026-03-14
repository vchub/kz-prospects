# Telegram Bot Conversation Script

## Entry — User taps link from ad / 2GIS / UGC

---

**[BOT]**
> Привет! 👋
> Это акция от Coca-Cola — получи бесплатный напиток в ближайшем магазине.
>
> Выбери, что хочешь попробовать:

```
[ 🔴 Coca-Cola ]  [ 🟠 Fanta ]  [ 🟢 Sprite ]
```

---

**[USER taps e.g. Fanta]**

**[BOT]**
> Отличный выбор! 🟠
>
> Твой купон на **Fanta** готов.
> Действует **30 дней** — до 12 апреля 2026.
>
> Когда будешь готов забрать напиток — нажми **Активировать**.

```
[ Активировать ]     [ Поделиться с другом ]
```

> _(купон сохранён в этом чате — можешь вернуться в любой момент)_

---

## Flow A — User activates immediately or later

---

**[USER taps Активировать]**

**[BOT]**
> Где будешь забирать напиток?

```
[ Magnum ]   [ CU ]   [ Glovo ]
```

---

**[USER taps e.g. Magnum]**

**[BOT — shows coupon card image + barcode]**
> ✅ Купон активирован!
>
> **Fanta — 1 бутылка / банка**
> Покажи этот экран кассиру и назови акцию **«Free Taste»**.
>
> `▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌`
> `#FT-4827-XKQM`
>
> ⚠️ Купон одноразовый. После сканирования он будет недействителен.

---

## Flow B — User shares coupon with a friend

---

**[USER taps Поделиться с другом]**

**[BOT]**
> Кому отправляем? Напиток получит тот, кто перейдёт по ссылке первым.
>
> 👇 Скопируй ссылку и отправь другу:
> `https://t.me/FreeTasteBot?start=share_4827`
>
> Или перешли это сообщение прямо из Telegram.

---

**[Friend opens link — new user enters bot]**

**[BOT]**
> Привет! Друг отправил тебе бесплатный напиток 🎁
>
> Тебе досталась **Fanta**.
> Действует 30 дней.
>
> Нажми **Активировать**, когда будешь в магазине.

```
[ Активировать ]
```

> _(Хочешь выбрать другой напиток для себя? Участвуй в акции →)_

```
[ Получить свой купон ]
```

---

## Flow C — Reminder (bot sends at day 25)

---

**[BOT — outbound message]**
> Напоминаем! ⏳
> Твой купон на **Fanta** истекает через **5 дней** — 12 апреля.
>
> Успей забрать бесплатный напиток.

```
[ Активировать ]
```

---

## Edge Cases

---

**User tries to activate an already-used coupon:**

**[BOT]**
> Этот купон уже был использован.
> Если это ошибка — напиши нам: @FreeTasteSupport

---

**User tries to get a second coupon (same Telegram ID):**

**[BOT]**
> Ты уже участвуешь в акции! 🎉
> Твой купон на **Fanta** активен до 12 апреля.

```
[ Показать купон ]
```

---

## Notes

- **One coupon per Telegram account** — enforced by Telegram ID, no additional verification needed
- **Barcode generated at activation**, not at issuance — this is when partner is known and the redemption event is logged
- **Share link is single-use** — first person to open it claims the coupon; original user's coupon is transferred (not duplicated)
- The "Get your own coupon" prompt on the friend flow is a growth loop — friend becomes a new participant
- **Expiry: 30 days** from issuance; reminder sent at day 25
- **Partners (pilot):** Magnum, CU, Glovo
