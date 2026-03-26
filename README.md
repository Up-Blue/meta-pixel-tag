  # Meta Pixel Tag | Up Blue

  Browser-side Meta Pixel tag for Google Tag Manager that automatically maps GA4 e-commerce dataLayer events to Meta (Facebook) standard events.

  ## Installation

  1. In Google Tag Manager, go to **Templates** > **Search Gallery**
  2. Search for **Meta Pixel Tag | Up Blue**
  3. Click **Add to workspace**
  4. Create a new tag using this template

  ## Configuration

  ### Required fields

  | Field | Description |
  |-------|-------------|
  | **Meta Pixel ID** | Your Meta Pixel ID (digits only). Found in Meta Events Manager. |
  | **Event Setup** | Choose **Inherit from GA4 (E-commerce)** for automatic mapping or **Manual** for custom configuration. |

  ### Optional fields

  | Field | Description |
  |-------|-------------|
  | **Event ID** | Unique identifier for deduplication between browser Pixel and server-side Conversions API. |
  | **Disable Automatic Configuration** | Prevents Meta from auto-scraping page metadata (microdata, Open Graph tags, etc.). |

  ### Manual mode

  When **Event Setup** is set to **Manual**, additional fields appear:

  - **Event Type** — Choose **Standard** (select from predefined Meta events) or **Custom** (enter a custom event name).
  - **Object Properties** — Key-value table for custom data parameters sent with the event.

  ## Supported event mappings (automatic mode)

  When using **Inherit from GA4 (E-commerce)**, the tag automatically maps GA4 events to Meta standard events:

  | GA4 Event | Meta Standard Event |
  |-----------|---------------------|
  | `page_view` | PageView |
  | `add_payment_info` | AddPaymentInfo |
  | `add_to_cart` | AddToCart |
  | `add_to_wishlist` | AddToWishlist |
  | `sign_up` | CompleteRegistration |
  | `begin_checkout` | InitiateCheckout |
  | `generate_lead` | Lead |
  | `purchase` | Purchase |
  | `search` | Search |
  | `view_item` | ViewContent |
  | `contact` | Contact |
  | `customize_product` | CustomizeProduct |
  | `donate` | Donate |
  | `find_location` | FindLocation |
  | `schedule` | Schedule |
  | `start_trial` | StartTrial |
  | `submit_application` | SubmitApplication |
  | `subscribe` | Subscribe |

  GTM4WP (WooCommerce) events are also supported and mapped to their corresponding Meta events.

  ### Events skipped in automatic mode

  The following events are silently skipped (no Meta event is fired):

  - **Always skipped:** `gtm.js`, `gtm.dom`, `gtm.load`, `user_engagement`, `scroll`, `form_start`, `form_submit`, `first_visit`, `session_start`, `click`
  - **Skipped in auto mode only:** `view_item_list`, `select_item`, `select_promotion`, `view_promotion`, `view_cart`, `remove_from_cart`, `add_shipping_info`, `refund`

  To track any of these events, create a separate tag instance using **Manual** mode.

  ## E-commerce data

  In automatic mode, the tag extracts e-commerce data from the GA4 dataLayer format:

  - **Content IDs** — extracted from `items[].item_id`, automatically deduplicated
  - **Content Name** — from `items[].item_name`
  - **Content Category** — from `items[].item_category`
  - **Value** and **Currency** — from event-level `value` and `currency` fields
  - **Num Items** — populated for `InitiateCheckout` and `Purchase` events only

  ## Deduplication with server-side Conversions API

  If you also send events via the Meta Conversions API (server-side), use the **Event ID** field to pass a unique identifier. Meta uses this ID to deduplicate browser and server events automatically.

  ## License

  Apache License 2.0 — see [LICENSE](LICENSE) for details.

  ## Author

  Built and maintained by [Up Blue](https://www.upblue.pl/).
