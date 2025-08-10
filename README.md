# PLANTAMIX.github.io
T.A.B Farm
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PLANTAMIX - Catálogo de Plantas</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 20px;
            margin-bottom: 30px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
            text-align: center;
            position: relative;
        }

        .logo-container {
            margin-bottom: 15px;
        }

        .company-logo {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            object-fit: cover;
            border: 4px solid #2d5a27;
            margin-bottom: 10px;
            cursor: pointer;
            transition: transform 0.3s ease;
        }

        .company-logo:hover {
            transform: scale(1.05);
        }

        .logo-edit-btn {
            position: absolute;
            top: 20px;
            right: 20px;
            background: #4CAF50;
            color: white;
            border: none;
            padding: 8px 12px;
            border-radius: 20px;
            cursor: pointer;
            font-size: 0.9rem;
        }

        .header h1 {
            color: #2d5a27;
            font-size: 2.5rem;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .header p {
            color: #666;
            font-size: 1.1rem;
        }

        .search-filter-bar {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 30px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            display: grid;
            grid-template-columns: 2fr 1fr 1fr 1fr;
            gap: 15px;
            align-items: end;
        }

        .search-input {
            padding: 12px 15px;
            border: 2px solid #ddd;
            border-radius: 25px;
            font-size: 1rem;
            outline: none;
            transition: border-color 0.3s ease;
        }

        .search-input:focus {
            border-color: #4CAF50;
        }

        .filter-select {
            padding: 12px 15px;
            border: 2px solid #ddd;
            border-radius: 10px;
            font-size: 1rem;
            outline: none;
            background: white;
        }

        .results-count {
            color: #666;
            font-size: 1rem;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .admin-panel {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 30px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        }

        .admin-toggle {
            background: #4CAF50;
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1rem;
            transition: all 0.3s ease;
            margin-bottom: 20px;
        }

        .admin-toggle:hover {
            background: #45a049;
            transform: translateY(-2px);
        }

        .admin-controls {
            display: none;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .admin-controls.show {
            display: grid;
        }

        .form-section {
            background: #f9f9f9;
            padding: 20px;
            border-radius: 10px;
            border: 2px solid #e0e0e0;
        }

        .form-section h3 {
            color: #2d5a27;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .control-group {
            display: flex;
            flex-direction: column;
            gap: 8px;
            margin-bottom: 15px;
        }

        .control-group label {
            font-weight: bold;
            color: #2d5a27;
        }

        .control-group input, .control-group textarea, .control-group select {
            padding: 12px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s ease;
        }

        .control-group input:focus, .control-group textarea:focus {
            outline: none;
            border-color: #4CAF50;
        }

        .control-group textarea {
            resize: vertical;
            min-height: 80px;
        }

        .image-preview {
            width: 100%;
            max-width: 200px;
            height: 150px;
            object-fit: cover;
            border-radius: 10px;
            margin-top: 10px;
            border: 2px solid #ddd;
        }

        .btn {
            background: #4CAF50;
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }

        .btn:hover {
            background: #45a049;
            transform: translateY(-1px);
        }

        .btn-danger {
            background: #f44336;
        }

        .btn-danger:hover {
            background: #da190b;
        }

        .btn-secondary {
            background: #2196F3;
        }

        .btn-secondary:hover {
            background: #1976D2;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }

        .product-card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
            transition: all 0.3s ease;
            position: relative;
        }

        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.2);
        }

        .product-card.disabled {
            opacity: 0.6;
            filter: grayscale(50%);
        }

        .product-image {
            width: 100%;
            height: 250px;
            object-fit: cover;
            transition: transform 0.3s ease;
        }

        .product-card:hover .product-image {
            transform: scale(1.05);
        }

        .product-info {
            padding: 20px;
        }

        .product-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 15px;
        }

        .product-name {
            font-size: 1.4rem;
            font-weight: bold;
            color: #2d5a27;
            flex: 1;
        }

        .scientific-name {
            font-size: 0.9rem;
            font-style: italic;
            color: #666;
            margin-bottom: 10px;
        }

        .product-description {
            color: #666;
            margin-bottom: 15px;
            line-height: 1.5;
        }

        .technical-specs {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 10px;
            margin: 15px 0;
            font-size: 0.9rem;
        }

        .technical-specs h4 {
            color: #2d5a27;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .spec-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 8px;
        }

        .spec-item {
            display: flex;
            justify-content: space-between;
            padding: 5px 0;
            border-bottom: 1px solid #eee;
        }

        .spec-label {
            font-weight: bold;
            color: #555;
        }

        .spec-value {
            color: #777;
        }

        .care-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 5px;
            margin: 15px 0;
        }

        .care-tag {
            background: #e8f5e8;
            color: #2d5a27;
            padding: 4px 12px;
            border-radius: 15px;
            font-size: 0.8rem;
            border: 1px solid #c8e6c9;
        }

        .product-price {
            font-size: 1.5rem;
            font-weight: bold;
            color: #4CAF50;
            margin-bottom: 15px;
        }

        .product-status {
            position: absolute;
            top: 15px;
            right: 15px;
            padding: 5px 12px;
            border-radius: 15px;
            font-size: 0.9rem;
            font-weight: bold;
        }

        .status-available {
            background: #4CAF50;
            color: white;
        }

        .status-unavailable {
            background: #f44336;
            color: white;
        }

        .product-actions {
            display: grid;
            grid-template-columns: 1fr 1fr auto;
            gap: 10px;
            align-items: center;
        }

        .add-to-cart {
            background: linear-gradient(45deg, #4CAF50, #45a049);
            color: white;
            border: none;
            padding: 12px;
            border-radius: 10px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: bold;
            transition: all 0.3s ease;
        }

        .add-to-cart:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(76, 175, 80, 0.4);
        }

        .add-to-cart:disabled {
            background: #ccc;
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }

        .view-details {
            background: #2196F3;
            color: white;
            border: none;
            padding: 8px 12px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 0.9rem;
        }

        .edit-product {
            background: #FF9800;
            color: white;
            border: none;
            padding: 8px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 0.9rem;
        }

        .cart-floating {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: #25D366;
            color: white;
            border: none;
            padding: 15px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 1.5rem;
            box-shadow: 0 4px 15px rgba(37, 211, 102, 0.4);
            transition: all 0.3s ease;
            z-index: 1000;
        }

        .cart-floating:hover {
            transform: scale(1.1);
            box-shadow: 0 6px 20px rgba(37, 211, 102, 0.6);
        }

        .share-qr-btn {
            position: fixed;
            bottom: 90px;
            right: 20px;
            background: #FF6B35;
            color: white;
            border: none;
            padding: 12px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 1.2rem;
            box-shadow: 0 4px 15px rgba(255, 107, 53, 0.4);
            transition: all 0.3s ease;
            z-index: 1000;
        }

        .share-qr-btn:hover {
            transform: scale(1.1);
            box-shadow: 0 6px 20px rgba(255, 107, 53, 0.6);
        }

        .cart-count {
            position: absolute;
            top: -5px;
            right: -5px;
            background: #f44336;
            color: white;
            border-radius: 50%;
            width: 25px;
            height: 25px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8rem;
            font-weight: bold;
        }

        .cart-modal {
            display: none;
            position: fixed;
            z-index: 2000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            backdrop-filter: blur(5px);
        }

        .cart-modal-content {
            background-color: white;
            margin: 2% auto;
            padding: 0;
            border-radius: 20px;
            width: 95%;
            max-width: 800px;
            max-height: 90vh;
            overflow: hidden;
            position: relative;
            display: flex;
            flex-direction: column;
        }

        .cart-modal-header {
            background: linear-gradient(135deg, #4CAF50, #45a049);
            color: white;
            padding: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .cart-modal-header h2 {
            margin: 0;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .cart-modal-body {
            flex: 1;
            overflow-y: auto;
            padding: 20px;
        }

        .cart-items {
            max-height: 300px;
            overflow-y: auto;
            margin-bottom: 20px;
        }

        .cart-item {
            display: flex;
            align-items: center;
            gap: 15px;
            padding: 15px;
            border: 1px solid #eee;
            border-radius: 10px;
            margin-bottom: 10px;
            background: #fafafa;
        }

        .cart-item-image {
            width: 60px;
            height: 60px;
            object-fit: cover;
            border-radius: 8px;
        }

        .cart-item-info {
            flex: 1;
        }

        .cart-item-info h4 {
            margin: 0 0 5px 0;
            color: #2d5a27;
        }

        .cart-item-price {
            color: #666;
            margin: 0;
            font-size: 0.9rem;
        }

        .quantity-controls {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-top: 5px;
        }

        .quantity-controls button {
            background: #4CAF50;
            color: white;
            border: none;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
        }

        .quantity {
            background: white;
            border: 1px solid #ddd;
            padding: 5px 15px;
            border-radius: 5px;
            min-width: 40px;
            text-align: center;
        }

        .cart-item-subtotal {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 10px;
            font-weight: bold;
            color: #4CAF50;
        }

        .remove-item {
            background: #f44336;
            color: white;
            border: none;
            padding: 5px 8px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 0.8rem;
        }

        .cart-summary {
            background: #f0f8ff;
            padding: 20px;
            border-radius: 10px;
            margin: 20px 0;
            border: 2px solid #4CAF50;
        }

        .cart-total {
            font-size: 1.5rem;
            font-weight: bold;
            color: #4CAF50;
            text-align: center;
            margin-bottom: 15px;
        }

        .cart-message-area {
            margin: 20px 0;
        }

        .cart-message-area label {
            font-weight: bold;
            color: #2d5a27;
            display: block;
            margin-bottom: 10px;
        }

        .cart-message {
            width: 100%;
            height: 200px;
            padding: 15px;
            border: 2px solid #ddd;
            border-radius: 10px;
            font-family: monospace;
            font-size: 0.9rem;
            resize: vertical;
            background: #f9f9f9;
        }

        .cart-actions {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-top: 20px;
        }

        .cart-btn {
            padding: 15px 20px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-size: 1.1rem;
            font-weight: bold;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .cart-btn-copy {
            background: #2196F3;
            color: white;
        }

        .cart-btn-copy:hover {
            background: #1976D2;
            transform: translateY(-2px);
        }

        .cart-btn-whatsapp {
            background: #25D366;
            color: white;
        }

        .cart-btn-whatsapp:hover {
            background: #128C7E;
            transform: translateY(-2px);
        }

        .cart-btn-clear {
            background: #f44336;
            color: white;
            grid-column: span 2;
        }

        .cart-btn-clear:hover {
            background: #d32f2f;
        }

        .qr-modal {
            display: none;
            position: fixed;
            z-index: 2001;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            backdrop-filter: blur(5px);
        }

        .qr-modal-content {
            background-color: white;
            margin: 10% auto;
            padding: 30px;
            border-radius: 20px;
            width: 90%;
            max-width: 400px;
            text-align: center;
            position: relative;
        }

        .qr-image {
            width: 200px;
            height: 200px;
            border: 3px solid #4CAF50;
            border-radius: 10px;
            margin: 20px 0;
        }

        .qr-url-input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            margin: 10px 0;
            font-size: 0.9rem;
        }

        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 20px;
            border-radius: 10px;
            color: white;
            font-weight: bold;
            z-index: 3000;
            transform: translateX(400px);
            transition: transform 0.3s ease;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }

        .notification.show {
            transform: translateX(0);
        }

        .notification.success {
            background: #4CAF50;
        }

        .notification.error {
            background: #f44336;
        }

        .notification.info {
            background: #2196F3;
        }

        .chatbot-toggle {
            position: fixed;
            bottom: 20px;
            left: 20px;
            background: #2196F3;
            color: white;
            border: none;
            padding: 15px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 1.5rem;
            box-shadow: 0 4px 15px rgba(33, 150, 243, 0.4);
            transition: all 0.3s ease;
            z-index: 1000;
        }

        .chatbot-toggle:hover {
            transform: scale(1.1);
            box-shadow: 0 6px 20px rgba(33, 150, 243, 0.6);
        }

        .chatbot {
            position: fixed;
            bottom: 90px;
            left: 20px;
            width: 400px;
            height: 500px;
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            display: none;
            flex-direction: column;
            z-index: 999;
        }

        .chatbot.show {
            display: flex;
        }

        .chatbot-header {
            background: #2196F3;
            color: white;
            padding: 15px;
            border-radius: 15px 15px 0 0;
            font-weight: bold;
        }

        .chatbot-messages {
            flex: 1;
            padding: 15px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .message {
            padding: 10px 15px;
            border-radius: 18px;
            max-width: 80%;
            word-wrap: break-word;
        }

        .message.bot {
            background: #f1f1f1;
            align-self: flex-start;
        }

        .message.user {
            background: #2196F3;
            color: white;
            align-self: flex-end;
        }

        .chatbot-input {
            padding: 15px;
            border-top: 1px solid #eee;
            display: flex;
            gap: 10px;
        }

        .chatbot-input input {
            flex: 1;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 20px;
            outline: none;
        }

        .chatbot-input button {
            background: #2196F3;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 20px;
            cursor: pointer;
        }

        .faq-buttons {
            padding: 10px 15px;
            border-top: 1px solid #eee;
            display: flex;
            flex-wrap: wrap;
            gap: 5px;
        }

        .faq-btn {
            background: #e3f2fd;
            color: #2196F3;
            border: 1px solid #2196F3;
            padding: 5px 10px;
            border-radius: 15px;
            cursor: pointer;
            font-size: 0.8rem;
            transition: all 0.3s ease;
        }

        .faq-btn:hover {
            background: #2196F3;
            color: white;
        }

        .modal {
            display: none;
            position: fixed;
            z-index: 2000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            backdrop-filter: blur(5px);
        }

        .modal-content {
            background-color: white;
            margin: 5% auto;
            padding: 30px;
            border-radius: 20px;
            width: 90%;
            max-width: 600px;
            max-height: 80vh;
            overflow-y: auto;
            position: relative;
        }

        .close {
            position: absolute;
            right: 20px;
            top: 20px;
            color: #aaa;
            font-size: 28px;
            font-weight: bold;
            cursor: pointer;
        }

        .close:hover {
            color: #000;
        }

        .pagination {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            margin: 30px 0;
        }

        .pagination button {
            background: #4CAF50;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .pagination button:hover:not(:disabled) {
            background: #45a049;
        }

        .pagination button:disabled {
            background: #ccc;
            cursor: not-allowed;
        }

        .pagination .current-page {
            background: #2196F3;
            font-weight: bold;
        }

        @media (max-width: 768px) {
            .container {
                padding: 10px;
            }

            .header h1 {
                font-size: 2rem;
            }

            .search-filter-bar {
                grid-template-columns: 1fr;
                gap: 10px;
            }

            .products-grid {
                grid-template-columns: 1fr;
                gap: 20px;
            }

            .admin-controls {
                grid-template-columns: 1fr;
            }

            .chatbot {
                width: calc(100vw - 40px);
                height: 450px;
            }

            .product-actions {
                grid-template-columns: 1fr;
                gap: 8px;
            }

            .spec-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header class="header">
            <button class="logo-edit-btn" onclick="openLogoEditor()">
                <i class="fas fa-edit"></i> Cambiar Logo
            </button>
            <div class="logo-container">
                <img src="https://images.unsplash.com/photo-1416879595882-3373a0480b5b?w=80&h=80&fit=crop&crop=center" 
                     alt="Logo" class="company-logo" id="companyLogo">
            </div>
            <h1 id="companyName">PLANTAMIX</h1>
            <p id="companyTagline">T.A.P Farm</p>
        </header>

        <!-- Barra de búsqueda y filtros -->
        <div class="search-filter-bar">
            <div class="control-group">
                <input type="text" id="searchInput" class="search-input" 
                       placeholder="🔍 Buscar plantas por nombre, especie o cuidados..." 
                       oninput="searchProducts()">
            </div>
            <div class="control-group">
                <select id="categoryFilter" class="filter-select" onchange="searchProducts()">
                    <option value="">Todas las categorías</option>
                    <option value="interior">Interior</option>
                    <option value="exterior">Exterior</option>
                    <option value="colgante">Colgante</option>
                    <option value="suculenta">Suculenta</option>
                    <option value="tropical">Tropical</option>
                    <option value="aromatica">Aromática</option>
                </select>
            </div>
            <div class="control-group">
                <select id="difficultyFilter" class="filter-select" onchange="searchProducts()">
                    <option value="">
