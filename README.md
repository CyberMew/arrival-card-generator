# arrival-card-generator
Basically this tries to be the standalone version of https://www.singlewindow.sh.cn/hj/arrval, because that submits your data to their backend which might seems suspicious, and it is unknown to me if this is a legit site or not.


# Arrival Card QR Decoder & Editor

This project is a web-based tool for decoding, editing, and generating QR codes for arrival card information. It allows users to input encrypted Base64 strings, decode them into a form, edit the data, and re-encode it into a QR code.

## Features

- **Decode Base64 Strings**: Users can paste an encrypted Base64 string to decode and populate the form fields.
- **Edit Form Data**: The form allows users to edit personal, travel, and contact information.
- **Generate QR Code**: After editing, the data can be re-encoded into a Base64 string and displayed as a QR code.
- **Multi-language Support**: The form supports multiple languages, including English, Japanese, Korean, Russian, French, and Spanish.
- **Dynamic Field Visibility**: Certain fields, such as Visa Number, are dynamically shown or hidden based on user input.
- **Validation**: The form includes validation for required fields and proper formatting.
- **No Data Submission**: All operations are performed locally in the browser. No data is sent to any server, ensuring privacy and security.

## Access the Tool

You can access the tool online at:  
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

## How to Use

1. **Decode Data**:
   - Paste an encrypted Base64 string into the "Paste Encrypted Base64 String" textarea.
   - Click the "🔓 Decode & Fill Form" button to populate the form.

2. **Edit Data**:
   - Update the form fields as needed. Required fields are marked with a red asterisk (*).

3. **Generate QR Code**:
   - Click the "🔐 Encode to Base64 + QR" button to encode the data and generate a QR code.

4. **Change Language**:
   - Use the language selector at the top of the form to switch between supported languages.

## Notes

- This project has **not been tested yet** to confirm if it works as intended. Please proceed with caution.
- Feel free to inspect the code and suggest or implement improvements. Contributions are welcome!
- **Disclaimer**: This tool is provided as-is, and no one is responsible if it does not work as expected or causes any issues. Use it at your own risk.
- **Privacy**: The tool does not submit any data to a server. All operations are performed locally in your browser, ensuring your data remains private.

## Dependencies

- **CryptoJS**: Used for AES encryption and decryption.
- **QRCode.js**: Used for generating QR codes.

## Multi-language Support

The form supports the following languages:
- English
- Japanese
- Korean
- Russian
- French
- Spanish

Translations are managed using a `translations` object in the JavaScript code. Labels are dynamically updated based on the selected language.

## License

This project is open-source and can be modified or distributed as needed.
