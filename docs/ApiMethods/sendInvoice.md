# sendInvoice

Use this method to send invoices. On success, the sent Message is returned.

**Parameters:**

| Parameter                               | Description                                                                                                                                                                                                                                                                                                                                                                                           |
| --------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| `options.chat_id`                       | Unique identifier for the target chat or username of the target channel (in the format @channelusername).**Type:** `number                                                                                                                                                                                                                                                                            | string` |
| `options.message_thread_id`             | Unique identifier for the target message thread (topic) of the forum; for forum supergroups only.**Type:** `number`                                                                                                                                                                                                                                                                                   |
| `options.title`                         | Product name, 1-32 characters.**Type:** `string`                                                                                                                                                                                                                                                                                                                                                      |
| `options.description`                   | Product description, 1-255 characters.**Type:** `string`                                                                                                                                                                                                                                                                                                                                              |
| `options.payload`                       | Bot-defined invoice payload, 1-128 bytes. This will not be displayed to the user, use for your internal processes.**Type:** `string`                                                                                                                                                                                                                                                                  |
| `options.provider_token`                | Payment provider token, obtained via @BotFather.**Type:** `string`                                                                                                                                                                                                                                                                                                                                    |
| `options.currency`                      | Three-letter ISO 4217 currency code, see more on currencies.**Type:** `string`                                                                                                                                                                                                                                                                                                                        |
| `options.prices`                        | Price breakdown, a list of components (e.g., product price, tax, discount, delivery cost, delivery tax, bonus, etc.).**Type:** `readonly LabeledPrice[]`                                                                                                                                                                                                                                              |
| `options.max_tip_amount`                | The maximum accepted amount for tips in the smallest units of the currency (integer, not float/double). For example, for a maximum tip of US$ 1.45 pass max_tip_amount = 145. See the exp parameter in currencies.json, it shows the number of digits past the decimal point for each currency (2 for the majority of currencies). Defaults to 0.**Type:** `number`                                   |
| `options.suggested_tip_amounts`         | An array of suggested amounts of tips in the smallest units of the currency (integer, not float/double). At most 4 suggested tip amounts can be specified. The suggested tip amounts must be positive, passed in a strictly increased order and must not exceed max_tip_amount.**Type:** `number[]`                                                                                                   |
| `options.start_parameter`               | Unique deep-linking parameter. If left empty, forwarded copies of the sent message will have a Pay button, allowing multiple users to pay directly from the forwarded message, using the same invoice. If non-empty, forwarded copies of the sent message will have a URL button with a deep link to the bot (instead of a Pay button), with the value used as the start parameter.**Type:** `string` |
| `options.provider_data`                 | Data about the invoice, which will be shared with the payment provider. A detailed description of required fields should be provided by the payment provider.**Type:** `string`                                                                                                                                                                                                                       |
| `options.photo_url`                     | URL of the product photo for the invoice. Can be a photo of the goods or a marketing image for a service. People like it better when they see what they are paying for.**Type:** `string`                                                                                                                                                                                                             |
| `options.photo_size`                    | Photo size in bytes.**Type:** `number`                                                                                                                                                                                                                                                                                                                                                                |
| `options.photo_width`                   | Photo width.**Type:** `number`                                                                                                                                                                                                                                                                                                                                                                        |
| `options.photo_height`                  | Photo height.**Type:** `number`                                                                                                                                                                                                                                                                                                                                                                       |
| `options.need_name`                     | Pass True if you require the user's full name to complete the order.**Type:** `boolean`                                                                                                                                                                                                                                                                                                               |
| `options.need_phone_number`             | Pass True if you require the user's phone number to complete the order.**Type:** `boolean`                                                                                                                                                                                                                                                                                                            |
| `options.need_email`                    | Pass True if you require the user's email address to complete the order.**Type:** `boolean`                                                                                                                                                                                                                                                                                                           |
| `options.need_shipping_address`         | Pass True if you require the user's shipping address to complete the order.**Type:** `boolean`                                                                                                                                                                                                                                                                                                        |
| `options.send_phone_number_to_provider` | Pass True if the user's phone number should be sent to the provider.**Type:** `boolean`                                                                                                                                                                                                                                                                                                               |
| `options.send_email_to_provider`        | Pass True if the user's email address should be sent to the provider.**Type:** `boolean`                                                                                                                                                                                                                                                                                                              |
| `options.is_flexible`                   | Pass True if the final price depends on the shipping method.**Type:** `boolean`                                                                                                                                                                                                                                                                                                                       |
| `options.disable_notification`          | Sends the message silently. Users will receive a notification with no sound.**Type:** `boolean`                                                                                                                                                                                                                                                                                                       |
| `options.protect_content`               | Protects the contents of the sent message from forwarding and saving.**Type:** `boolean`                                                                                                                                                                                                                                                                                                              |
| `options.reply_to_message_id`           | If the message is a reply, ID of the original message.**Type:** `number`                                                                                                                                                                                                                                                                                                                              |
| `options.allow_sending_without_reply`   | Pass True if the message should be sent even if the specified replied-to message is not found.**Type:** `boolean`                                                                                                                                                                                                                                                                                     |
| `options.reply_markup`                  | An object for an inline keyboard. If empty, one 'Pay total price' button will be shown. If not empty, the first button must be a Pay button.**Type:** `InlineKeyboardMarkup`                                                                                                                                                                                                                          |

**Return Type:**

[Message.InvoiceMessage](https://core.telegram.org/bots/api#invoice)

**Example:**

```javascript
const { TelegramBot } = require("telegramsjs");

const bot = new TelegramBot("BOT_TOKEN");

const invoiceTitle = "Example Invoice";
const invoiceDescription = "This is an example invoice";
const invoicePayload = "example_payload";
const providerToken = "YOUR_PROVIDER_TOKEN";
const currency = "USD";
const prices = [{ label: "Product Price", amount: 1000 }];

bot.sendInvoice({
  chat_id: CHAT_ID,
  title: invoiceTitle,
  description: invoiceDescription,
  payload: invoicePayload,
  provider_token: providerToken,
  currency: currency,
  prices: prices,
});

bot.login();
```