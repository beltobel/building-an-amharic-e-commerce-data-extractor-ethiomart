# building-an-amharic-e-commerce-data-extractor-ethiomart

## Telegram Data Ingestion

The [`scripts/telegram_data_ingestion.ipynb`](scripts/telegram_data_ingestion.ipynb) notebook implements the pipeline for extracting, normalizing, and preprocessing Amharic e-commerce data from Telegram channels. The main steps include:

- **Configuration:** Set up Telegram API credentials and define the list of e-commerce channels to crawl.
- **Telegram Client Initialization:** Uses the Telethon library to connect and authenticate with Telegram.
- **Message Fetching:** Asynchronously fetches messages (including text, images, and documents) from each specified channel.
- **Media Download:** Downloads images and documents attached to messages, saving them in the appropriate `data/images` and `data/documents` directories.
- **Text Normalization:** Normalizes Amharic text to handle linguistic variations and standardizes punctuation.
- **Tokenization:** Tokenizes normalized Amharic text for further processing.
- **Preprocessing:** Each message is processed to include normalized text and tokens.
- **Data Storage:** Saves the processed messages as both CSV and JSON files in `data/processed/`.

---

## Task 2: Label a Subset of Dataset in CoNLL Format

labeling a portion of the dataset in the CoNLL format, commonly used for Named Entity Recognition (NER) tasks. The goal is to identify and label entities such as products, prices, and locations in Amharic text from the "Message" column.

**CoNLL Format Guidelines:**

- Each token (word) is labeled on its own line, followed by its entity label.
- Blank lines separate individual messages.
- Entity Types:
  - `B-Product`: Beginning of a product entity (e.g., "Baby bottle").
  - `I-Product`: Inside a product entity.
  - `B-LOC`: Beginning of a location entity (e.g., "Addis abeba").
  - `I-LOC`: Inside a location entity.
  - `B-PRICE`: Beginning of a price entity (e.g., "ዋጋ 1000 ብር").
  - `I-PRICE`: Inside a price entity.
  - `O`: Tokens outside any entities.
