# arrival-card-generator

Basically this tries to be the standalone version of https://www.singlewindow.sh.cn/hj/arrval, because that website submits your data to their backend which might seem suspicious, and it is unknown to me if this is a legit official site or not.

# Arrival Card QR Decoder & Editor

This project is a web-based tool for decoding, editing, and generating QR codes for arrival card information. It allows users to input encrypted Base64 strings, decode them into a form, edit the data, and re-encode it into a QR code.

You can download the HTML file, open it in Chrome, and it should run locally. All codes are created using Copilot.

### Disclaimer

This tool is **not an official arrival form** and is not affiliated with any government or immigration authority. It is a standalone utility designed to help users decode, edit, and generate QR codes for arrival card information. 

Please ensure that you verify the accuracy of the information and consult official sources or authorities for any official requirements.

## Features

- **Decode Base64 Strings**: Users can paste an encrypted Base64 string to decode and populate the form fields.
- **Edit Form Data**: The form allows users to edit personal, travel, and contact information.
- **Generate QR Code**: After editing, the data can be re-encoded into a Base64 string and displayed as a QR code.
- **Multi-language Support**: The form supports multiple languages, including English, Japanese, Korean, Russian, French, and Spanish.
- **Dynamic Field Visibility**: Certain fields, such as Visa Number, are dynamically shown or hidden based on user input.
- **Validation**: The form includes validation for required fields and proper formatting.
- **No Data Submission**: All operations are performed locally in the browser. No data is sent to any server, ensuring privacy and security.

## Access the Tool

