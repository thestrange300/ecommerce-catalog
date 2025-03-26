# E-Commerce Catalog

## 📌 Project Overview
This project is a simple **E-Commerce Product Catalog** built using **VueJS**. The application fetches product data from the [FakeStoreAPI](https://fakestoreapi.com/) and displays different product categories dynamically. Users can navigate through products using a "Next Product" button.

## 🚀 Features
- Fetch and display products from **FakeStoreAPI**
- Categorize products into **Men's Clothing**, **Women's Clothing**, and **Unavailable Product**
- Implement a **Next Product** button to cycle through products
- Add a **loading spinner/skeleton** while fetching data
- Responsive UI based on **Figma design**
- Styled using **Vanilla CSS**

## 🛠️ Technologies Used
- **VueJS** (Frontend framework)
- **FakeStoreAPI** (Product data source)
- **Vanilla CSS** (Custom styling without frameworks)

## 🎨 UI Design
The application has three different UI layouts based on the product category:
1. **Men's Clothing** - Styled for male-oriented products
2. **Women's Clothing** - Styled for female-oriented products
3. **Unavailable Product** - Placeholder for products outside these categories

## 📂 Project Structure
```
├── src
│   ├── components
│   │   ├── ProductCard.vue  # Component to display product details
│   ├── views
│   │   ├── Home.vue         # Main view displaying products
│   ├── assets               # Images, icons, styles
│   ├── App.vue              # Root component
│   ├── main.js              # Vue app entry point
├── public
├── README.md
├── package.json
└── .gitignore
```

## 🔄 API Integration
### API Endpoint Used:
```plaintext
https://fakestoreapi.com/products/{index}
```
- `{index}` is a number between **1-20**.
- Clicking **Next Product** increments the index and fetches the next product.
- If `index > 20`, it resets to `1`.
- Only **Men’s Clothing** and **Women’s Clothing** products are displayed.

## 📜 Installation & Setup
1. **Clone the repository**
```bash
git clone https://github.com/thestrange300/ecommerce-catalog.git
cd ecommerce-catalog
```
2. **Install dependencies**
```bash
npm install
```
3. **Run the development server**
```bash
npm run dev
```
4. **Build for production**
```bash
npm run build
```

## 📞 Contact
For any questions, reach out via **email** or **GitHub Issues**.

---

✨ **Happy Coding!** 🚀
