# Convert Squarespace Profiles to Shopify Customer Rows

Upload a Squarespace profile CSV or read the existing profiles tab to prepare Shopify customer rows in Google Sheets.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/convert-squarespace-profiles-for-shopify.n8n.json)
<!-- template-actions:end -->

## Setup

1. Create the two tabs in one Google spreadsheet. Paste the relevant header line below into cell A1 and leave enough empty rows for new profiles. In **Set the spreadsheet and both tabs**, set the spreadsheet ID and both tab names.
2. Bind the same **Google Sheets OAuth2** credential in **Read both Sheets tabs** and **Write both tabs in one Sheets batch**. Give the connected account edit access to the spreadsheet.
3. Assign a **Header Auth** credential to **Receive a Squarespace CSV upload** and publish the workflow. POST a UTF-8 CSV as a single multipart file field named `file` to the production HTTPS webhook URL. Include the configured authentication header. To rebuild customer rows from the existing profiles, run **Rebuild the Shopify customer tab** instead.

### Squarespace profiles headers

```text
Email	First Name	Last Name	Created On	Order Count	Last Order Date	Total Spent	Member Since	Subscriber Since	Subscriber Source	Tags	Mailing Lists	Member Areas	Donation Count	Last Donation Date	Total Donation Amount	Has Account	Customer Since	Shipping Name	Shipping Address 1	Shipping Address 2	Shipping City	Shipping Zip	Shipping Province/State	Shipping Country	Shipping Phone Number	Billing Name	Billing Address 1	Billing Address 2	Billing City	Billing Zip	Billing Province/State	Billing Country	Billing Phone Number	Accepts Marketing
```

### Shopify customers headers

```text
First Name	Last Name	Email	Accepts Email Marketing	Default Address Company	Default Address Address1	Default Address Address2	Default Address City	Default Address Province Code	Default Address Country Code	Default Address Zip	Default Address Phone	Phone	Accepts SMS Marketing	Tags	Note	Tax Exempt
```

## Behavior

The upload updates only the emails in the CSV. The manual run regenerates the Shopify customer rows for every email in the source tab. Email matching trims outer spaces and ignores case across the entire address. Duplicate addresses within a file or tab stop the run before writing. The workflow preserves unrelated rows and existing notes, tax exemption and SMS marketing cells.

The Shopify columns use billing addresses and phone numbers. Use ISO country codes or recognized English country names. US, Canadian and Australian regions accept names or codes. For other countries, enter the Shopify subdivision code. The workflow sets email marketing to `yes` only when the profile has explicit affirmative consent in **Accepts Marketing**. Blank or missing consent is written as `no`.

Uploads accept up to 1 MiB and 1,000 profile rows. Each tab can contain up to 2,000 profile rows, subject to the Sheets request size. Keep customer/run data private and run one update at a time. Avoid editing or sorting tabs during an update. Both tabs are written together through Google Sheets when an upload changes them. If the request outcome is unknown, inspect the tabs before running again. Export the Shopify customers tab as CSV when you are ready to import it. [Shopify customer CSV fields](https://help.shopify.com/en/manual/customers/import-export-customers)

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

Authenticate uploads, validate the original CSV rows, match full email addresses across both tabs, and require explicit email marketing consent. One Google Sheets batch applies both sets of updates. [Original workflow by bangank36](https://n8n.io/workflows/3110-convert-squarespace-profiles-to-shopify-customers-in-google-sheets/).

Adapted from [Convert Squarespace Profiles to Shopify Customers in Google Sheets](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Webhook/1132_Webhook_Extractfromfile_Process_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: bangank36 (original workflow); Zie619 / n8n-workflows (collection).

The collection’s [MIT notice](https://github.com/Zie619/n8n-workflows/blob/94007c1445d9258a7da116646b79473e7c7c3282/LICENSE) is pinned at a later revision. This is the collection notice at that revision; it does not establish a separate original template author's license. Our changes are listed above; see [repository licensing](../../README.md#licensing).

> MIT License
>
> Copyright (c) 2025 Zie619
>
> Permission is hereby granted, free of charge, to any person obtaining a copy
> of this software and associated documentation files (the "Software"), to deal
> in the Software without restriction, including without limitation the rights
> to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
> copies of the Software, and to permit persons to whom the Software is
> furnished to do so, subject to the following conditions:
>
> The above copyright notice and this permission notice shall be included in all
> copies or substantial portions of the Software.
>
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
> IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
> FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
> AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
> LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
> OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
> SOFTWARE.

</details>
