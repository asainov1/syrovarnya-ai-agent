# Restaurant AI Agent

AI-powered restaurant assistant built with **n8n** workflow automation — handles reservations, orders, menu management, and CRM integration via Telegram.

## Features

- **Table Reservations** — check availability, create/confirm/cancel bookings
- **Order Management** — cart system, menu browsing, order placement with payment links
- **Menu System** — PDF menus (breakfast/adult/kids) in multiple languages (RU/KZ/EN)
- **CRM Integration** — customer search, creation, deduplication by phone number
- **Access Control** — whitelist-based Telegram user authorization

## Architecture

```
┌──────────────┐     ┌──────────────────┐     ┌─────────────┐
│   Telegram    │────▶│   n8n Workflow    │────▶│  Restaurant │
│    Client     │◀────│   (AI Agent)      │◀────│   CRM API   │
└──────────────┘     └──────────────────┘     └─────────────┘
                            │
                     ┌──────┴──────┐
                     │  OpenRouter  │
                     │    (LLM)    │
                     └─────────────┘
```

## Workflow Components

| Component | Purpose |
|-----------|---------|
| **Telegram Trigger** | Receives user messages |
| **AI Agent** | LLM-powered intent recognition and response |
| **CRM Tools** | Customer management, reservations, orders |
| **Menu Service** | PDF generation and delivery |
| **Payment Integration** | Order checkout with payment links |

## Supported Actions

### Reservations
- Check table availability by date, time, and guest count
- Suggest alternative time slots when unavailable
- Create, confirm, and cancel reservations

### Orders
- Browse menu by category (appetizers, mains, desserts, beverages, etc.)
- Add/remove items from cart with quantity management
- Place orders with automatic payment link generation

### Customer Management
- Search customers by phone or name
- Auto-deduplication to prevent duplicate profiles
- Phone number normalization (any format accepted)

## Tech Stack

- **Orchestration**: n8n (workflow automation)
- **LLM**: OpenRouter
- **Interface**: Telegram Bot API
- **Backend**: Custom REST API (CRM)
- **Database**: PostgreSQL

## License

MIT
