# 🌐 CryptoView Web

A modern, cyberpunk-styled cryptocurrency exchange viewer built with pure HTML5, CSS3, and JavaScript. This web version mirrors the functionality of the desktop WPF application, providing real-time cryptocurrency trading data from various exchanges.

![CryptoView Web Screenshot](https://img.shields.io/badge/Status-Active-brightgreen)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)

## ✨ Features

### 🎨 **Visual Design**
- **Cyberpunk aesthetic** with neon colors and glowing effects
- **Futuristic UI** with custom-styled controls and animations
- **Responsive design** that adapts to desktop, tablet, and mobile devices
- **Dark theme** optimized for extended viewing sessions

### 🔧 **Core Functionality**
- **Persistent State Management**: localStorage-based persistence keeps your loaded exchanges across page refreshes
- **Smart Exchange Filtering**: Automatically filters and displays only exchanges with valid trading data
- **Real-time Progress Tracking**: Visual progress bar shows filtering progress with live updates
- **Trading Pair Display**: Clean table view of BASE/QUOTE pairs with pricing and volume data
- **Exchange Information**: Detailed exchange metadata including founding date and website
- **Error Handling**: Comprehensive error messages and validation
- **Status Updates**: Real-time status information and loading indicators
- **Intelligent Caching**: 7-day cache expiration with automatic fallback to defaults

### 📊 **Data Features**
- **Multiple Data Formats**: Supports both array and object-based API responses
- **Price Display**: USD pricing with proper decimal formatting
- **Volume Information**: Trading volume with number formatting
- **Timestamp Handling**: Automatic time formatting with fallback to current time
- **Data Validation**: Robust parsing with error recovery

## 🚀 Quick Start

### Option 1: Direct File Access
1. **Download** the `index.html` file
2. **Open** it in any modern web browser
3. **Wait** for the exchange filtering to complete
4. **Select** an exchange from the dropdown
5. **Click** "LOAD DATA" to view trading pairs

### Option 2: Local Web Server (Recommended)
```bash
# Using Python 3
python -m http.server 8000

# Using Node.js
npx http-server

# Using PHP
php -S localhost:8000
```

Then navigate to `http://localhost:8000` in your browser.

## 🖥️ Browser Compatibility

| Browser | Version | Status |
|---------|---------|--------|
| Chrome | 80+ | ✅ Fully Supported |
| Firefox | 75+ | ✅ Fully Supported |
| Safari | 13+ | ✅ Fully Supported |
| Edge | 80+ | ✅ Fully Supported |

**Requirements:**
- Modern browser with ES6+ support
- JavaScript enabled
- Internet connection for API access

## 📱 Mobile Support

The application is fully responsive and optimized for mobile devices:

- **Touch-friendly controls** with appropriate sizing
- **Responsive layout** that adapts to screen size
- **Optimized table view** for mobile viewing
- **Swipe-friendly** interface elements

## 🔧 Technical Details

### **Architecture**
- **Pure JavaScript ES6+** with classes and async/await
- **No external dependencies** except Google Fonts
- **Modular design** with clear separation of concerns
- **Event-driven architecture** for UI interactions

### **API Integration**
- **CoinLore API** for exchange and trading data
- **CORS-compatible** fetch requests
- **5-second timeout** for exchange validation
- **Error handling** with retry logic

### **Performance**
- **Lazy loading** of exchange data
- **Efficient DOM manipulation** with minimal reflows
- **Progress tracking** to keep users informed
- **Memory-conscious** data handling

## 🎯 Usage Guide

### **1. Initial Load**
When you first open the application:
- The system checks localStorage for previously loaded exchanges
- If found (and less than 7 days old), exchanges are instantly restored
- If not found, the system automatically loads a default exchange (Binance)
- Click "ADD EXCHANGES" to load all available exchanges with valid data
- Progress is shown with a visual progress bar during bulk loading
- All loaded exchanges persist across page refreshes

### **2. Selecting an Exchange**
- Choose from the filtered list of valid exchanges
- Exchanges are sorted alphabetically for easy browsing
- The "LOAD DATA" button becomes enabled once an exchange is selected
- Your selection is automatically saved and restored on page refresh
- Data for the selected exchange loads automatically when changed

### **3. Viewing Trading Data**
- Click "LOAD DATA" to fetch trading pairs
- Data is displayed in a responsive table format
- Information includes base/quote currencies, prices, volume, and timestamps
- Exchange information is shown in the status bar

### **4. Understanding the Interface**

#### Status Indicators
- **Loading spinner**: Indicates active data processing
- **Progress bar**: Shows filtering progress percentage
- **Status text**: Provides real-time operation updates
- **Message area**: Displays success/error notifications

#### Data Table Columns
- **BASE**: Base currency (e.g., BTC, ETH)
- **QUOTE**: Quote currency (e.g., USD, USDT)
- **PRICE (USD)**: Current USD price with 2 decimal places
- **VOLUME**: Trading volume with proper formatting
- **TIME**: Last update time or current time if data is stale

## 🔍 Troubleshooting

### **Common Issues**

#### **No exchanges loading**
- Check internet connection
- Verify that JavaScript is enabled
- Try refreshing the page
- Check browser console for CORS errors

#### **CORS errors**
- Use a local web server instead of file:// protocol
- Consider using a CORS proxy for production deployment
- Ensure the API endpoints are accessible

#### **Slow loading**
- The initial filtering process checks each exchange individually
- This is normal and ensures only quality data is shown
- Progress bar indicates current status

#### **Empty exchange data**
- Some exchanges may return empty or invalid data
- The filtering process automatically excludes these
- This is expected behavior to improve user experience

### **Browser Console Debugging**
Open Developer Tools (F12) and check the Console tab for detailed error messages.

## 🚧 Development

### **File Structure**
```
cryptoview-web/
├── index.html          # Main application file
├── README.md          # This documentation
└── assets/            # Optional: images, icons, etc.
```

### **Customization**

#### **Styling**
The CSS uses custom properties that can be easily modified:
```css
:root {
    --primary-color: #00FF9C;
    --secondary-color: #00FFFF;
    --background-color: #0F0F17;
    --container-bg: #1A1A2E;
}
```

#### **API Configuration**
API endpoints can be modified in the JavaScript:
```javascript
// Exchange list API
const EXCHANGES_API = 'https://api.coinlore.net/api/exchanges/';

// Individual exchange data API
const EXCHANGE_DATA_API = 'https://api.coinlore.net/api/exchange/?id=';
```

## 🛡️ Security Considerations

- **localStorage usage**: Stores exchange list and preferences locally (non-sensitive data only)
- **Auto-expiration**: Cached data expires after 7 days to prevent stale information
- **HTTPS recommended**: Use HTTPS in production for secure API calls
- **Input validation**: All API responses are validated before processing
- **Error boundaries**: Comprehensive error handling prevents crashes
- **Cache clearing**: Clearing browser data resets to default state

## 🌟 Future Enhancements

- **WebSocket support** for real-time price updates
- **Chart integration** for price history visualization
- **Favorites system** for preferred exchanges
- **Export functionality** for trading data
- **PWA support** for offline functionality
- **Dark/Light theme toggle**
- **IndexedDB migration** for larger datasets and better performance

## 📄 License

This project is open source and available under the [MIT License](LICENSE).



## 🔗 Related Projects

- **CryptoView Desktop**: WPF application version
- **CoinLore API**: Data source for cryptocurrency information

---

Made with 💚 for the cryptocurrency community
