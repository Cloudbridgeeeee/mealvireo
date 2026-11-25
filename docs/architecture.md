# MealVireo — proposed AWS architecture

MealVireo uses AWS to combine sales, recipes and bookings into daily forecasts and purchase lists — reliably, for every kitchen.

## Request flow

1. POS & bookings
2. Amazon S3
3. AWS Lambda
4. SageMaker AI
5. DynamoDB
6. Chef approval
7. Bedrock summary

## Services

### Amazon SageMaker AI

**Role:** Forecast covers and dish sales

Trains per-kitchen models on sales history, bookings, weather and calendar effects to forecast covers and dish sales by service.

### Amazon S3

**Role:** Store sales and recipes

Keeps POS exports, recipe files and waste logs encrypted as the history every forecast is trained and audited against.

### Amazon DynamoDB

**Role:** Hold requirements and stock

Stores ingredients, recipes, stock levels, forecasts and approved purchase lists for fast access during busy service.

### AWS Lambda

**Role:** Convert dishes to ingredients

Explodes forecast dishes into ingredient requirements using recipes, deducts stock on hand and rounds to supplier pack sizes.

### Amazon Bedrock

**Role:** Summarise the week

Drafts a weekly purchasing and waste summary in plain language for the head chef and managers to edit and share.

## Principles

- **Chefs decide** — Purchase lists are proposals until a chef approves.
- **Recipes are truth** — Requirements follow your recipes and portions.
- **Kitchen data private** — Recipes and costs stay with your business.

## Safeguards

- **Chef approval** — MealVireo recommends; the chef approves every purchase list.
- **Food safety unchanged** — Storage, hygiene and allergen controls remain with your food safety system.
- **Explained quantities** — Every quantity shows the forecast dishes and recipes behind it.
- **Recipes protected** — Your recipes and costs are encrypted and private.

## MVP scope

For one or two kitchens, we import your sales history and recipes, add upcoming bookings, and deliver daily ingredient forecasts and draft purchase lists your chef reviews.

- POS sales import
- Recipe and portion setup
- Daily ingredient forecasts
- Draft purchase lists
- Weekly waste report
