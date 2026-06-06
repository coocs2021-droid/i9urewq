<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VERTEX | متجر عبدالرحمن الهلالي</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght=400;500;700;900&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>

    <style>
        /* الهوية البصرية: عنابي فخم مع أسود ملكي */
        :root {
            --burgundy-main: #800020;   
            --burgundy-dark: #4a0012;   
            --burgundy-light: #f5e6e8;  
            --dark-black: #121212;      
            --light-bg: #fafafa;
            --white: #ffffff;
            --border-color: #e5e5e5;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Tajawal', sans-serif;
            transition: all 0.2s ease;
        }

        body {
            background-color: var(--light-bg);
            color: var(--dark-black);
            overflow-x: hidden;
        }

        header {
            background-color: var(--dark-black);
            color: var(--white);
            padding: 15px 5%;
            position: sticky;
            top: 0;
            z-index: 1000;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 3px solid var(--burgundy-main);
        }

        .logo-vertex {
            font-size: 32px;
            font-weight: 900;
            letter-spacing: 2px;
            color: var(--burgundy-main);
            text-shadow: 1px 1px 0px rgba(255,255,255,0.1);
            text-transform: uppercase;
            font-family: 'Arial Black', sans-serif;
            cursor: pointer;
        }

        .header-user-badge {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .cart-icon-container {
            position: relative;
            cursor: pointer;
        }

        .cart-icon-container i {
            font-size: 26px;
            color: var(--burgundy-main);
        }

        .cart-count {
            position: absolute;
            top: -8px;
            right: -10px;
            background-color: var(--burgundy-main);
            color: var(--white);
            border-radius: 50%;
            padding: 2px 7px;
            font-size: 11px;
            font-weight: bold;
        }

        /* أقسام الفلترة */
        .categories-nav {
            display: flex;
            justify-content: center;
            gap: 10px;
            padding: 20px;
            background: var(--white);
            overflow-x: auto;
            border-bottom: 1px solid var(--border-color);
        }

        .category-btn {
            background-color: var(--light-bg);
            border: 1px solid var(--border-color);
            padding: 10px 20px;
            border-radius: 20px;
            cursor: pointer;
            font-weight: bold;
            white-space: nowrap;
        }

        .category-btn.active, .category-btn:hover {
            background-color: var(--burgundy-main);
            color: var(--white);
            border-color: var(--burgundy-main);
        }

        .hero {
            background: linear-gradient(135deg, var(--dark-black) 0%, var(--burgundy-dark) 100%);
            color: var(--white);
            text-align: center;
            padding: 40px 20px;
            border-bottom: 4px solid var(--burgundy-main);
        }

        .hero h1 {
            font-size: 36px;
            margin-bottom: 10px;
        }

        .container {
            max-width: 1300px;
            margin: 0 auto;
            padding: 40px 20px;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
            gap: 25px;
        }

        .product-card {
            background: var(--white);
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 4px 10px rgba(0,0,0,0.03);
            border: 1px solid var(--border-color);
            display: flex;
            flex-direction: column;
            cursor: pointer;
        }

        .product-card:hover {
            transform: translateY(-5px);
            border-color: var(--burgundy-main);
            box-shadow: 0 10px 20px rgba(128, 0, 32, 0.15);
        }

        .product-img-box {
            width: 100%;
            height: 230px;
            background-color: #ffffff;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            border-bottom: 1px solid var(--border-color);
        }

        .product-img-box img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .product-details {
            padding: 20px;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
        }

        .product-title {
            font-size: 16px;
            font-weight: 700;
            margin-bottom: 8px;
            height: 44px;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }

        .product-price {
            font-size: 18px;
            font-weight: bold;
            color: var(--burgundy-main);
            margin-bottom: 15px;
            margin-top: auto;
        }

        .add-btn {
            background-color: var(--burgundy-main);
            color: var(--white);
            border: none;
            padding: 12px;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
        }

        .add-btn:hover {
            background-color: var(--dark-black);
        }

        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.7);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 2000;
            padding: 20px;
        }

        .modal-content {
            background-color: var(--white);
            border-radius: 16px;
            width: 100%;
            max-width: 550px;
            max-height: 90vh;
            overflow-y: auto;
            padding: 30px;
            position: relative;
            border-top: 6px solid var(--burgundy-main);
        }

        .close-btn {
            position: absolute;
            top: 20px;
            left: 20px;
            font-size: 24px;
            cursor: pointer;
            color: #aaa;
            z-index: 10;
        }

        .product-view-img {
            width: 100%;
            max-height: 300px;
            object-fit: contain;
            border-radius: 8px;
            margin-bottom: 15px;
            background-color: #fff;
        }

        .product-view-specs {
            background: var(--light-bg);
            padding: 15px;
            border-radius: 8px;
            margin: 15px 0;
            font-size: 14px;
            line-height: 1.6;
            border-right: 4px solid var(--burgundy-main);
        }

        .contact-highlight {
            background: #fffbeb;
            border: 1px solid #fef3c7;
            padding: 12px;
            border-radius: 6px;
            margin-top: 12px;
            color: #b45309;
            font-weight: bold;
            font-size: 14px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 12px 0;
            border-bottom: 1px solid var(--border-color);
        }

        .input-group {
            margin-top: 15px;
            text-align: right;
        }

        .input-group label {
            display: block;
            margin-bottom: 6px;
            font-weight: bold;
            font-size: 14px;
        }

        .input-group input {
            width: 100%;
            padding: 12px;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            outline: none;
            font-size: 14px;
        }

        .input-group input:focus {
            border-color: var(--burgundy-main);
        }

        .input-group input:disabled {
            background-color: #fce8ec;
            border-color: #f3a3b4;
            color: var(--burgundy-main);
            font-weight: bold;
            cursor: not-allowed;
        }

        .payment-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 8px;
            margin: 15px 0;
        }

        .payment-card {
            border: 2px solid var(--border-color);
            border-radius: 8px;
            padding: 12px 2px;
            text-align: center;
            cursor: pointer;
            font-weight: bold;
            font-size: 12px;
        }

        .payment-card.active {
            border-color: var(--burgundy-main);
            background-color: var(--burgundy-light);
            color: var(--burgundy-main);
        }

        .project-notice-box {
            background-color: #fce8ec;
            border: 2px dashed #f3a3b4;
            border-radius: 8px;
            padding: 15px;
            margin-top: 15px;
            text-align: center;
            color: var(--burgundy-main);
            font-weight: bold;
        }

        #invoicePrintArea {
            background: white;
            padding: 20px;
            border: 1px solid var(--border-color);
            margin-top: 15px;
            border-radius: 8px;
        }

        .invoice-header {
            text-align: center;
            border-bottom: 2px solid var(--burgundy-main);
            padding-bottom: 15px;
            margin-bottom: 15px;
        }

        .action-btn {
            background-color: var(--burgundy-main);
            color: white;
            border: none;
            padding: 12px;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
            margin-top: 10px;
            font-size: 15px;
        }

        .action-btn.whatsapp { background-color: #25d366; }
        .action-btn.pdf-btn { background-color: #e11d48; }
        .action-btn.thanks-btn { background-color: var(--dark-black); }

        footer {
            background-color: var(--dark-black);
            color: var(--white);
            text-align: center;
            padding: 35px 20px;
            margin-top: 50px;
            border-top: 3px solid var(--burgundy-main);
            line-height: 1.8;
        }

        .footer-phone {
            color: #ffffff;
            font-weight: bold;
            font-size: 16px;
            margin: 10px 0;
            background: var(--burgundy-main);
            display: inline-block;
            padding: 5px 15px;
            border-radius: 20px;
        }

        .payment-methods-footer {
            margin-top: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 15px;
            flex-wrap: wrap;
        }

        .payment-methods-footer img {
            height: 25px;
            background-color: var(--white);
            padding: 4px 8px;
            border-radius: 4px;
            object-fit: contain;
        }
        
        .cod-badge {
            font-size: 11px;
            font-weight: bold;
            background-color: var(--white);
            color: var(--dark-black);
            padding: 4px 8px;
            border-radius: 4px;
            display: flex;
            align-items: center;
            gap: 4px;
            height: 25px;
        }
    </style>
</head>
<body>

    <div id="storeMainContent">
        <header>
            <div class="logo-vertex" onclick="location.reload()">VERTEX</div>
            <div class="header-user-badge">
                <div class="cart-icon-container" onclick="openCart()">
                    <i class="fa-solid fa-basket-shopping"></i>
                    <span class="cart-count" id="cartCount">0</span>
                </div>
            </div>
        </header>

        <section class="hero">
            <h1>متجر VERTEX الإلكتروني</h1>
            <p>أحدث التشكيلات الحصرية والمنتجات الأكثر طلباً وترند بأسعار تنافسية</p>
        </section>

        <div class="categories-nav">
            <button class="category-btn active" onclick="filterCategory('all', this)">كل المنتجات التجهيزية</button>
            <button class="category-btn" onclick="filterCategory('phones', this)">إكسسوارات الجوالات</button>
            <button class="category-btn" onclick="filterCategory('cars', this)">إكسسوارات السيارات</button>
            <button class="category-btn" onclick="filterCategory('lighting', this)">إضاءة وديكور الغرف</button>
            <button class="category-btn" onclick="filterCategory('trends', this)">منتجات ترند</button>
        </div>

        <main class="container">
            <div class="products-grid" id="mainProductsContainer"></div>
        </main>

        <div class="modal" id="productViewModal">
            <div class="modal-content">
                <i class="fa-solid fa-xmark close-btn" onclick="closeModal('productViewModal')"></i>
                <img src="" id="viewProductImg" class="product-view-img" alt="صورة المنتج">
                <h2 id="viewProductTitle" style="color: var(--dark-black); font-size: 20px; margin-bottom: 10px;"></h2>
                <h3 id="viewProductPrice" style="color: var(--burgundy-main); font-size: 22px; font-weight: bold;"></h3>
                
                <div class="product-view-specs" id="viewProductSpecs"></div>
                
                <div id="inlineAddToCartBtnContainer"></div>
            </div>
        </div>

        <div class="modal" id="cartModal">
            <div class="modal-content">
                <i class="fa-solid fa-xmark close-btn" onclick="closeModal('cartModal')"></i>
                <h3 style="color: var(--burgundy-main); margin-bottom: 15px;"><i class="fa-solid fa-cart-shopping"></i> حقيبة التسوق</h3>
                
                <div id="modalCartItems"></div>
                
                <div style="display:flex; justify-content:space-between; margin-top:20px; font-weight:bold; font-size:18px; border-top:1px solid #eee; padding-top:15px;">
                    <span>المجموع:</span>
                    <span id="modalTotal">0 ر.س</span>
                </div>

                <div id="stepPhoneSection" style="margin-top:20px;">
                    <div class="input-group">
                        <label><i class="fa-solid fa-phone" style="color:var(--burgundy-main)"></i> رقم جوال العميل للطلب والتسليم:</label>
                        <input type="tel" id="userPhoneInput" placeholder="05xxxxxxxx">
                    </div>
                    <button class="action-btn" style="margin-top:15px;" onclick="validatePhoneStep()">الانتقال لخيارات الدفع</button>
                </div>

                <div id="stepPaymentSection" style="display:none; margin-top:25px; border-top: 2px dashed var(--burgundy-main); padding-top:15px;">
                    <h4 style="margin-bottom:10px;">اختر طريقة الدفع:</h4>
                    <div class="payment-grid">
                        <div class="payment-card active" onclick="changePayment('cod')">الدفع عند الاستلام</div>
                        <div class="payment-card" onclick="changePayment('mada')">مدى</div>
                        <div class="payment-card" onclick="changePayment('visa')">فيزا</div>
                        <div class="payment-card" onclick="changePayment('apple')">Apple Pay</div>
                        <div class="payment-card" onclick="changePayment('google')">Google Pay</div>
                    </div>

                    <div id="codFields">
                        <div class="input-group">
                            <label>الاسم الكامل للمستلم</label>
                            <input type="text" id="codName" placeholder="أدخل اسمك الثلاثي هنا لتأكيد الطلب">
                        </div>
                        <div class="input-group">
                            <label>عنوان التوصيل المدن / الأحياء</label>
                            <input type="text" id="codAddress" placeholder="مثال: الرياض - حي النرجس">
                        </div>
                    </div>

                    <div id="normalCardFields" style="display:none;">
                        <div class="input-group">
                            <label>الاسم الكامل لصاحب البطاقة</label>
                            <input type="text" value="بوابة الدفع الإلكتروني المباشر قيد الصيانة" disabled>
                        </div>
                        <div class="input-group">
                            <label>رقم البطاقة</label>
                            <input type="text" value="يرجى اختيار الدفع عند الاستلام حالياً" disabled>
                        </div>
                    </div>

                    <div id="applePayField" style="display:none;">
                        <div class="project-notice-box">
                            <i class="fa-brands fa-apple-pay" style="font-size:32px; display:block; margin-bottom:5px;"></i>
                            بوابة Apple Pay السريعة قيد التحديث الرقمي.
                        </div>
                        <button class="action-btn" style="background-color:black; color:white;" onclick="processFinalOrder('Apple Pay')">تأكيد ومحاكاة طلب Apple Pay</button>
                    </div>

                    <div id="googlePayField" style="display:none;">
                        <div class="project-notice-box" style="background-color: #e8f0fe; border-color: #aecbfa; color: #1a73e8;">
                            <i class="fa-brands fa-google-pay" style="font-size:32px; display:block; margin-bottom:5px;"></i>
                            بوابة Google Pay السريعة قيد التحديث الرقمي.
                        </div>
                        <button class="action-btn" style="background-color:#1a73e8; color:white;" onclick="processFinalOrder('Google Pay')">تأكيد ومحاكاة طلب Google Pay</button>
                    </div>

                    <button class="action-btn" id="finalCheckoutBtn" style="margin-top:20px;" onclick="processFinalOrder()">تأكيد الطلب بنجاح</button>
                </div>
            </div>
        </div>

        <div class="modal" id="invoiceModal">
            <div class="modal-content" style="max-width: 600px;">
                <a href="https://wa.me/966540365657" target="_blank" style="text-decoration: none;">
                    <div class="action-btn whatsapp" style="text-align:center; font-size:14px; margin-bottom:15px; color:#fff;">
                        <i class="fa-brands fa-whatsapp"></i> اضغط هنا لتأكيد طلبك فوراً عبر واتساب المتجر: 0540365657
                    </div>
                </a>

                <div id="invoicePrintArea">
                    <div class="invoice-header">
                        <h2 style="color:var(--burgundy-main);">VERTEX INVOICE</h2>
                        <p style="font-size:12px; color:#666;">فاتورة شراء رقمية - تفاصيل الطلب</p>
                        <p style="font-size:14px; color:var(--burgundy-main); font-weight: bold; margin-top: 5px;">رقم تواصل المتجر: 0540365657</p>
                    </div>
                    <div style="font-size:14px; margin-bottom:15px; line-height:1.6;">
                        <strong>رقم الجوال للعميل:</strong> <span id="invPhone"></span><br>
                        <strong>طريقة الدفع المختارة:</strong> <span id="invMethod"></span><br>
                        <div id="invCodDetails" style="display:none;">
                            <strong>اسم المستلم:</strong> <span id="invName"></span><br>
                            <strong>عنوان الشحن:</strong> <span id="invAddress"></span>
                        </div>
                        <strong>التاريخ:</strong> 2026-06-06
                    </div>
                    <table style="width:100%; border-collapse:collapse; font-size:14px;">
                        <thead>
                            <tr style="background-color:var(--burgundy-light); color:var(--burgundy-main);">
                                <th style="padding:8px; text-align:right;">المنتج</th>
                                <th style="padding:8px; text-align:center;">الكمية</th>
                                <th style="padding:8px; text-align:left;">السعر</th>
                            </tr>
                        </thead>
                        <tbody id="invoiceTableBody"></tbody>
                    </table>
                    <div style="text-align:left; margin-top:15px; font-weight:bold; font-size:16px; border-top:2px solid var(--burgundy-main); padding-top:10px;">
                        إجمالي المبلغ المستحق: <span id="invTotal"></span>
                    </div>
                </div>

                <button class="action-btn pdf-btn" style="margin-top:20px;" onclick="downloadPDF()"><i class="fa-solid fa-file-pdf"></i> حفظ الفاتورة PDF</button>
                <button class="action-btn thanks-btn" onclick="finishAndReset()"><i class="fa-solid fa-circle-check"></i> إغلاق وتأكيد</button>
            </div>
        </div>

        <footer>
            <p>&copy; 2026 متجر VERTEX الحصري - جميع الحقوق محفوظة</p>
            <p class="footer-phone"><i class="fa-solid fa-phone"></i> رقم التواصل: 0540365657</p>
            
            <div class="payment-methods-footer">
                <img src="https://upload.wikimedia.org/wikipedia/commons/b/b0/Apple_Pay_logo.svg" alt="Apple Pay">
                <img src="https://upload.wikimedia.org/wikipedia/commons/c/c7/Google_Pay_Logo.svg" alt="Google Pay">
                <img src="https://upload.wikimedia.org/wikipedia/commons/8/84/Visa_2021.svg" alt="Visa">
                <img src="https://assets.salla.sa/cp/assets/images/payment/mada.svg" alt="Mada">
                <div class="cod-badge"><i class="fa-solid fa-hand-holding-dollar"></i> الدفع عند الاستلام</div>
            </div>
        </footer>
    </div>

    <script>
        // مصفوفة المنتجات الحصرية المربوطة بمصادر صور حقيقية ومباشرة من علي إكسبريس (ae01.alicdn.com)
        const productsList = [
            // قسم إكسسوارات الجوالات Phones
            { id: 1, category: "phones", title: "حامل جوال مغناطيسي Magsafe مكتبي ذكي 3 في 1", price: 99, img: "https://ae01.alicdn.com/kf/S5df79b1df0ef430a969b2d3bf305a4647/3-In-1-Magnetic-Wireless-Charger-Stand-For-iPhone-14-13-12-Pro-Max-Apple-Watch.jpg", specs: "قاعدة شحن لاسلكية متطورة مغناطيسية، مثالية لتنظيم الهواتف، الساعات الذكية، والسماعات اللاسلكية بمظهر عصري مميز." },
            { id: 2, category: "phones", title: "كابل شحن نايلون مضفر فائق القوة مع شاشة رقمية LED", price: 29, img: "https://ae01.alicdn.com/kf/H70bcbc603c4f48ffba6f6d89bfa52945V/Baseus-100W-USB-C-To-USB-Type-C-Cable-Digital-Display-Fast-Charging-Charger-Wire.jpg", specs: "كابل شحن مجهز بشاشة ذكية تعرض طاقة الشحن الفعلية بالواط ومصنوع من النسيج المقاوم للقطع والالتواء والتلف السريع." },
            { id: 3, category: "phones", title: "سماعات بلوتوث TWS داخل الأذن عازلة تماماً للضوضاء", price: 54, img: "https://ae01.alicdn.com/kf/S0b58e77c4e51413a968bd0a563b71bfbe/Lenovo-LP40-Pro-Earphone-Bluetooth-Wireless-Headphones-Mini-Earbuds-Touch-Control-Sport-Headset.jpg", specs: "سماعة لاسلكية مريحة وذكية تمنحك صوتاً محيطياً ممتعاً، ومقاومة للتعرق ومثالية للاستخدام اليومي المستمر وبطارية طويلة المدى." },

            // قسم إكسسوارات السيارات Cars
            { id: 4, category: "cars", title: "مثبت جوال ألومنيوم فخم مغناطيسي دوار لفتحة التكييف", price: 39, img: "https://ae01.alicdn.com/kf/S0730d1efbdf849769da46cb66927909cl/Baseus-Magnetic-Car-Phone-Holder-Air-Vent-Mount-Stand-For-iPhone-Samsung-Xiaomi-Universal-Cell.jpg", specs: "قاعدة تثبيت للهاتف ألومنيوم فخمة مدمجة بمغناطيس عالي القوة يضمن ثباتاً أسطورياً لجوالك في المطبات والطرق الوعرة." },
            { id: 5, category: "cars", title: "شاحن سيارة سريع ذكي ومنفذين شحن PD عالي الأداء", price: 45, img: "https://ae01.alicdn.com/kf/S2666113dbff4453cb12a52ee24037803C/Baseus-160W-Digital-Display-Car-Charger-QC-5-0-Fast-Charging-Type-C-Car-USB-Charger.jpg", specs: "قابس ولاعة ذكي يوفر طاقة شحن فائقة لهاتفك الذكي وأجهزتك الرقمية بأمان وبدون التسبب في أي حرارة زائدة بالسيارة." },
            { id: 6, category: "cars", title: "إضاءة سقف السيارة الداخلية المحيطية بمنفذ USB مذهل", price: 35, img: "https://ae01.alicdn.com/kf/Sbe0b82f80eb34ca4bebf650949d26bb36/USB-Car-Roof-Atmosphere-Star-Sky-Lamp-LED-Interior-Ambient-Night-Light-Projector-Galaxies-Decoration.jpg", specs: "جهاز إسقاط ضوئي ليزري صغير يضفي أجواء النجوم والمجرات الساحرة داخل السيارة لرحلات وقيادة ليلية استثنائية." },

            // قسم إضاءة وديكور الغرف Lighting
            { id: 7, category: "lighting", title: "شريط إضاءة ذكي RGB مخصص لخلفيات شاشات غرف القيمنق", price: 65, img: "https://ae01.alicdn.com/kf/Scb01b65074f046e7b2f0a8276f7b3e5ex/Tuya-Wifi-Smart-LED-Light-Strip-RGB-5050-Flexible-Tape-Luces-Led-With-Remote-Control-Alexa.jpg", specs: "شريط نيون ليد ذكي يتكامل بريموت وتحكم مرن عبر الجوال، ويتزامن مع الموجات الصوتية لخلق تجربة ديكور غرف أسطورية." },
            { id: 8, category: "lighting", title: "مصباح إسقاط ضوئي رائد الفضاء الشهير لعرض الفضاء والنجوم", price: 119, img: "https://ae01.alicdn.com/kf/S003d6d02f8db4cb4ad0be4bbf9cbef511/Astronaut-Galaxy-Starry-Sky-Projector-Night-Light-LED-Lamp-For-Bedroom-Room-Decor-Decorative-Nightlights.jpg", specs: "بروجكتر رائد الفضاء المميز لعرض السديم الكوني النجمي المتحرك على الأسقف والجدران لخلق بيئة جلوس مريحة وملهمة." },
            { id: 9, category: "lighting", title: "مصباح مكتبي حلزوني عصري وقاعدة شحن لاسلكية سريعة للموبايل", price: 145, img: "https://ae01.alicdn.com/kf/S91ea3fa7a3464197995f36e4f0bb4e1dt/Modern-Spiral-LED-Table-Lamp-Desk-Bedside-Night-Light-With-Wireless-Charger-For-Bedroom-Living-Room.jpg", specs: "إضاءة مكتبية فخمة بشكل انسيابي فريد، تدعم تخصيص مستوى السطوع وقاعدتها مجهزة بشاحن هاتف ذكي لاسلكي ذكي وسريع." },

            // قسم منتجات ترند Trends
            { id: 10, category: "trends", title: "محفظة بطاقات رجالية ذكية مقاومة للاختراق اللاسلكي من ألياف الكربون", price: 32, img: "https://ae01.alicdn.com/kf/Sf3b1368c85784f1882d96281be39f88bt/Anti-Theft-RFID-Blocking-Carbon-Fiber-Wallet-Slim-Smart-Money-Clip-Credit-Card-Holder-For-Men.jpg", specs: "محفظة بطاقات فخمة وصغيرة تنبثق تلقائياً بضغطة زر واحدة لحماية بيانات بطاقاتك البنكية تماماً من السرقة الإلكترونية." },
            { id: 11, category: "trends", title: "لوحة ماوس ديسك مكتبية ضخمة RGB مخصصة للألعاب والقيمنق", price: 59, img: "https://ae01.alicdn.com/kf/S32d56a297746401fa91cf69be6c507a2V/RGB-Gaming-Mouse-Pad-Large-Gamer-Mousepad-Big-Computer-Mouse-Mat-With-Backlight-Carpet-For-Keyboard.jpg", specs: "ماوس باد عملاق مضاد للسوائل ومغطى بنسيج ناعم يضمن سلاسة حركة الماوس، بإطار ليد متوهج يضفي رونقاً رائعاً للمكتب." },
            { id: 12, category: "trends", title: "مكبر صوت بلوتوث محمول مقاوم للصدمات والماء للرحلات الخارجية", price: 79, img: "https://ae01.alicdn.com/kf/S0b37db8754b248a39d89243763f0bb0fw/Mifa-A10-Plus-Portable-Bluetooth-Speaker-Stereo-Sound-30W-IPX7-Waterproof-Wireless-Speakers-For-Outdoor.jpg", specs: "سبيكر لاسلكي متين يمنحك صوتاً جهورياً ونقياً، مقاوم للماء ليكون رفيقك المثالي في التجمعات والطلعات البرية والبحرية." }
        ];

        let cart = [];
        let currentSelectedMethod = 'cod';

        window.onload = function() {
            renderProducts(productsList);
        };

        function renderProducts(items) {
            const container = document.getElementById('mainProductsContainer');
            container.innerHTML = '';
            items.forEach(p => {
                const card = document.createElement('div');
                card.className = 'product-card';
                card.addEventListener('click', () => { openProductView(p.id); });

                card.innerHTML = `
                    <div class="product-img-box">
                        <img src="${p.img}" alt="${p.title}" onerror="this.src='https://images.unsplash.com/photo-1546868871-7041f2a55e12?auto=format&fit=crop&w=400&q=80'">
                    </div>
                    <div class="product-details">
                        <h3 class="product-title">${p.title}</h3>
                        <div class="product-price">${p.price} ر.س</div>
                        <button class="add-btn" onclick="event.stopPropagation(); addToCart(${p.id})">إضافة للسلة</button>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        function openProductView(id) {
            const product = productsList.find(p => p.id === id);
            if (!product) return;

            document.getElementById('viewProductImg').src = product.img;
            document.getElementById('viewProductTitle').textContent = product.title;
            document.getElementById('viewProductPrice').textContent = `${product.price} ر.س`;
            
            document.getElementById('viewProductSpecs').innerHTML = `
                <p style="margin-bottom:10px; font-weight:500;">${product.specs}</p>
                <div class="contact-highlight">
                    <i class="fa-solid fa-headset"></i> رقم تواصل المتجر الرسمي: 0540365657
                </div>
            `;

            document.getElementById('inlineAddToCartBtnContainer').innerHTML = `
                <button class="action-btn" onclick="addToCart(${product.id}); closeModal('productViewModal');">إضافة إلى حقيبة التسوق</button>
            `;

            document.getElementById('productViewModal').style.display = 'flex';
        }

        function filterCategory(cat, btn) {
            document.querySelectorAll('.category-btn').forEach(b => b.classList.remove('active'));
            btn.classList.add('active');
            if(cat === 'all') { renderProducts(productsList); } 
            else { renderProducts(productsList.filter(p => p.category === cat)); }
        }

        function addToCart(id) {
            const product = productsList.find(p => p.id === id);
            const exist = cart.find(item => item.id === id);
            if(exist) { exist.qty++; } else { cart.push({ ...product, qty: 1 }); }
            updateCartUI();
        }

        function updateCartUI() {
            document.getElementById('cartCount').textContent = cart.reduce((acc, item) => acc + item.qty, 0);
            const container = document.getElementById('modalCartItems');
            container.innerHTML = '';

            if(cart.length === 0) {
                container.innerHTML = '<p style="text-align:center; padding:20px; color:#999;">حقيبة التسوق فارغة حالياً.</p>';
                document.getElementById('stepPhoneSection').style.display = 'none';
            } else {
                document.getElementById('stepPhoneSection').style.display = 'block';
                cart.forEach(item => {
                    container.innerHTML += `
                        <div class="cart-item">
                            <div><strong>${item.title}</strong><br><small>الكمية: ${item.qty}</small></div>
                            <div style="font-weight:bold;">${item.price * item.qty} ر.س</div>
                        </div>`;
                });
            }
            document.getElementById('modalTotal').textContent = `${cart.reduce((acc, item) => acc + (item.price * item.qty), 0)} ر.س`;
        }

        function openCart() { updateCartUI(); document.getElementById('cartModal').style.display = 'flex'; }
        function closeModal(id) { document.getElementById(id).style.display = 'none'; }

        function validatePhoneStep() {
            const phone = document.getElementById('userPhoneInput').value.trim();
            if(!phone || phone.length < 9) { alert('الرجاء إدخال رقم جوال صحيح لتأكيد وشحن الطلبية.'); return; }
            document.getElementById('stepPaymentSection').style.display = 'block';
        }

        function changePayment(method) {
            currentSelectedMethod = method;
            document.querySelectorAll('.payment-card').forEach(c => c.classList.remove('active'));
            event.target.classList.add('active');

            const codFields = document.getElementById('codFields');
            const normalFields = document.getElementById('normalCardFields');
            const appleField = document.getElementById('applePayField');
            const googleField = document.getElementById('googlePayField');
            const finalBtn = document.getElementById('finalCheckoutBtn');

            codFields.style.display = 'none';
            normalFields.style.display = 'none';
            appleField.style.display = 'none';
            googleField.style.display = 'none';
            finalBtn.style.display = 'block';

            if(method === 'cod') {
                codFields.style.display = 'block';
            } else if(method === 'apple') {
                appleField.style.display = 'block';
                finalBtn.style.display = 'none';
            } else if(method === 'google') {
                googleField.style.display = 'block';
                finalBtn.style.display = 'none';
            } else {
                normalFields.style.display = 'block';
            }
        }

        function processFinalOrder(forcedMethod = '') {
            const phone = document.getElementById('userPhoneInput').value.trim();
            const methodUsed = forcedMethod ? forcedMethod : currentSelectedMethod;

            document.getElementById('invPhone').textContent = phone;
            const codDetailsDiv = document.getElementById('invCodDetails');

            if(methodUsed === 'cod') {
                const codName = document.getElementById('codName').value.trim();
                const codAddress = document.getElementById('codAddress').value.trim();
                if(!codName || !codAddress) {
                    alert('فضلاً قم بكتابة الاسم والعنوان لتأكيد الشحن الفوري عند الاستلام.');
                    return;
                }
                document.getElementById('invMethod').textContent = "الدفع عند الاستلام";
                document.getElementById('invName').textContent = codName;
                document.getElementById('invAddress').textContent = codAddress;
                codDetailsDiv.style.display = 'block';
            } else {
                document.getElementById('invMethod').textContent = forcedMethod ? forcedMethod : currentSelectedMethod.toUpperCase();
                codDetailsDiv.style.display = 'none';
            }

            const tbody = document.getElementById('invoiceTableBody');
            tbody.innerHTML = '';
            cart.forEach(item => {
                tbody.innerHTML += `
                    <tr>
                        <td style="padding:8px; border-bottom:1px solid #eee;">${item.title}</td>
                        <td style="padding:8px; border-bottom:1px solid #eee; text-align:center;">${item.qty}</td>
                        <td style="padding:8px; border-bottom:1px solid #eee; text-align:left;">${item.price * item.qty} ر.س</td>
                    </tr>`;
                });

            document.getElementById('invTotal').textContent = `${cart.reduce((acc, item) => acc + (item.price * item.qty), 0)} ر.س`;
            closeModal('cartModal');
            document.getElementById('invoiceModal').style.display = 'flex';
        }

        window.onclick = function(event) {
            const modals = document.querySelectorAll('.modal');
            modals.forEach(m => {
                if (event.target === m) {
                    if (m.id === 'invoiceModal') { finishAndReset(); } 
                    else { m.style.display = 'none'; }
                }
            });
        }

        function downloadPDF() {
            const element = document.getElementById('invoicePrintArea');
            html2pdf().set({
                margin: 10, filename: 'VERTEX-Invoice.pdf',
                html2canvas: { scale: 2 }, jsPDF: { format: 'a4', orientation: 'portrait' }
            }).from(element).save();
        }

        function finishAndReset() {
            cart = [];
            updateCartUI();
            closeModal('invoiceModal');
            document.getElementById('codName').value = '';
            document.getElementById('codAddress').value = '';
            document.getElementById('userPhoneInput').value = '';
            document.getElementById('stepPaymentSection').style.display = 'none';
            changePayment('cod');
        }
    </script>
</body>
</html>
