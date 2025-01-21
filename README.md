# 🔢 [Invoice Number Generator](https://format.im/)

A professional online tool for generating invoice numbers, built with pure HTML, CSS, and JavaScript. Perfect for businesses, developers, and accounting software integration.

![Invoice Number Generator](https://raw.githubusercontent.com/SoraWebui/format.im/refs/heads/main/format.png)

## 🌟 Features

- Multiple numbering formats (Sequential, Date-based, Client-based)
- Excel/Google Sheets compatible
- Custom prefix and suffix support
- Bulk generation capability
- No registration required
- Free to use

## 🚀 Live Demo

Try it now: [https://format.im/](https://format.im/)

## 📝 Invoice Number Formats

### Basic Format Structure
```
[PREFIX]-[MAIN_NUMBER]-[SUFFIX]
```

### Invoice Number Supported Formats

1. **Sequential Numbers**
   ```
   INV-0001
   INV-0002
   INV-0003
   ```

2. **Date-Based**
   ```
   20240121-001
   20240121-002
   INV/2024/001
   ```

3. **Client/Project Based**
   ```
   CLI001-INV-001
   PRJ001-INV-001
   ```

4. **Financial Year**
   ```
   FY24-0001
   FY24-0002
   ```

## 💡 Implementation Guide

### JavaScript Implementation

```javascript
function generateInvoiceNumber(format, counter, options = {}) {
    const {
        prefix = 'INV',
        suffix = '',
        padding = 4,
        separator = '-'
    } = options;

    const date = new Date();
    const year = date.getFullYear();
    const month = String(date.getMonth() + 1).padStart(2, '0');
    const day = String(date.getDate()).padStart(2, '0');

    const number = String(counter).padStart(padding, '0');

    switch (format) {
        case 'sequential':
            return `${prefix}${separator}${number}${suffix ? separator + suffix : ''}`;
        case 'date':
            return `${year}${month}${day}${separator}${number}`;
        case 'fiscal':
            return `FY${year.toString().slice(-2)}${separator}${number}`;
        default:
            return `${prefix}${separator}${number}`;
    }
}
```

### Python Implementation

```python
from datetime import datetime

def generate_invoice_number(format_type, counter, **options):
    prefix = options.get('prefix', 'INV')
    suffix = options.get('suffix', '')
    padding = options.get('padding', 4)
    separator = options.get('separator', '-')

    now = datetime.now()
    number = str(counter).zfill(padding)

    formats = {
        'sequential': f"{prefix}{separator}{number}{separator + suffix if suffix else ''}",
        'date': f"{now.strftime('%Y%m%d')}{separator}{number}",
        'fiscal': f"FY{str(now.year)[2:]}{separator}{number}"
    }

    return formats.get(format_type, formats['sequential'])
```

## 🔍 Best Practices

1. **Uniqueness**
   - Never reuse invoice numbers
   - Use sufficiently large padding (e.g., 4 digits minimum)
   - Consider adding business unit identifiers for multiple departments

2. **Consistency**
   - Maintain consistent format throughout the fiscal year
   - Use clear separators between components
   - Keep a logical sequence

3. **Readability**
   - Avoid ambiguous characters (I, l, O, 0)
   - Use meaningful prefixes
   - Limit total length to 15-20 characters

4. **Compliance**
   - Follow local tax regulations
   - Include year/date information when required
   - Maintain proper audit trails

## 💻 Technical Details

### Features Implementation

- Pure HTML/CSS/JavaScript
- No external dependencies
- Cross-browser compatible
- Mobile responsive
- Clipboard API integration


## 🤝 Contributing

Contributions are welcome! Feel free to submit issues and enhancement requests.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📜 License

This project is licensed under the MIT License .

## 🙏 Acknowledgments

- Inspired by real-world business needs
- Built with modern web standards
- Community feedback and contributions

## 📞 Support

For support and questions, please [open an issue](https://github.com/SoraWebui/format.im/issues) or contact us at support@format.im.

---

⭐ Don't forget to star this repo if you find it useful!