You can access the tool/form online at:  
[https://cybermew.github.io/arrival-card-generator](https://cybermew.github.io/arrival-card-generator)

## File Structure

### HTML
- The form is divided into sections:
  - **Personal Information**: Includes fields like surname, given names, gender, nationality, and date of birth.
  - **Travel Document Information**: Includes passport number and visa-related fields.
  - **Departure Information**: Includes departure ticket status, date, and flight/train/ship details.
  - **Arrival Information**: Includes arrival flight details, cities to visit, and residence information.
  - **Purpose of Trip**: Allows users to select the purpose of their trip.
  - **Contact in China**: Includes fields for contact details in China.
  - **Travel History**: Allows users to list countries visited in the past two years.

### JavaScript
- **Decoding and Filling Form**: The `decodeAndFill` function decrypts the Base64 string and populates the form fields.
- **Encoding and QR Code Generation**: The `encodeAndGenerateQR` function collects form data, encrypts it, and generates a QR code.
- **Dynamic Field Handling**: Functions like `toggleConditional` and `toggleVisaNo` handle the visibility of conditional fields.
- **Language Support**: The `setLanguage` function updates the form labels based on the selected language.

### CSS
- Styles are included for form layout, validation, and dynamic effects like highlighting updated fields.

## Usage

1. **Decode Data**:
   - Paste an encrypted Base64 string into the "Paste Encrypted Base64 String" textarea.
   - Click the "🔓 Decode & Fill Form" button to populate the form.

2. **Edit Data**:
   - Update the form fields as needed. Required fields are marked with a red asterisk (*).

3. **Generate QR Code**:
   - Click the "🔐 Encode to Base64 + QR" button to encode the data and generate a QR code.

4. **Change Language**:
   - Use the language selector at the top of the form to switch between supported languages.

## Input Keys and Their Meanings

Below is a list of the input keys used in the form, along with their Hanyu Pinyin, Chinese words, and English meanings:

| **Key**   | **Hanyu Pinyin**       | **Chinese Word**       | **English Meaning**                     |
|-----------|------------------------|------------------------|-----------------------------------------|
| `x`       | **Xìng**               | 姓                    | Surname                                 |
| `m`       | **Míng**               | 名                    | Given Name                              |
| `xb`      | **Xìng Bié**           | 性别                  | Gender/Sex — value is the string `Male` or `Female` |
| `zwxm`    | **Zhōng Wén Xìng Míng**| 中文姓名              | Chinese Name                            |
| `gj`      | **Guó Jí**             | 国籍                  | Nationality                             |
| `csrq`    | **Chū Shēng Rì Qī**    | 出生日期              | Date of Birth                           |
| `lxzjhm`  | **Lǚ Xíng Zhèng Jiàn Hào Mǎ** | 旅行证件号码 | Passport/Travel Document Number         |
| `qzhm`    | **Qiān Zhèng Hào Mǎ**  | 签证号码              | Visa Number                             |
| `ddhb`    | **Dǐ Dá Háng Bān**     | 抵达航班              | Arrival Flight                          |
| `brdhhm`  | **Běn Rén Diàn Huà Hào Mǎ** | 本人电话号码      | Personal Phone Number                   |
| `zhjt`    | **Zài Huá Jīng Tíng**  | 在华经停              | Cities Intended to Visit in China       |
| `zhzz`    | **Zài Huá Zhù Zhǐ**    | 在华住址              | Detailed Address or Hotel Name in China |
| `zhzzcs`  | **Zài Huá Zhù Zhǐ Chéng Shì** | 在华住址城市    | City in China                           |
| `rjsy`    | **Rù Jìng Shì Yóu**    | 入境事由              | Purpose of Entry — value is one of the Chinese labels: `外交/公务`, `访问/商务`, `定居`, `工作`, `学习`, `旅游`, `探亲`, `过境`, `其他` |
| `cjsj`    | **Chū Jìng Shí Jiān**  | 出境时间              | Date of Departure                       |
| `cjhb`    | **Chū Jìng Háng Bān**  | 出境航班              | Departure Flight/Train/Ship Number      |
| `yqrmc`   | **Yāo Qǐng Rén Míng Chēng** | 邀请人名称        | Name of Inviter/Reception Unit          |
| `yqrlxfs` | **Yāo Qǐng Rén Lián Xì Fāng Shì** | 邀请人联系方式 | Contact Information of Inviter          |
| `cqgj`    | **Céng Qù Guó Jiā**    | 曾去国家              | Countries Visited                       |
| `lb`      | **Lèi Bié**            | 类别                  | Category — constant `1` for the arrival card |
| `t`       | **Shí Jiān Cuò**       | 时间戳                | Timestamp (epoch milliseconds)          |
| `check1`  | —                      | 免签                  | Visa-Free flag: `1` = Yes (visa-free), `0` = No. When `1`, `qzhm` is blank |
| `check2`  | —                      | 是否预订离境票        | Departure ticket booked: `1` = Yes, `0` = No. When `0`, `cjsj`/`cjhb` are blank |
| `check3`  | —                      | 是否有中国联系人      | Has contact/inviter in China: `1` = Yes, `0` = No |

> All `check*` values and `lb` are JSON **numbers** (not strings). Dates (`csrq`, `cjsj`) use `YYYY-MM-DD`. The encrypted payload preserves this exact key order: `x, m, xb, gj, csrq, zwxm, lxzjhm, check1, qzhm, ddhb, brdhhm, zhjt, zhzz, zhzzcs, rjsy, check2, cjsj, cjhb, check3, yqrmc, yqrlxfs, cqgj, lb, t`.

## Verification Against the Official Site

These findings come from reverse-engineering the live `singlewindow.sh.cn/hj/arrval` site and decoding a handful of controlled test submissions. The backend is closed-source, so the server-side observations below describe **only the cases we tested** — they are not guarantees, and untested inputs or combinations could behave differently.

- **Encryption is byte-identical.** The official site uses CryptoJS `AES.encrypt(JSON.stringify(data), key, {iv, mode: CBC, padding: Pkcs7})` with key `sdgdfjytyjkueesh` and IV `fhgtdytestgrjrtd` (both 16-byte UTF-8 → AES-128). This tool's native Web Crypto output produced the same Base64 string for the same input in our tests. (AES-CBC is deterministic for a fixed key/IV, so this should hold generally.)
- **Payload structure matches.** Decrypting real submissions confirmed the exact field names, key order, value formats (`xb` = `Male`/`Female`, `rjsy` = Chinese label, dates = `YYYY-MM-DD`, `check*`/`lb` = numbers), and the official site's conditional blanking (`qzhm` empty when visa-free; `cjsj`/`cjhb` empty when no departure ticket). Note the official site does **not** blank the contact fields (`yqrmc`/`yqrlxfs`) even when "No contact" is selected; this tool blanks them on purpose for consistency.
- **The QR encoded the submitted string verbatim, in every case we tried.** On the official site, the form POSTs `{data: <encrypted>}` to `/qrCode/generate`, which returns a server-rendered QR **PNG**. In our tests the PNG decoded back to exactly the string we sent — including arbitrary non-ciphertext (e.g. `hello world`), which the server still rendered as-is. This is consistent with the server acting as a pass-through QR-image renderer that does not decrypt or validate the payload, but we cannot rule out untested edge cases. Because the QR content appears to equal the submitted string, generating the QR locally (as this tool does) should yield an identical QR.
- **Client-side validation is presence-only.** The official form's client-side rules enforce only *required* checks — we found **no character-set (e.g. ASCII/Cyrillic) or length restrictions** in the form bundle. Any such rules would be applied server-side / at the border, which we did not test. The form hint asks you to "complete clearly in Chinese or English."

### Tests we ran

Each test below was a real submission on the official site; we then **decoded the resulting QR image** (not just the request) and decrypted it to see exactly what it contained:

1. **Standard entry** (visa-free, no departure ticket, no contact) → the QR decoded back to exactly our submitted data; no changes by the server.
2. **Visa number entered, then switched to "Visa-Free = Yes"** → the visa number was dropped (`qzhm` empty) in the final QR.
3. **Departure date/flight entered, then switched to "ticket booked = No"** → both were dropped (`cjsj`/`cjhb` empty) in the final QR.
4. **Contact name/address entered, then switched to "no contact in China"** → the official site **still included them** in the QR. (This tool deliberately blanks them instead — see above.)
5. **Arbitrary non-encrypted strings** (e.g. `hello world`, raw JSON, special characters) sent to the QR endpoint → each came back as a QR of that exact text. In the cases we tried, the server rendered whatever string it was given without decrypting or validating it.

These are the specific cases we checked — they cover the conditional fields and the question of server-side tampering, but they are not exhaustive.

## Notes

- Output matched the official site in the test cases we tried (see above) — this is **not a guarantee** of correctness for all inputs. **Use at your own risk** and always confirm details against official sources.
- Feel free to inspect the code and suggest or implement improvements. Contributions are welcome!
- **Disclaimer**: This tool is provided as-is, and no one is responsible if it does not work as expected or causes any issues. Use it at your own risk.
- **Privacy**: The tool does not submit any data to a server. All operations are performed locally in your browser, ensuring your data remains private.

## Dependencies

- ~**CryptoJS**: Used for AES encryption and decryption.~ - This is now done natively in browser.
- **QRCode.js**: Used for generating QR codes. Feel free to remove the script (since it is 3rd party dependency) and copy the generated Base64 string elsewhere to generate the QR code.

## Multi-language Support

The form currently supports the following languages:
- English
- Japanese
- Korean
- Russian
- French
- Spanish

Translations are managed using a `translations` object in the JavaScript code. Labels are dynamically updated based on the selected language.

## License

This project is open-source and can be modified or distributed as needed.
