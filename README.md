<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Sistema de Gestión de Almacén - Hostelería y Turismo</title>
    <link
      href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap"
      rel="stylesheet"
    />
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"
    />
    <style>
      :root {
        --primary: #2c3e50;
        --secondary: #3498db;
        --success: #2ecc71;
        --warning: #f39c12;
        --danger: #e74c3c;
        --light: #ecf0f1;
        --dark: #34495e;
        --gray: #95a5a6;
      }

      * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
      }

      body {
        font-family: "Roboto", sans-serif;
        background-color: #f5f7fa;
        color: var(--dark);
        line-height: 1.6;
      }

      .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 0 20px;
      }

      /* Login Styles */
      .login-container {
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        background: linear-gradient(135deg, var(--primary), var(--secondary));
      }

      .login-form {
        background: white;
        padding: 40px;
        border-radius: 10px;
        box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
        width: 100%;
        max-width: 400px;
      }

      .login-form h2 {
        text-align: center;
        margin-bottom: 30px;
        color: var(--primary);
      }

      .form-group {
        margin-bottom: 20px;
      }

      .form-group label {
        display: block;
        margin-bottom: 8px;
        font-weight: 500;
      }

      .form-control {
        width: 100%;
        padding: 12px 15px;
        border: 1px solid #ddd;
        border-radius: 5px;
        font-size: 16px;
        transition: border 0.3s;
      }

      .form-control:focus {
        border-color: var(--secondary);
        outline: none;
        box-shadow: 0 0 0 2px rgba(52, 152, 219, 0.2);
      }

      .btn {
        display: inline-block;
        padding: 12px 24px;
        background: var(--secondary);
        color: white;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        font-size: 16px;
        font-weight: 500;
        transition: all 0.3s;
        text-align: center;
      }

      .btn:hover {
        background: #2980b9;
        transform: translateY(-2px);
      }

      .btn-block {
        display: block;
        width: 100%;
      }

      .btn-success {
        background: var(--success);
      }

      .btn-success:hover {
        background: #27ae60;
      }

      .btn-warning {
        background: var(--warning);
      }

      .btn-warning:hover {
        background: #d35400;
      }

      .btn-danger {
        background: var(--danger);
      }

      .btn-danger:hover {
        background: #c0392b;
      }

      /* Profile Selection */
      .profile-selection {
        display: none;
        background: white;
        padding: 40px;
        border-radius: 10px;
        box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
        width: 100%;
        max-width: 500px;
        margin: 50px auto;
        text-align: center;
      }

      .profile-selection h2 {
        margin-bottom: 30px;
        color: var(--primary);
      }

      .profile-cards {
        display: flex;
        flex-wrap: wrap;
        gap: 20px;
        justify-content: center;
      }

      .profile-card {
        background: #f8f9fa;
        border: 1px solid #e9ecef;
        border-radius: 8px;
        padding: 20px;
        width: 200px;
        cursor: pointer;
        transition: all 0.3s;
      }

      .profile-card:hover {
        transform: translateY(-5px);
        box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        border-color: var(--secondary);
      }

      .profile-card i {
        font-size: 48px;
        color: var(--secondary);
        margin-bottom: 15px;
      }

      .profile-card h3 {
        margin-bottom: 10px;
      }

      /* Dashboard */
      .dashboard {
        display: none;
        min-height: 100vh;
      }

      .sidebar {
        position: fixed;
        top: 0;
        left: 0;
        height: 100vh;
        width: 250px;
        background: var(--primary);
        color: white;
        padding-top: 20px;
        z-index: 1000;
        overflow-y: auto;
        transition: all 0.3s;
      }

      .sidebar-header {
        padding: 0 20px 20px;
        border-bottom: 1px solid rgba(255, 255, 255, 0.1);
      }

      .sidebar-header h2 {
        font-size: 24px;
        font-weight: 500;
      }

      .user-info {
        display: flex;
        align-items: center;
        padding: 15px 20px;
        border-bottom: 1px solid rgba(255, 255, 255, 0.1);
      }

      .user-avatar {
        width: 40px;
        height: 40px;
        border-radius: 50%;
        background: var(--secondary);
        display: flex;
        align-items: center;
        justify-content: center;
        margin-right: 15px;
        font-weight: 500;
      }

      .user-details h3 {
        font-size: 16px;
        font-weight: 500;
        margin-bottom: 4px;
      }

      .user-details p {
        font-size: 14px;
        opacity: 0.7;
      }

      .sidebar-menu {
        padding: 20px 0;
      }

      .menu-item {
        display: block;
        padding: 12px 20px;
        color: rgba(255, 255, 255, 0.8);
        text-decoration: none;
        transition: all 0.3s;
        border-left: 3px solid transparent;
      }

      .menu-item:hover,
      .menu-item.active {
        background: rgba(255, 255, 255, 0.1);
        color: white;
        border-left-color: var(--secondary);
      }

      .menu-item i {
        margin-right: 10px;
        width: 20px;
        text-align: center;
      }

      .main-content {
        margin-left: 250px;
        padding: 20px;
        min-height: 100vh;
      }

      .header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 30px;
        padding-bottom: 15px;
        border-bottom: 1px solid #e9ecef;
      }

      .header h1 {
        font-size: 28px;
        font-weight: 500;
      }

      .header-actions {
        display: flex;
        gap: 15px;
      }

      .notification-icon {
        position: relative;
        font-size: 20px;
        color: var(--dark);
        cursor: pointer;
      }

      .notification-badge {
        position: absolute;
        top: -8px;
        right: -8px;
        background: var(--danger);
        color: white;
        font-size: 10px;
        width: 18px;
        height: 18px;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
      }

      .stats-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
        gap: 20px;
        margin-bottom: 30px;
      }

      .stat-card {
        background: white;
        border-radius: 8px;
        padding: 20px;
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        display: flex;
        align-items: center;
      }

      .stat-icon {
        width: 60px;
        height: 60px;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 24px;
        margin-right: 20px;
      }

      .stat-icon.primary {
        background: rgba(52, 152, 219, 0.1);
        color: var(--secondary);
      }

      .stat-icon.success {
        background: rgba(46, 204, 113, 0.1);
        color: var(--success);
      }

      .stat-icon.warning {
        background: rgba(243, 156, 18, 0.1);
        color: var(--warning);
      }

      .stat-icon.danger {
        background: rgba(231, 76, 60, 0.1);
        color: var(--danger);
      }

      .stat-info h3 {
        font-size: 24px;
        font-weight: 500;
        margin-bottom: 5px;
      }

      .stat-info p {
        font-size: 14px;
        color: var(--gray);
      }

      .card {
        background: white;
        border-radius: 8px;
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        margin-bottom: 30px;
      }

      .card-header {
        padding: 20px;
        border-bottom: 1px solid #e9ecef;
        display: flex;
        justify-content: space-between;
        align-items: center;
      }

      .card-title {
        font-size: 20px;
        font-weight: 500;
      }

      .card-body {
        padding: 20px;
      }

      .table {
        width: 100%;
        border-collapse: collapse;
      }

      .table th,
      .table td {
        padding: 12px 15px;
        text-align: left;
        border-bottom: 1px solid #e9ecef;
      }

      .table th {
        background: #f8f9fa;
        font-weight: 500;
      }

      .table tr:hover {
        background: #f8f9fa;
      }

      .badge {
        display: inline-block;
        padding: 4px 8px;
        border-radius: 4px;
        font-size: 12px;
        font-weight: 500;
      }

      .badge-success {
        background: rgba(46, 204, 113, 0.1);
        color: var(--success);
      }

      .badge-warning {
        background: rgba(243, 156, 18, 0.1);
        color: var(--warning);
      }

      .badge-danger {
        background: rgba(231, 76, 60, 0.1);
        color: var(--danger);
      }

      .btn-group {
        display: flex;
        gap: 10px;
      }

      .form-row {
        display: flex;
        gap: 20px;
        margin-bottom: 20px;
      }

      .form-col {
        flex: 1;
      }

      .modal {
        display: none;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.5);
        z-index: 2000;
        align-items: center;
        justify-content: center;
      }

      .modal-content {
        background: white;
        border-radius: 8px;
        width: 90%;
        max-width: 600px;
        max-height: 90vh;
        overflow-y: auto;
      }

      .modal-header {
        padding: 20px;
        border-bottom: 1px solid #e9ecef;
        display: flex;
        justify-content: space-between;
        align-items: center;
      }

      .modal-title {
        font-size: 20px;
        font-weight: 500;
      }

      .modal-close {
        background: none;
        border: none;
        font-size: 24px;
        cursor: pointer;
        color: var(--gray);
      }

      .modal-body {
        padding: 20px;
      }

      .modal-footer {
        padding: 20px;
        border-top: 1px solid #e9ecef;
        display: flex;
        justify-content: flex-end;
        gap: 10px;
      }

      .product-list {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
        gap: 15px;
        margin-bottom: 20px;
      }

      .product-item {
        border: 1px solid #e9ecef;
        border-radius: 8px;
        padding: 15px;
        cursor: pointer;
        transition: all 0.3s;
      }

      .product-item:hover {
        border-color: var(--secondary);
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
      }

      .product-item.selected {
        border-color: var(--success);
        background: rgba(46, 204, 113, 0.05);
      }

      .product-image {
        width: 100%;
        height: 120px;
        background: #f8f9fa;
        border-radius: 5px;
        margin-bottom: 10px;
        display: flex;
        align-items: center;
        justify-content: center;
        color: var(--gray);
      }

      .product-name {
        font-weight: 500;
        margin-bottom: 5px;
      }

      .product-price {
        color: var(--gray);
      }

      .order-summary {
        background: #f8f9fa;
        border-radius: 8px;
        padding: 20px;
        margin-top: 20px;
      }

      .order-item {
        display: flex;
        justify-content: space-between;
        padding: 10px 0;
        border-bottom: 1px solid #e9ecef;
      }

      .order-item:last-child {
        border-bottom: none;
        font-weight: 500;
        font-size: 18px;
      }

      .message-form {
        margin-bottom: 20px;
      }

      .recipient-list {
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
        margin-bottom: 15px;
      }

      .recipient-tag {
        background: #e9ecef;
        border-radius: 20px;
        padding: 5px 10px;
        display: flex;
        align-items: center;
        gap: 5px;
      }

      .recipient-tag button {
        background: none;
        border: none;
        color: var(--gray);
        cursor: pointer;
      }

      .message-list {
        max-height: 400px;
        overflow-y: auto;
      }

      .message-item {
        padding: 15px;
        border-bottom: 1px solid #e9ecef;
      }

      .message-header {
        display: flex;
        justify-content: space-between;
        margin-bottom: 10px;
      }

      .message-sender {
        font-weight: 500;
      }

      .message-date {
        font-size: 12px;
        color: var(--gray);
      }

      .message-content {
        margin-bottom: 10px;
      }

      .message-recipients {
        font-size: 12px;
        color: var(--gray);
      }

      .filter-container {
        display: flex;
        gap: 15px;
        margin-bottom: 20px;
        flex-wrap: wrap;
      }

      .filter-group {
        flex: 1;
        min-width: 200px;
      }

      .event-calendar {
        display: grid;
        grid-template-columns: repeat(7, 1fr);
        gap: 1px;
        background: #e9ecef;
        border: 1px solid #e9ecef;
        border-radius: 5px;
        overflow: hidden;
      }

      .calendar-day {
        background: white;
        padding: 10px;
        min-height: 80px;
        position: relative;
      }

      .calendar-day-header {
        background: #f8f9fa;
        font-weight: 500;
        text-align: center;
        padding: 10px;
      }

      .calendar-day-number {
        font-weight: 500;
        margin-bottom: 5px;
      }

      .calendar-event {
        background: var(--secondary);
        color: white;
        font-size: 12px;
        padding: 2px 5px;
        border-radius: 3px;
        margin-bottom: 3px;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
      }

      .provider-info {
        display: flex;
        align-items: center;
        gap: 15px;
        margin-bottom: 20px;
      }

      .provider-logo {
        width: 60px;
        height: 60px;
        background: #f8f9fa;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        color: var(--gray);
      }

      .provider-details h3 {
        margin-bottom: 5px;
      }

      .provider-details p {
        font-size: 14px;
        color: var(--gray);
      }

      .delivery-status {
        display: flex;
        align-items: center;
        gap: 10px;
      }

      .status-indicator {
        width: 12px;
        height: 12px;
        border-radius: 50%;
      }

      .status-indicator.pending {
        background: var(--warning);
      }

      .status-indicator.processing {
        background: var(--secondary);
      }

      .status-indicator.completed {
        background: var(--success);
      }

      .status-indicator.delayed {
        background: var(--danger);
      }

      .alert {
        padding: 15px;
        border-radius: 5px;
        margin-bottom: 20px;
      }

      .alert-success {
        background: rgba(46, 204, 113, 0.1);
        border-left: 4px solid var(--success);
        color: var(--success);
      }

      .alert-warning {
        background: rgba(243, 156, 18, 0.1);
        border-left: 4px solid var(--warning);
        color: var(--warning);
      }

      .alert-danger {
        background: rgba(231, 76, 60, 0.1);
        border-left: 4px solid var(--danger);
        color: var(--danger);
      }

      .tabs {
        display: flex;
        border-bottom: 1px solid #e9ecef;
        margin-bottom: 20px;
      }

      .tab {
        padding: 10px 20px;
        cursor: pointer;
        border-bottom: 2px solid transparent;
        font-weight: 500;
      }

      .tab.active {
        border-bottom-color: var(--secondary);
        color: var(--secondary);
      }

      .tab-content {
        display: none;
      }

      .tab-content.active {
        display: block;
      }

      @media (max-width: 768px) {
        .sidebar {
          transform: translateX(-100%);
        }

        .sidebar.active {
          transform: translateX(0);
        }

        .main-content {
          margin-left: 0;
        }

        .stats-container {
          grid-template-columns: 1fr;
        }

        .form-row {
          flex-direction: column;
        }

        .filter-container {
          flex-direction: column;
        }

        .product-list {
          grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
        }
      }
    </style>
  </head>
  <body>
    <!-- Login Form -->
    <div id="loginContainer" class="login-container">
      <div class="login-form">
        <h2>Sistema de Gestión de Almacén</h2>
        <form id="loginForm">
          <div class="form-group">
            <label for="email">Correo electrónico</label>
            <input
              type="email"
              id="email"
              class="form-control"
              placeholder="usuario@ejemplo.com"
              required
            />
          </div>
          <div class="form-group">
            <label for="password">Contraseña</label>
            <input
              type="password"
              id="password"
              class="form-control"
              placeholder="Contraseña"
              required
            />
          </div>
          <button type="submit" class="btn btn-block">Iniciar Sesión</button>
        </form>
      </div>
    </div>

    <!-- Profile Selection -->
    <div id="profileSelection" class="profile-selection">
      <h2>Seleccionar Perfil</h2>
      <div class="profile-cards" id="profileCards">
        <!-- Profile cards will be dynamically generated -->
      </div>
    </div>

    <!-- Dashboard -->
    <div id="dashboard" class="dashboard">
      <!-- Sidebar -->
      <div class="sidebar" id="sidebar">
        <div class="sidebar-header">
          <h2>Gestión de Almacén</h2>
        </div>
        <div class="user-info">
          <div class="user-avatar" id="userAvatar">U</div>
          <div class="user-details">
            <h3 id="userName">Usuario</h3>
            <p id="userProfile">Perfil</p>
          </div>
        </div>
        <div class="sidebar-menu" id="sidebarMenu">
          <!-- Menu items will be dynamically generated based on profile -->
        </div>
      </div>

      <!-- Main Content -->
      <div class="main-content">
        <div class="header">
          <h1 id="pageTitle">Panel de Control</h1>
          <div class="header-actions">
            <div class="notification-icon">
              <i class="fas fa-bell"></i>
              <span class="notification-badge" id="notificationBadge">3</span>
            </div>
            <button class="btn" id="logoutBtn">
              <i class="fas fa-sign-out-alt"></i> Cerrar Sesión
            </button>
          </div>
        </div>

        <!-- Content Area -->
        <div id="contentArea">
          <!-- Dashboard content will be dynamically loaded here -->
        </div>
      </div>
    </div>

    <!-- Modals -->
    <div class="modal" id="modal">
      <div class="modal-content">
        <div class="modal-header">
          <h3 class="modal-title" id="modalTitle">Modal Title</h3>
          <button class="modal-close" id="modalClose">&times;</button>
        </div>
        <div class="modal-body" id="modalBody">
          <!-- Modal content will be dynamically loaded here -->
        </div>
        <div class="modal-footer" id="modalFooter">
          <!-- Modal footer buttons will be dynamically loaded here -->
        </div>
      </div>
    </div>

    <script>
      // Simulated Database
      const db = {
        users: [
          {
            id: 1,
            email: "admin@example.com",
            password: "admin123",
            name: "Admin User",
            profiles: ["Administrador"],
          },
          {
            id: 2,
            email: "encargado@example.com",
            password: "encargado123",
            name: "Encargado Almacén",
            profiles: ["Encargado de Almacén"],
          },
          {
            id: 3,
            email: "profesor1@example.com",
            password: "profesor123",
            name: "Ana López",
            profiles: ["Profesor"],
          },
          {
            id: 4,
            email: "profesor2@example.com",
            password: "profesor123",
            name: "Carlos Ruiz",
            profiles: ["Profesor"],
          },
        ],
        events: [
          {
            id: 1,
            name: "Pedido Semana 3 Octubre 2025",
            startDate: "2025-10-01",
            endDate: "2025-10-07",
            closeTime: "23:59",
            type: "regular",
            active: true,
          },
          {
            id: 2,
            name: "Semana de la Ciencia",
            startDate: "2025-10-10",
            endDate: "2025-10-17",
            closeTime: "18:00",
            type: "extraordinary",
            active: true,
          },
          {
            id: 3,
            name: "Proyecto Fin de Curso",
            startDate: "2025-05-15",
            endDate: "2025-05-22",
            closeTime: "20:00",
            type: "extraordinary",
            active: false,
          },
        ],
        products: [
          {
            id: 1,
            name: "Leche",
            price: 1.2,
            unit: "litro",
            category: "Lácteos",
            image: "milk",
          },
          {
            id: 2,
            name: "Huevos",
            price: 2.5,
            unit: "docena",
            category: "Lácteos",
            image: "eggs",
          },
          {
            id: 3,
            name: "Harina",
            price: 0.9,
            unit: "kg",
            category: "Despensa",
            image: "flour",
          },
          {
            id: 4,
            name: "Aceite de Oliva",
            price: 4.5,
            unit: "litro",
            category: "Aceites y Grasas",
            image: "oil",
          },
          {
            id: 5,
            name: "Tomates",
            price: 2.0,
            unit: "kg",
            category: "Frutas y Verduras",
            image: "tomato",
          },
          {
            id: 6,
            name: "Pollo",
            price: 5.5,
            unit: "kg",
            category: "Carnes",
            image: "chicken",
          },
          {
            id: 7,
            name: "Arroz",
            price: 1.2,
            unit: "kg",
            category: "Despensa",
            image: "rice",
          },
          {
            id: 8,
            name: "Queso",
            price: 6.0,
            unit: "kg",
            category: "Lácteos",
            image: "cheese",
          },
          {
            id: 9,
            name: "Papel A4",
            price: 4.5,
            unit: "paquete",
            category: "Material de Oficina",
            image: "paper",
          },
          {
            id: 10,
            name: "Bolígrafos",
            price: 8.25,
            unit: "caja",
            category: "Material de Oficina",
            image: "pens",
          },
        ],
        orders: [
          {
            id: 1,
            code: "PED-2024-147",
            date: "2024-03-14",
            professor: "Ana López",
            products: 12,
            status: "Enviado",
            total: 125.3,
          },
          {
            id: 2,
            code: "PED-2024-146",
            date: "2024-03-07",
            professor: "Carlos Ruiz",
            products: 8,
            status: "Procesado",
            total: 98.5,
          },
          {
            id: 3,
            code: "PED-2024-145",
            date: "2024-02-28",
            professor: "Ana López",
            products: 15,
            status: "Cerrado",
            total: 210.75,
          },
        ],
        providers: [
          {
            id: 1,
            name: "Distribuciones Alimentarias S.A.",
            contact: "Juan Pérez",
            phone: "912345678",
            email: "info@distaliment.com",
          },
          {
            id: 2,
            name: "Suministros Hostelería",
            contact: "María García",
            phone: "915678901",
            email: "contacto@sumhost.com",
          },
          {
            id: 3,
            name: "Papelera del Sur",
            contact: "Pedro Martín",
            phone: "917890123",
            email: "ventas@papsur.com",
          },
        ],
        messages: [
          {
            id: 1,
            sender: "Admin User",
            recipients: ["Todos"],
            content:
              "Recordatorio: El pedido semanal cierra el lunes a las 23:59",
            date: "2024-03-15 10:30",
            read: false,
          },
          {
            id: 2,
            sender: "Encargado Almacén",
            recipients: ["Profesores"],
            content: "Nuevos productos disponibles en el catálogo",
            date: "2024-03-14 16:45",
            read: false,
          },
          {
            id: 3,
            sender: "Ana López",
            recipients: ["Encargado de Almacén"],
            content: "Consulta sobre disponibilidad de queso especial",
            date: "2024-03-13 09:15",
            read: true,
          },
        ],
      };

      // Global variables
      let currentUser = null;
      let currentProfile = null;
      let currentOrder = [];
      let currentEvent = null;

      // DOM Elements
      const loginContainer = document.getElementById("loginContainer");
      const profileSelection = document.getElementById("profileSelection");
      const dashboard = document.getElementById("dashboard");
      const loginForm = document.getElementById("loginForm");
      const profileCards = document.getElementById("profileCards");
      const sidebar = document.getElementById("sidebar");
      const sidebarMenu = document.getElementById("sidebarMenu");
      const contentArea = document.getElementById("contentArea");
      const pageTitle = document.getElementById("pageTitle");
      const userAvatar = document.getElementById("userAvatar");
      const userName = document.getElementById("userName");
      const userProfile = document.getElementById("userProfile");
      const logoutBtn = document.getElementById("logoutBtn");
      const modal = document.getElementById("modal");
      const modalTitle = document.getElementById("modalTitle");
      const modalBody = document.getElementById("modalBody");
      const modalFooter = document.getElementById("modalFooter");
      const modalClose = document.getElementById("modalClose");
      const notificationBadge = document.getElementById("notificationBadge");

      // Initialize the app
      function init() {
        loginForm.addEventListener("submit", handleLogin);
        logoutBtn.addEventListener("click", handleLogout);
        modalClose.addEventListener("click", closeModal);

        // Set up notification badge
        updateNotificationBadge();
      }

      // Handle login
      function handleLogin(e) {
        e.preventDefault();
        const email = document.getElementById("email").value;
        const password = document.getElementById("password").value;

        // Find user in database
        const user = db.users.find(
          (u) => u.email === email && u.password === password
        );

        if (user) {
          currentUser = user;
          showProfileSelection(user.profiles);
        } else {
          alert("Credenciales incorrectas. Inténtalo de nuevo.");
        }
      }

      // Show profile selection
      function showProfileSelection(profiles) {
        loginContainer.style.display = "none";
        profileSelection.style.display = "block";

        // Clear existing cards
        profileCards.innerHTML = "";

        // Create profile cards
        profiles.forEach((profile) => {
          const card = document.createElement("div");
          card.className = "profile-card";
          card.dataset.profile = profile;

          let icon = "";
          switch (profile) {
            case "Administrador":
              icon = "fas fa-user-shield";
              break;
            case "Encargado de Almacén":
              icon = "fas fa-warehouse";
              break;
            case "Profesor":
              icon = "fas fa-chalkboard-teacher";
              break;
          }

          card.innerHTML = `
                    <i class="${icon}"></i>
                    <h3>${profile}</h3>
                    <p>Acceder como ${profile}</p>
                `;

          card.addEventListener("click", () => selectProfile(profile));
          profileCards.appendChild(card);
        });
      }

      // Select profile
      function selectProfile(profile) {
        currentProfile = profile;
        profileSelection.style.display = "none";
        dashboard.style.display = "block";

        // Update user info
        userName.textContent = currentUser.name;
        userProfile.textContent = profile;
        userAvatar.textContent = currentUser.name.charAt(0);

        // Set up sidebar menu
        setupSidebarMenu(profile);

        // Load dashboard
        loadDashboard(profile);
      }

      // Set up sidebar menu based on profile
      function setupSidebarMenu(profile) {
        sidebarMenu.innerHTML = "";

        let menuItems = [];

        switch (profile) {
          case "Administrador":
            menuItems = [
              {
                icon: "fas fa-tachometer-alt",
                label: "Panel de Control",
                view: "adminDashboard",
              },
              {
                icon: "fas fa-calendar-alt",
                label: "Gestión de Eventos",
                view: "eventManagement",
              },
              {
                icon: "fas fa-boxes",
                label: "Gestión de Productos",
                view: "productManagement",
              },
              { icon: "fas fa-chart-bar", label: "Reportes", view: "reports" },
              {
                icon: "fas fa-users",
                label: "Gestión de Profesores",
                view: "teacherManagement",
              },
              {
                icon: "fas fa-envelope",
                label: "Mensajes Internos",
                view: "messages",
              },
            ];
            break;
          case "Encargado de Almacén":
            menuItems = [
              {
                icon: "fas fa-tachometer-alt",
                label: "Panel de Control",
                view: "warehouseDashboard",
              },
              {
                icon: "fas fa-clipboard-list",
                label: "Procesamiento de Pedidos",
                view: "orderProcessing",
              },
              {
                icon: "fas fa-truck",
                label: "Gestión de Proveedores",
                view: "providerManagement",
              },
              {
                icon: "fas fa-shipping-fast",
                label: "Seguimiento de Entregas",
                view: "deliveryTracking",
              },
              {
                icon: "fas fa-envelope",
                label: "Mensajes Internos",
                view: "messages",
              },
            ];
            break;
          case "Profesor":
            menuItems = [
              {
                icon: "fas fa-shopping-cart",
                label: "Mis Pedidos",
                view: "teacherOrders",
              },
              {
                icon: "fas fa-history",
                label: "Historial de Pedidos",
                view: "orderHistory",
              },
              {
                icon: "fas fa-calendar-check",
                label: "Eventos",
                view: "teacherEvents",
              },
              {
                icon: "fas fa-envelope",
                label: "Mensajes Internos",
                view: "messages",
              },
            ];
            break;
        }

        menuItems.forEach((item) => {
          const menuItem = document.createElement("a");
          menuItem.className = "menu-item";
          menuItem.dataset.view = item.view;
          menuItem.innerHTML = `<i class="${item.icon}"></i> ${item.label}`;
          menuItem.addEventListener("click", () =>
            loadView(item.view, item.label)
          );
          sidebarMenu.appendChild(menuItem);
        });
      }

      // Load dashboard based on profile
      function loadDashboard(profile) {
        switch (profile) {
          case "Administrador":
            loadAdminDashboard();
            break;
          case "Encargado de Almacén":
            loadWarehouseDashboard();
            break;
          case "Profesor":
            loadTeacherDashboard();
            break;
        }
      }

      // Load admin dashboard
      function loadAdminDashboard() {
        pageTitle.textContent = "Panel de Control - Administrador";

        const stats = [
          {
            title: "Gastos Totales",
            value: "€5,000",
            icon: "fas fa-euro-sign",
            class: "primary",
          },
          {
            title: "Pedidos Procesados",
            value: "50",
            icon: "fas fa-clipboard-check",
            class: "success",
          },
          {
            title: "Profesores Activos",
            value: "34",
            icon: "fas fa-users",
            class: "warning",
          },
          {
            title: "Eventos Activos",
            value: "8",
            icon: "fas fa-calendar-alt",
            class: "danger",
          },
        ];

        const events = db.events.filter((e) => e.active);

        contentArea.innerHTML = `
                <div class="stats-container">
                    ${stats
                      .map(
                        (stat) => `
                        <div class="stat-card">
                            <div class="stat-icon ${stat.class}">
                                <i class="${stat.icon}"></i>
                            </div>
                            <div class="stat-info">
                                <h3>${stat.value}</h3>
                                <p>${stat.title}</p>
                            </div>
                        </div>
                    `
                      )
                      .join("")}
                </div>
                
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Eventos Activos</h3>
                        <button class="btn" onclick="showCreateEventModal()">
                            <i class="fas fa-plus"></i> Crear Nuevo Evento
                        </button>
                    </div>
                    <div class="card-body">
                        <div class="table-responsive">
                            <table class="table">
                                <thead>
                                    <tr>
                                        <th>Nombre</th>
                                        <th>Fecha Apertura</th>
                                        <th>Fecha Cierre</th>
                                        <th>Hora Cierre</th>
                                        <th>Tipo</th>
                                        <th>Estado</th>
                                        <th>Acciones</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    ${events
                                      .map(
                                        (event) => `
                                        <tr>
                                            <td>${event.name}</td>
                                            <td>${event.startDate}</td>
                                            <td>${event.endDate}</td>
                                            <td>${event.closeTime}</td>
                                            <td>${
                                              event.type === "regular"
                                                ? "Regular"
                                                : "Extraordinario"
                                            }</td>
                                            <td><span class="badge badge-success">Activo</span></td>
                                            <td>
                                                <div class="btn-group">
                                                    <button class="btn btn-sm" onclick="editEvent(${
                                                      event.id
                                                    })">
                                                        <i class="fas fa-edit"></i>
                                                    </button>
                                                    <button class="btn btn-sm btn-danger" onclick="toggleEventStatus(${
                                                      event.id
                                                    })">
                                                        <i class="fas fa-toggle-on"></i>
                                                    </button>
                                                </div>
                                            </td>
                                        </tr>
                                    `
                                      )
                                      .join("")}
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
                
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Notificaciones</h3>
                    </div>
                    <div class="card-body">
                        <div class="alert alert-warning">
                            <i class="fas fa-exclamation-triangle"></i> Tienes 2 mensajes no leídos
                        </div>
                        <div class="alert alert-success">
                            <i class="fas fa-check-circle"></i> El pedido semanal se ha procesado correctamente
                        </div>
                    </div>
                </div>
            `;
      }

      // Load warehouse dashboard
      function loadWarehouseDashboard() {
        pageTitle.textContent = "Panel de Control - Encargado de Almacén";

        const stats = [
          {
            title: "Pedidos Pendientes",
            value: "12",
            icon: "fas fa-clipboard-list",
            class: "warning",
          },
          {
            title: "Pedidos Procesados",
            value: "38",
            icon: "fas fa-check-circle",
            class: "success",
          },
          {
            title: "Proveedores Activos",
            value: "15",
            icon: "fas fa-truck",
            class: "primary",
          },
          {
            title: "Entregas Hoy",
            value: "5",
            icon: "fas fa-shipping-fast",
            class: "danger",
          },
        ];

        const pendingOrders = db.orders.filter((o) => o.status === "Enviado");

        contentArea.innerHTML = `
                <div class="stats-container">
                    ${stats
                      .map(
                        (stat) => `
                        <div class="stat-card">
                            <div class="stat-icon ${stat.class}">
                                <i class="${stat.icon}"></i>
                            </div>
                            <div class="stat-info">
                                <h3>${stat.value}</h3>
                                <p>${stat.title}</p>
                            </div>
                        </div>
                    `
                      )
                      .join("")}
                </div>
                
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Pedidos Pendientes de Procesar</h3>
                    </div>
                    <div class="card-body">
                        <div class="table-responsive">
                            <table class="table">
                                <thead>
                                    <tr>
                                        <th>Código</th>
                                        <th>Fecha</th>
                                        <th>Profesor</th>
                                        <th>Productos</th>
                                        <th>Total</th>
                                        <th>Estado</th>
                                        <th>Acciones</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    ${pendingOrders
                                      .map(
                                        (order) => `
                                        <tr>
                                            <td>${order.code}</td>
                                            <td>${order.date}</td>
                                            <td>${order.professor}</td>
                                            <td>${order.products}</td>
                                            <td>€${order.total.toFixed(2)}</td>
                                            <td><span class="badge badge-warning">${
                                              order.status
                                            }</span></td>
                                            <td>
                                                <div class="btn-group">
                                                    <button class="btn btn-sm btn-success" onclick="processOrder(${
                                                      order.id
                                                    })">
                                                        <i class="fas fa-check"></i> Procesar
                                                    </button>
                                                    <button class="btn btn-sm" onclick="viewOrderDetails(${
                                                      order.id
                                                    })">
                                                        <i class="fas fa-eye"></i>
                                                    </button>
                                                </div>
                                            </td>
                                        </tr>
                                    `
                                      )
                                      .join("")}
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
                
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Próximas Entregas</h3>
                    </div>
                    <div class="card-body">
                        <div class="table-responsive">
                            <table class="table">
                                <thead>
                                    <tr>
                                        <th>Proveedor</th>
                                        <th>Fecha Estimada</th>
                                        <th>Productos</th>
                                        <th>Estado</th>
                                        <th>Acciones</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr>
                                        <td>Distribuciones Alimentarias S.A.</td>
                                        <td>2024-03-18</td>
                                        <td>15</td>
                                        <td>
                                            <div class="delivery-status">
                                                <div class="status-indicator processing"></div>
                                                En proceso
                                            </div>
                                        </td>
                                        <td>
                                            <button class="btn btn-sm" onclick="trackDelivery(1)">
                                                <i class="fas fa-map-marker-alt"></i> Seguir
                                            </button>
                                        </td>
                                    </tr>
                                    <tr>
                                        <td>Suministros Hostelería</td>
                                        <td>2024-03-19</td>
                                        <td>8</td>
                                        <td>
                                            <div class="delivery-status">
                                                <div class="status-indicator pending"></div>
                                                Pendiente
                                            </div>
                                        </td>
                                        <td>
                                            <button class="btn btn-sm" onclick="trackDelivery(2)">
                                                <i class="fas fa-map-marker-alt"></i> Seguir
                                            </button>
                                        </td>
                                    </tr>
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            `;
      }

      // Load teacher dashboard
      function loadTeacherDashboard() {
        pageTitle.textContent = "Panel de Control - Profesor";

        const activeEvents = db.events.filter((e) => e.active);
        const recentOrders = db.orders
          .filter((o) => o.professor === currentUser.name)
          .slice(0, 3);

        contentArea.innerHTML = `
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Presupuesto</h3>
                    </div>
                    <div class="card-body">
                        <div class="stats-container">
                            <div class="stat-card">
                                <div class="stat-icon primary">
                                    <i class="fas fa-euro-sign"></i>
                                </div>
                                <div class="stat-info">
                                    <h3>€250.00</h3>
                                    <p>Presupuesto Asignado</p>
                                </div>
                            </div>
                            <div class="stat-card">
                                <div class="stat-icon warning">
                                    <i class="fas fa-shopping-cart"></i>
                                </div>
                                <div class="stat-info">
                                    <h3>€125.30</h3>
                                    <p>Gasto del Mes</p>
                                </div>
                            </div>
                            <div class="stat-card">
                                <div class="stat-icon success">
                                    <i class="fas fa-piggy-bank"></i>
                                </div>
                                <div class="stat-info">
                                    <h3>€124.70</h3>
                                    <p>Disponible</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Pedidos Recientes</h3>
                        <button class="btn" onclick="createNewOrder()">
                            <i class="fas fa-plus"></i> Nuevo Pedido
                        </button>
                    </div>
                    <div class="card-body">
                        <div class="table-responsive">
                            <table class="table">
                                <thead>
                                    <tr>
                                        <th>Código</th>
                                        <th>Fecha</th>
                                        <th>Productos</th>
                                        <th>Total</th>
                                        <th>Estado</th>
                                        <th>Acciones</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    ${recentOrders
                                      .map(
                                        (order) => `
                                        <tr>
                                            <td>${order.code}</td>
                                            <td>${order.date}</td>
                                            <td>${order.products}</td>
                                            <td>€${order.total.toFixed(2)}</td>
                                            <td><span class="badge badge-${
                                              order.status === "Enviado"
                                                ? "warning"
                                                : order.status === "Procesado"
                                                ? "primary"
                                                : "success"
                                            }">${order.status}</span></td>
                                            <td>
                                                <div class="btn-group">
                                                    <button class="btn btn-sm" onclick="viewOrderDetails(${
                                                      order.id
                                                    })">
                                                        <i class="fas fa-eye"></i>
                                                    </button>
                                                    ${
                                                      order.status === "Enviado"
                                                        ? `<button class="btn btn-sm btn-danger" onclick="cancelOrder(${order.id})"><i class="fas fa-times"></i></button>`
                                                        : ""
                                                    }
                                                </div>
                                            </td>
                                        </tr>
                                    `
                                      )
                                      .join("")}
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
                
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Eventos Activos</h3>
                    </div>
                    <div class="card-body">
                        <div class="stats-container">
                            ${activeEvents
                              .map(
                                (event) => `
                                <div class="stat-card">
                                    <div class="stat-icon primary">
                                        <i class="fas fa-calendar-alt"></i>
                                    </div>
                                    <div class="stat-info">
                                        <h3>${event.name}</h3>
                                        <p>Hasta ${event.endDate} - ${event.closeTime}</p>
                                        <button class="btn btn-sm" onclick="createEventOrder(${event.id})">
                                            <i class="fas fa-plus"></i> Añadir Pedido
                                        </button>
                                    </div>
                                </div>
                            `
                              )
                              .join("")}
                        </div>
                    </div>
                </div>
                
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Próximas Fechas Límite</h3>
                    </div>
                    <div class="card-body">
                        <div class="alert alert-warning">
                            <i class="fas fa-exclamation-triangle"></i> El pedido semanal cierra el lunes 23/03 a las 23:59
                        </div>
                        <div class="alert alert-info">
                            <i class="fas fa-info-circle"></i> El evento "Semana de la Ciencia" cierra el viernes 27/03 a las 18:00
                        </div>
                    </div>
                </div>
            `;
      }

      // Load view based on profile and selection
      function loadView(view, title) {
        pageTitle.textContent = title;

        // Update active menu item
        document.querySelectorAll(".menu-item").forEach((item) => {
          item.classList.remove("active");
          if (item.dataset.view === view) {
            item.classList.add("active");
          }
        });

        // Load specific view
        switch (view) {
          case "eventManagement":
            loadEventManagement();
            break;
          case "productManagement":
            loadProductManagement();
            break;
          case "teacherManagement":
            loadTeacherManagement();
            break;
          case "reports":
            loadReports();
            break;
          case "orderProcessing":
            loadOrderProcessing();
            break;
          case "providerManagement":
            loadProviderManagement();
            break;
          case "deliveryTracking":
            loadDeliveryTracking();
            break;
          case "teacherOrders":
            loadTeacherOrders();
            break;
          case "orderHistory":
            loadOrderHistory();
            break;
          case "teacherEvents":
            loadTeacherEvents();
            break;
          case "messages":
            loadMessages();
            break;
          default:
            loadDashboard(currentProfile);
        }
      }

      // Load event management view
      function loadEventManagement() {
        const events = db.events;

        contentArea.innerHTML = `
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Gestión de Eventos</h3>
                        <button class="btn" onclick="showCreateEventModal()">
                            <i class="fas fa-plus"></i> Crear Nuevo Evento
                        </button>
                    </div>
                    <div class="card-body">
                        <div class="tabs">
                            <div class="tab active" onclick="switchTab('regular-events')">Eventos Regulares</div>
                            <div class="tab" onclick="switchTab('extraordinary-events')">Eventos Extraordinarios</div>
                        </div>
                        
                        <div id="regular-events" class="tab-content active">
                            <div class="table-responsive">
                                <table class="table">
                                    <thead>
                                        <tr>
                                            <th>Nombre</th>
                                            <th>Fecha Apertura</th>
                                            <th>Fecha Cierre</th>
                                            <th>Hora Cierre</th>
                                            <th>Estado</th>
                                            <th>Acciones</th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        ${events
                                          .filter((e) => e.type === "regular")
                                          .map(
                                            (event) => `
                                            <tr>
                                                <td>${event.name}</td>
                                                <td>${event.startDate}</td>
                                                <td>${event.endDate}</td>
                                                <td>${event.closeTime}</td>
                                                <td><span class="badge badge-${
                                                  event.active
                                                    ? "success"
                                                    : "danger"
                                                }">${
                                              event.active
                                                ? "Activo"
                                                : "Inactivo"
                                            }</span></td>
                                                <td>
                                                    <div class="btn-group">
                                                        <button class="btn btn-sm" onclick="editEvent(${
                                                          event.id
                                                        })">
                                                            <i class="fas fa-edit"></i>
                                                        </button>
                                                        <button class="btn btn-sm btn-${
                                                          event.active
                                                            ? "danger"
                                                            : "success"
                                                        }" onclick="toggleEventStatus(${
                                              event.id
                                            })">
                                                            <i class="fas fa-toggle-${
                                                              event.active
                                                                ? "on"
                                                                : "off"
                                                            }"></i>
                                                        </button>
                                                    </div>
                                                </td>
                                            </tr>
                                        `
                                          )
                                          .join("")}
                                    </tbody>
                                </table>
                            </div>
                        </div>
                        
                        <div id="extraordinary-events" class="tab-content">
                            <div class="table-responsive">
                                <table class="table">
                                    <thead>
                                        <tr>
                                            <th>Nombre</th>
                                            <th>Fecha Apertura</th>
                                            <th>Fecha Cierre</th>
                                            <th>Hora Cierre</th>
                                            <th>Estado</th>
                                            <th>Acciones</th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        ${events
                                          .filter(
                                            (e) => e.type === "extraordinary"
                                          )
                                          .map(
                                            (event) => `
                                            <tr>
                                                <td>${event.name}</td>
                                                <td>${event.startDate}</td>
                                                <td>${event.endDate}</td>
                                                <td>${event.closeTime}</td>
                                                <td><span class="badge badge-${
                                                  event.active
                                                    ? "success"
                                                    : "danger"
                                                }">${
                                              event.active
                                                ? "Activo"
                                                : "Inactivo"
                                            }</span></td>
                                                <td>
                                                    <div class="btn-group">
                                                        <button class="btn btn-sm" onclick="editEvent(${
                                                          event.id
                                                        })">
                                                            <i class="fas fa-edit"></i>
                                                        </button>
                                                        <button class="btn btn-sm btn-${
                                                          event.active
                                                            ? "danger"
                                                            : "success"
                                                        }" onclick="toggleEventStatus(${
                                              event.id
                                            })">
                                                            <i class="fas fa-toggle-${
                                                              event.active
                                                                ? "on"
                                                                : "off"
                                                            }"></i>
                                                        </button>
                                                    </div>
                                                </td>
                                            </tr>
                                        `
                                          )
                                          .join("")}
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Calendario de Eventos</h3>
                    </div>
                    <div class="card-body">
                        <div class="event-calendar">
                            <div class="calendar-day-header">Lun</div>
                            <div class="calendar-day-header">Mar</div>
                            <div class="calendar-day-header">Mié</div>
                            <div class="calendar-day-header">Jue</div>
                            <div class="calendar-day-header">Vie</div>
                            <div class="calendar-day-header">Sáb</div>
                            <div class="calendar-day-header">Dom</div>
                            
                            <!-- Calendar days will be dynamically generated -->
                            ${generateCalendarDays()}
                        </div>
                    </div>
                </div>
            `;
      }

      // Generate calendar days with events
      function generateCalendarDays() {
        let days = "";
        const today = new Date();
        const currentMonth = today.getMonth();
        const currentYear = today.getFullYear();
        const daysInMonth = new Date(
          currentYear,
          currentMonth + 1,
          0
        ).getDate();
        const firstDay = new Date(currentYear, currentMonth, 1).getDay();

        // Empty cells for days before month starts
        for (let i = 0; i < (firstDay === 0 ? 6 : firstDay - 1); i++) {
          days += '<div class="calendar-day"></div>';
        }

        // Days of the month
        for (let day = 1; day <= daysInMonth; day++) {
          const dateStr = `${currentYear}-${String(currentMonth + 1).padStart(
            2,
            "0"
          )}-${String(day).padStart(2, "0")}`;
          const dayEvents = db.events.filter(
            (e) => e.startDate <= dateStr && e.endDate >= dateStr
          );

          days += `
                    <div class="calendar-day">
                        <div class="calendar-day-number">${day}</div>
                        ${dayEvents
                          .map(
                            (event) => `
                            <div class="calendar-event">${event.name}</div>
                        `
                          )
                          .join("")}
                    </div>
                `;
        }

        return days;
      }

      // Load product management view
      function loadProductManagement() {
        const products = db.products;
        const categories = [...new Set(products.map((p) => p.category))];

        contentArea.innerHTML = `
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Gestión de Productos</h3>
                        <button class="btn" onclick="showAddProductModal()">
                            <i class="fas fa-plus"></i> Añadir Producto
                        </button>
                    </div>
                    <div class="card-body">
                        <div class="filter-container">
                            <div class="filter-group">
                                <select class="form-control" id="categoryFilter" onchange="filterProducts()">
                                    <option value="">Todas las Categorías</option>
                                    ${categories
                                      .map(
                                        (cat) =>
                                          `<option value="${cat}">${cat}</option>`
                                      )
                                      .join("")}
                                </select>
                            </div>
                            <div class="filter-group">
                                <input type="text" class="form-control" id="productSearch" placeholder="Buscar productos..." onkeyup="filterProducts()">
                            </div>
                        </div>
                        
                        <div class="product-list" id="productList">
                            ${products
                              .map(
                                (product) => `
                                <div class="product-item" data-category="${
                                  product.category
                                }" data-name="${product.name.toLowerCase()}">
                                    <div class="product-image">
                                        <i class="fas fa-box"></i>
                                    </div>
                                    <div class="product-name">${
                                      product.name
                                    }</div>
                                    <div class="product-price">€${product.price.toFixed(
                                      2
                                    )} / ${product.unit}</div>
                                    <div class="btn-group" style="margin-top: 10px;">
                                        <button class="btn btn-sm" onclick="editProduct(${
                                          product.id
                                        })">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                        <button class="btn btn-sm btn-danger" onclick="deleteProduct(${
                                          product.id
                                        })">
                                            <i class="fas fa-trash"></i>
                                        </button>
                                    </div>
                                </div>
                            `
                              )
                              .join("")}
                        </div>
                    </div>
                </div>
            `;
      }

      // Load teacher management view
      function loadTeacherManagement() {
        const teachers = db.users.filter((u) =>
          u.profiles.includes("Profesor")
        );

        contentArea.innerHTML = `
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Gestión de Profesores</h3>
                        <button class="btn" onclick="showAddTeacherModal()">
                            <i class="fas fa-plus"></i> Añadir Profesor
                        </button>
                    </div>
                    <div class="card-body">
                        <div class="table-responsive">
                            <table class="table">
                                <thead>
                                    <tr>
                                        <th>Nombre</th>
                                        <th>Email</th>
                                        <th>Estado</th>
                                        <th>Acciones</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    ${teachers
                                      .map(
                                        (teacher) => `
                                        <tr>
                                            <td>${teacher.name}</td>
                                            <td>${teacher.email}</td>
                                            <td><span class="badge badge-success">Activo</span></td>
                                            <td>
                                                <div class="btn-group">
                                                    <button class="btn btn-sm" onclick="editTeacher(${teacher.id})">
                                                        <i class="fas fa-edit"></i>
                                                    </button>
                                                    <button class="btn btn-sm btn-danger" onclick="resetTeacherPassword(${teacher.id})">
                                                        <i class="fas fa-key"></i>
                                                    </button>
                                                </div>
                                            </td>
                                        </tr>
                                    `
                                      )
                                      .join("")}
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            `;
      }

      // Load reports view
      function loadReports() {
        contentArea.innerHTML = `
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Reportes y Estadísticas</h3>
                    </div>
                    <div class="card-body">
                        <div class="tabs">
                            <div class="tab active" onclick="switchTab('monthly-report')">Reporte Mensual</div>
                            <div class="tab" onclick="switchTab('annual-report')">Reporte Anual</div>
                            <div class="tab" onclick="switchTab('event-report')">Reporte por Evento</div>
                        </div>
                        
                        <div id="monthly-report" class="tab-content active">
                            <div class="form-row">
                                <div class="form-col">
                                    <select class="form-control">
                                        <option>Enero 2024</option>
                                        <option>Febrero 2024</option>
                                        <option selected>Marzo 2024</option>
                                        <option>Abril 2024</option>
                                    </select>
                                </div>
                                <div class="form-col">
                                    <button class="btn" onclick="generateReport('monthly')">
                                        <i class="fas fa-file-pdf"></i> Generar PDF
                                    </button>
                                    <button class="btn" onclick="generateReport('monthly', 'excel')">
                                        <i class="fas fa-file-excel"></i> Generar Excel
                                    </button>
                                </div>
                            </div>
                            
                            <div class="stats-container">
                                <div class="stat-card">
                                    <div class="stat-icon primary">
                                        <i class="fas fa-euro-sign"></i>
                                    </div>
                                    <div class="stat-info">
                                        <h3>€1,250.75</h3>
                                        <p>Gasto Total</p>
                                    </div>
                                </div>
                                <div class="stat-card">
                                    <div class="stat-icon success">
                                        <i class="fas fa-shopping-cart"></i>
                                    </div>
                                    <div class="stat-info">
                                        <h3>42</h3>
                                        <p>Pedidos Realizados</p>
                                    </div>
                                </div>
                                <div class="stat-card">
                                    <div class="stat-icon warning">
                                        <i class="fas fa-users"></i>
                                    </div>
                                    <div class="stat-info">
                                        <h3>28</h3>
                                        <p>Profesores Activos</p>
                                    </div>
                                </div>
                            </div>
                            
                            <div style="height: 300px; background: #f8f9fa; border-radius: 5px; display: flex; align-items: center; justify-content: center; margin-top: 20px;">
                                <p>Gráfico de gastos por categoría</p>
                            </div>
                        </div>
                        
                        <div id="annual-report" class="tab-content">
                            <div class="form-row">
                                <div class="form-col">
                                    <select class="form-control">
                                        <option>2023-2024</option>
                                        <option selected>2024-2025</option>
                                    </select>
                                </div>
                                <div class="form-col">
                                    <button class="btn" onclick="generateReport('annual')">
                                        <i class="fas fa-file-pdf"></i> Generar PDF
                                    </button>
                                    <button class="btn" onclick="generateReport('annual', 'excel')">
                                        <i class="fas fa-file-excel"></i> Generar Excel
                                    </button>
                                </div>
                            </div>
                            
                            <div class="stats-container">
                                <div class="stat-card">
                                    <div class="stat-icon primary">
                                        <i class="fas fa-euro-sign"></i>
                                    </div>
                                    <div class="stat-info">
                                        <h3>€15,250.75</h3>
                                        <p>Gasto Total del Curso</p>
                                    </div>
                                </div>
                                <div class="stat-card">
                                    <div class="stat-icon success">
                                        <i class="fas fa-shopping-cart"></i>
                                    </div>
                                    <div class="stat-info">
                                        <h3>312</h3>
                                        <p>Pedidos Realizados</p>
                                    </div>
                                </div>
                                <div class="stat-card">
                                    <div class="stat-icon warning">
                                        <i class="fas fa-calendar-alt"></i>
                                    </div>
                                    <div class="stat-info">
                                        <h3>24</h3>
                                        <p>Eventos Realizados</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div id="event-report" class="tab-content">
                            <div class="form-row">
                                <div class="form-col">
                                    <select class="form-control">
                                        ${db.events
                                          .map(
                                            (event) =>
                                              `<option value="${event.id}">${event.name}</option>`
                                          )
                                          .join("")}
                                    </select>
                                </div>
                                <div class="form-col">
                                    <button class="btn" onclick="generateReport('event')">
                                        <i class="fas fa-file-pdf"></i> Generar PDF
                                    </button>
                                    <button class="btn" onclick="generateReport('event', 'excel')">
                                        <i class="fas fa-file-excel"></i> Generar Excel
                                    </button>
                                </div>
                            </div>
                            
                            <div class="stats-container">
                                <div class="stat-card">
                                    <div class="stat-icon primary">
                                        <i class="fas fa-euro-sign"></i>
                                    </div>
                                    <div class="stat-info">
                                        <h3>€850.25</h3>
                                        <p>Gasto del Evento</p>
                                    </div>
                                </div>
                                <div class="stat-card">
                                    <div class="stat-icon success">
                                        <i class="fas fa-shopping-cart"></i>
                                    </div>
                                    <div class="stat-info">
                                        <h3>18</h3>
                                        <p>Pedidos Realizados</p>
                                    </div>
                                </div>
                                <div class="stat-card">
                                    <div class="stat-icon warning">
                                        <i class="fas fa-users"></i>
                                    </div>
                                    <div class="stat-info">
                                        <h3>12</h3>
                                        <p>Profesores Participantes</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            `;
      }

      // Load order processing view
      function loadOrderProcessing() {
        const pendingOrders = db.orders.filter((o) => o.status === "Enviado");

        contentArea.innerHTML = `
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Procesamiento de Pedidos</h3>
                    </div>
                    <div class="card-body">
                        <div class="table-responsive">
                            <table class="table">
                                <thead>
                                    <tr>
                                        <th>Código</th>
                                        <th>Fecha</th>
                                        <th>Profesor</th>
                                        <th>Productos</th>
                                        <th>Total</th>
                                        <th>Estado</th>
                                        <th>Acciones</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    ${pendingOrders
                                      .map(
                                        (order) => `
                                        <tr>
                                            <td>${order.code}</td>
                                            <td>${order.date}</td>
                                            <td>${order.professor}</td>
                                            <td>${order.products}</td>
                                            <td>€${order.total.toFixed(2)}</td>
                                            <td><span class="badge badge-warning">${
                                              order.status
                                            }</span></td>
                                            <td>
                                                <div class="btn-group">
                                                    <button class="btn btn-sm btn-success" onclick="processOrder(${
                                                      order.id
                                                    })">
                                                        <i class="fas fa-check"></i> Procesar
                                                    </button>
                                                    <button class="btn btn-sm" onclick="viewOrderDetails(${
                                                      order.id
                                                    })">
                                                        <i class="fas fa-eye"></i> Ver Detalles
                                                    </button>
                                                </div>
                                            </td>
                                        </tr>
                                    `
                                      )
                                      .join("")}
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            `;
      }

      // Load provider management view
      function loadProviderManagement() {
        const providers = db.providers;

        contentArea.innerHTML = `
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Gestión de Proveedores</h3>
                        <button class="btn" onclick="showAddProviderModal()">
                            <i class="fas fa-plus"></i> Añadir Proveedor
                        </button>
                    </div>
                    <div class="card-body">
                        <div class="table-responsive">
                            <table class="table">
                                <thead>
                                    <tr>
                                        <th>Nombre</th>
                                        <th>Contacto</th>
                                        <th>Teléfono</th>
                                        <th>Email</th>
                                        <th>Acciones</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    ${providers
                                      .map(
                                        (provider) => `
                                        <tr>
                                            <td>${provider.name}</td>
                                            <td>${provider.contact}</td>
                                            <td>${provider.phone}</td>
                                            <td>${provider.email}</td>
                                            <td>
                                                <div class="btn-group">
                                                    <button class="btn btn-sm" onclick="editProvider(${provider.id})">
                                                        <i class="fas fa-edit"></i>
                                                    </button>
                                                    <button class="btn btn-sm btn-danger" onclick="deleteProvider(${provider.id})">
                                                        <i class="fas fa-trash"></i>
                                                    </button>
                                                </div>
                                            </td>
                                        </tr>
                                    `
                                      )
                                      .join("")}
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            `;
      }

      // Load delivery tracking view
      function loadDeliveryTracking() {
        contentArea.innerHTML = `
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Seguimiento de Entregas</h3>
                    </div>
                    <div class="card-body">
                        <div class="table-responsive">
                            <table class="table">
                                <thead>
                                    <tr>
                                        <th>Pedido</th>
                                        <th>Proveedor</th>
                                        <th>Fecha Estimada</th>
                                        <th>Productos</th>
                                        <th>Estado</th>
                                        <th>Acciones</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr>
                                        <td>PED-2024-150</td>
                                        <td>Distribuciones Alimentarias S.A.</td>
                                        <td>2024-03-18</td>
                                        <td>15</td>
                                        <td>
                                            <div class="delivery-status">
                                                <div class="status-indicator processing"></div>
                                                En proceso
                                            </div>
                                        </td>
                                        <td>
                                            <button class="btn btn-sm" onclick="trackDelivery(1)">
                                                <i class="fas fa-map-marker-alt"></i> Seguir
                                            </button>
                                        </td>
                                    </tr>
                                    <tr>
                                        <td>PED-2024-151</td>
                                        <td>Suministros Hostelería</td>
                                        <td>2024-03-19</td>
                                        <td>8</td>
                                        <td>
                                            <div class="delivery-status">
                                                <div class="status-indicator pending"></div>
                                                Pendiente
                                            </div>
                                        </td>
                                        <td>
                                            <button class="btn btn-sm" onclick="trackDelivery(2)">
                                                <i class="fas fa-map-marker-alt"></i> Seguir
                                            </button>
                                        </td>
                                    </tr>
                                    <tr>
                                        <td>PED-2024-148</td>
                                        <td>Papelera del Sur</td>
                                        <td>2024-03-17</td>
                                        <td>5</td>
                                        <td>
                                            <div class="delivery-status">
                                                <div class="status-indicator completed"></div>
                                                Completado
                                            </div>
                                        </td>
                                        <td>
                                            <button class="btn btn-sm" onclick="viewDeliveryDetails(3)">
                                                <i class="fas fa-eye"></i> Ver Detalles
                                            </button>
                                        </td>
                                    </tr>
                                    <tr>
                                        <td>PED-2024-149</td>
                                        <td>Distribuciones Alimentarias S.A.</td>
                                        <td>2024-03-16</td>
                                        <td>12</td>
                                        <td>
                                            <div class="delivery-status">
                                                <div class="status-indicator delayed"></div>
                                                Retrasado
                                            </div>
                                        </td>
                                        <td>
                                            <button class="btn btn-sm" onclick="trackDelivery(4)">
                                                <i class="fas fa-map-marker-alt"></i> Seguir
                                            </button>
                                        </td>
                                    </tr>
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            `;
      }

      // Load teacher orders view
      function loadTeacherOrders() {
        const activeEvents = db.events.filter((e) => e.active);

        contentArea.innerHTML = `
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Realizar Nuevo Pedido</h3>
                    </div>
                    <div class="card-body">
                        <div class="alert alert-info">
                            <i class="fas fa-info-circle"></i> Período activo: hasta 20/03 - 23:59
                        </div>
                        
                        <div class="form-row">
                            <div class="form-col">
                                <label>Seleccionar Evento (opcional)</label>
                                <select class="form-control" id="eventSelect">
                                    <option value="">Ninguno (pedido regular)</option>
                                    ${activeEvents
                                      .map(
                                        (event) =>
                                          `<option value="${event.id}">${event.name}</option>`
                                      )
                                      .join("")}
                                </select>
                            </div>
                            <div class="form-col">
                                <label>Grupo Destinatario</label>
                                <select class="form-control">
                                    <option>DAM-2A</option>
                                    <option>DAM-2B</option>
                                    <option>ASIR-1A</option>
                                </select>
                            </div>
                        </div>
                        
                        <h4 style="margin: 20px 0 10px;">Productos Disponibles</h4>
                        
                        <div class="filter-container">
                            <div class="filter-group">
                                <select class="form-control" id="categoryFilter" onchange="filterProductsForOrder()">
                                    <option value="">Todas las Categorías</option>
                                    ${[
                                      ...new Set(
                                        db.products.map((p) => p.category)
                                      ),
                                    ]
                                      .map(
                                        (cat) =>
                                          `<option value="${cat}">${cat}</option>`
                                      )
                                      .join("")}
                                </select>
                            </div>
                            <div class="filter-group">
                                <input type="text" class="form-control" id="productSearch" placeholder="Buscar productos..." onkeyup="filterProductsForOrder()">
                            </div>
                        </div>
                        
                        <div class="product-list" id="productListForOrder">
                            ${db.products
                              .map(
                                (product) => `
                                <div class="product-item" data-category="${
                                  product.category
                                }" data-name="${product.name.toLowerCase()}" onclick="addProductToOrder(${
                                  product.id
                                })">
                                    <div class="product-image">
                                        <i class="fas fa-box"></i>
                                    </div>
                                    <div class="product-name">${
                                      product.name
                                    }</div>
                                    <div class="product-price">€${product.price.toFixed(
                                      2
                                    )} / ${product.unit}</div>
                                </div>
                            `
                              )
                              .join("")}
                        </div>
                        
                        <div class="order-summary">
                            <h4>Pedido Actual</h4>
                            <div id="orderItems">
                                <p>No hay productos en el pedido</p>
                            </div>
                            <div class="order-item">
                                <span>Total:</span>
                                <span id="orderTotal">€0.00</span>
                            </div>
                            <div style="margin-top: 20px;">
                                <button class="btn btn-success" onclick="submitOrder()">
                                    <i class="fas fa-paper-plane"></i> Enviar Pedido
                                </button>
                                <button class="btn" onclick="saveOrderDraft()">
                                    <i class="fas fa-save"></i> Guardar Borrador
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            `;
      }

      // Load order history view
      function loadOrderHistory() {
        const orders = db.orders.filter(
          (o) => o.professor === currentUser.name
        );

        contentArea.innerHTML = `
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Historial de Pedidos</h3>
                    </div>
                    <div class="card-body">
                        <div class="filter-container">
                            <div class="filter-group">
                                <select class="form-control">
                                    <option value="">Todos los Estados</option>
                                    <option value="Enviado">Enviado</option>
                                    <option value="Procesado">Procesado</option>
                                    <option value="Cerrado">Cerrado</option>
                                </select>
                            </div>
                            <div class="filter-group">
                                <select class="form-control">
                                    <option value="">Todos los Eventos</option>
                                    ${db.events
                                      .map(
                                        (event) =>
                                          `<option value="${event.id}">${event.name}</option>`
                                      )
                                      .join("")}
                                </select>
                            </div>
                            <div class="filter-group">
                                <input type="month" class="form-control" value="2024-03">
                            </div>
                        </div>
                        
                        <div class="table-responsive">
                            <table class="table">
                                <thead>
                                    <tr>
                                        <th>Código</th>
                                        <th>Fecha</th>
                                        <th>Productos</th>
                                        <th>Total</th>
                                        <th>Estado</th>
                                        <th>Acciones</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    ${orders
                                      .map(
                                        (order) => `
                                        <tr>
                                            <td>${order.code}</td>
                                            <td>${order.date}</td>
                                            <td>${order.products}</td>
                                            <td>€${order.total.toFixed(2)}</td>
                                            <td><span class="badge badge-${
                                              order.status === "Enviado"
                                                ? "warning"
                                                : order.status === "Procesado"
                                                ? "primary"
                                                : "success"
                                            }">${order.status}</span></td>
                                            <td>
                                                <div class="btn-group">
                                                    <button class="btn btn-sm" onclick="viewOrderDetails(${
                                                      order.id
                                                    })">
                                                        <i class="fas fa-eye"></i> Ver
                                                    </button>
                                                    <button class="btn btn-sm" onclick="downloadOrder(${
                                                      order.id
                                                    })">
                                                        <i class="fas fa-download"></i> Descargar
                                                    </button>
                                                    ${
                                                      order.status === "Enviado"
                                                        ? `<button class="btn btn-sm btn-danger" onclick="cancelOrder(${order.id})"><i class="fas fa-times"></i> Cancelar</button>`
                                                        : ""
                                                    }
                                                </div>
                                            </td>
                                        </tr>
                                    `
                                      )
                                      .join("")}
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            `;
      }

      // Load teacher events view
      function loadTeacherEvents() {
        const events = db.events.filter((e) => e.active);

        contentArea.innerHTML = `
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Eventos Activos</h3>
                    </div>
                    <div class="card-body">
                        <div class="stats-container">
                            ${events
                              .map(
                                (event) => `
                                <div class="stat-card">
                                    <div class="stat-icon primary">
                                        <i class="fas fa-calendar-alt"></i>
                                    </div>
                                    <div class="stat-info">
                                        <h3>${event.name}</h3>
                                        <p>Hasta ${event.endDate} - ${event.closeTime}</p>
                                        <button class="btn btn-sm" onclick="createEventOrder(${event.id})">
                                            <i class="fas fa-plus"></i> Añadir Pedido
                                        </button>
                                    </div>
                                </div>
                            `
                              )
                              .join("")}
                        </div>
                    </div>
                </div>
                
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Historial de Eventos</h3>
                    </div>
                    <div class="card-body">
                        <div class="table-responsive">
                            <table class="table">
                                <thead>
                                    <tr>
                                        <th>Nombre</th>
                                        <th>Fecha</th>
                                        <th>Mi Pedido</th>
                                        <th>Total</th>
                                        <th>Estado</th>
                                        <th>Acciones</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    ${db.events
                                      .filter((e) => !e.active)
                                      .map(
                                        (event) => `
                                        <tr>
                                            <td>${event.name}</td>
                                            <td>${event.startDate} - ${event.endDate}</td>
                                            <td>8 productos</td>
                                            <td>€125.50</td>
                                            <td><span class="badge badge-success">Completado</span></td>
                                            <td>
                                                <button class="btn btn-sm" onclick="viewEventDetails(${event.id})">
                                                    <i class="fas fa-eye"></i> Ver
                                                </button>
                                            </td>
                                        </tr>
                                    `
                                      )
                                      .join("")}
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            `;
      }

      // Load messages view
      function loadMessages() {
        const messages = db.messages;
        const unreadCount = messages.filter((m) => !m.read).length;

        contentArea.innerHTML = `
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Mensajes Internos</h3>
                        <button class="btn" onclick="showNewMessageModal()">
                            <i class="fas fa-plus"></i> Nuevo Mensaje
                        </button>
                    </div>
                    <div class="card-body">
                        <div class="tabs">
                            <div class="tab active" onclick="switchTab('inbox')">Bandeja de Entrada (${unreadCount})</div>
                            <div class="tab" onclick="switchTab('sent')">Enviados</div>
                        </div>
                        
                        <div id="inbox" class="tab-content active">
                            <div class="message-list">
                                ${messages
                                  .map(
                                    (message) => `
                                    <div class="message-item ${
                                      !message.read ? "unread" : ""
                                    }">
                                        <div class="message-header">
                                            <div class="message-sender">${
                                              message.sender
                                            }</div>
                                            <div class="message-date">${
                                              message.date
                                            }</div>
                                        </div>
                                        <div class="message-content">${
                                          message.content
                                        }</div>
                                        <div class="message-recipients">
                                            Para: ${message.recipients.join(
                                              ", "
                                            )}
                                        </div>
                                        ${
                                          !message.read
                                            ? `
                                            <div style="margin-top: 10px;">
                                                <button class="btn btn-sm" onclick="markAsRead(${message.id})">
                                                    <i class="fas fa-envelope-open"></i> Marcar como leído
                                                </button>
                                            </div>
                                        `
                                            : ""
                                        }
                                    </div>
                                `
                                  )
                                  .join("")}
                            </div>
                        </div>
                        
                        <div id="sent" class="tab-content">
                            <div class="message-list">
                                <div class="message-item">
                                    <div class="message-header">
                                        <div class="message-sender">Yo</div>
                                        <div class="message-date">2024-03-12 14:30</div>
                                    </div>
                                    <div class="message-content">Consulta sobre disponibilidad de productos para el próximo evento</div>
                                    <div class="message-recipients">
                                        Para: Encargado de Almacén
                                    </div>
                                </div>
                                <div class="message-item">
                                    <div class="message-header">
                                        <div class="message-sender">Yo</div>
                                        <div class="message-date">2024-03-10 09:15</div>
                                    </div>
                                    <div class="message-content">Solicitud de material adicional para prácticas</div>
                                    <div class="message-recipients">
                                        Para: Administrador
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            `;
      }

      // Modal functions
      function showModal(title, body, footer) {
        modalTitle.textContent = title;
        modalBody.innerHTML = body;
        modalFooter.innerHTML = footer;
        modal.style.display = "flex";
      }

      function closeModal() {
        modal.style.display = "none";
      }

      // Show create event modal
      function showCreateEventModal() {
        const body = `
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label>Nombre del Evento</label>
                            <input type="text" class="form-control" id="eventName" placeholder="Nombre del evento">
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label>Tipo de Evento</label>
                            <select class="form-control" id="eventType">
                                <option value="regular">Regular</option>
                                <option value="extraordinary">Extraordinario</option>
                            </select>
                        </div>
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label>Fecha de Apertura</label>
                            <input type="date" class="form-control" id="eventStartDate">
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label>Fecha de Cierre</label>
                            <input type="date" class="form-control" id="eventEndDate">
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <label>Hora de Cierre</label>
                    <input type="time" class="form-control" id="eventCloseTime">
                </div>
                <div class="form-group">
                    <label>Activación</label>
                    <select class="form-control" id="eventActivation">
                        <option value="manual">Manual</option>
                        <option value="automatic">Automática</option>
                    </select>
                </div>
            `;

        const footer = `
                <button class="btn" onclick="closeModal()">Cancelar</button>
                <button class="btn btn-success" onclick="createEvent()">Crear Evento</button>
            `;

        showModal("Crear Nuevo Evento", body, footer);
      }

      // Show add product modal
      function showAddProductModal() {
        const categories = [...new Set(db.products.map((p) => p.category))];

        const body = `
                <div class="form-group">
                    <label>Nombre del Producto</label>
                    <input type="text" class="form-control" id="productName" placeholder="Nombre del producto">
                </div>
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label>Precio (€)</label>
                            <input type="number" step="0.01" class="form-control" id="productPrice" placeholder="0.00">
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label>Unidad de Medida</label>
                            <input type="text" class="form-control" id="productUnit" placeholder="kg, litro, unidad...">
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <label>Categoría</label>
                    <select class="form-control" id="productCategory">
                        ${categories
                          .map(
                            (cat) => `<option value="${cat}">${cat}</option>`
                          )
                          .join("")}
                        <option value="new">Nueva Categoría</option>
                    </select>
                </div>
                <div class="form-group" id="newCategoryGroup" style="display: none;">
                    <label>Nueva Categoría</label>
                    <input type="text" class="form-control" id="newCategory" placeholder="Nombre de la nueva categoría">
                </div>
                <div class="form-group">
                    <label>Proveedor</label>
                    <select class="form-control" id="productProvider">
                        ${db.providers
                          .map(
                            (p) => `<option value="${p.id}">${p.name}</option>`
                          )
                          .join("")}
                        <option value="new">Nuevo Proveedor</option>
                    </select>
                </div>
            `;

        const footer = `
                <button class="btn" onclick="closeModal()">Cancelar</button>
                <button class="btn btn-success" onclick="addProduct()">Añadir Producto</button>
            `;

        showModal("Añadir Nuevo Producto", body, footer);

        // Add event listener for category selection
        document
          .getElementById("productCategory")
          .addEventListener("change", function () {
            const newCategoryGroup =
              document.getElementById("newCategoryGroup");
            if (this.value === "new") {
              newCategoryGroup.style.display = "block";
            } else {
              newCategoryGroup.style.display = "none";
            }
          });
      }

      // Show add teacher modal
      function showAddTeacherModal() {
        const body = `
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label>Nombre</label>
                            <input type="text" class="form-control" id="teacherName" placeholder="Nombre">
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label>Apellidos</label>
                            <input type="text" class="form-control" id="teacherSurname" placeholder="Apellidos">
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <label>Correo Electrónico</label>
                    <input type="email" class="form-control" id="teacherEmail" placeholder="correo@ejemplo.com">
                </div>
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label>Teléfono</label>
                            <input type="tel" class="form-control" id="teacherPhone" placeholder="Teléfono">
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label>Tipo de Profesor</label>
                            <select class="form-control" id="teacherType">
                                <option value="fijo">Fijo</option>
                                <option value="interino">Interino</option>
                            </select>
                        </div>
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label>Fecha de Nacimiento</label>
                            <input type="date" class="form-control" id="teacherBirthdate">
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label>Estatus</label>
                            <select class="form-control" id="teacherStatus">
                                <option value="titular">Titular</option>
                                <option value="sustituto">Sustituto</option>
                            </select>
                        </div>
                    </div>
                </div>
                <div class="form-group" id="substituteGroup" style="display: none;">
                    <label>Profesor Sustituido</label>
                    <select class="form-control" id="substitutedTeacher">
                        ${db.users
                          .filter((u) => u.profiles.includes("Profesor"))
                          .map(
                            (t) => `<option value="${t.id}">${t.name}</option>`
                          )
                          .join("")}
                    </select>
                </div>
            `;

        const footer = `
                <button class="btn" onclick="closeModal()">Cancelar</button>
                <button class="btn btn-success" onclick="addTeacher()">Añadir Profesor</button>
            `;

        showModal("Añadir Nuevo Profesor", body, footer);

        // Add event listener for status selection
        document
          .getElementById("teacherStatus")
          .addEventListener("change", function () {
            const substituteGroup = document.getElementById("substituteGroup");
            if (this.value === "sustituto") {
              substituteGroup.style.display = "block";
            } else {
              substituteGroup.style.display = "none";
            }
          });
      }

      // Show add provider modal
      function showAddProviderModal() {
        const body = `
                <div class="form-group">
                    <label>Nombre de la Empresa</label>
                    <input type="text" class="form-control" id="providerName" placeholder="Nombre de la empresa">
                </div>
                <div class="form-group">
                    <label>Tipo</label>
                    <select class="form-control" id="providerType">
                        <option value="sede">Sede Central</option>
                        <option value="sucursal">Sucursal</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Persona de Contacto</label>
                    <input type="text" class="form-control" id="providerContact" placeholder="Nombre del contacto">
                </div>
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label>Teléfono Principal</label>
                            <input type="tel" class="form-control" id="providerPhone" placeholder="Teléfono principal">
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label>Teléfono Secundario</label>
                            <input type="tel" class="form-control" id="providerPhone2" placeholder="Teléfono secundario (opcional)">
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <label>Email</label>
                    <input type="email" class="form-control" id="providerEmail" placeholder="correo@ejemplo.com">
                </div>
                <div class="form-group">
                    <label>Dirección</label>
                    <input type="text" class="form-control" id="providerAddress" placeholder="Dirección completa">
                </div>
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label>Ciudad</label>
                            <input type="text" class="form-control" id="providerCity" placeholder="Ciudad">
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label>Código Postal</label>
                            <input type="text" class="form-control" id="providerPostal" placeholder="Código postal">
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <label>Notas</label>
                    <textarea class="form-control" id="providerNotes" rows="3" placeholder="Notas adicionales"></textarea>
                </div>
            `;

        const footer = `
                <button class="btn" onclick="closeModal()">Cancelar</button>
                <button class="btn btn-success" onclick="addProvider()">Añadir Proveedor</button>
            `;

        showModal("Añadir Nuevo Proveedor", body, footer);
      }

      // Show new message modal
      function showNewMessageModal() {
        const profiles = ["Administrador", "Encargado de Almacén", "Profesor"];
        const teachers = db.users.filter((u) =>
          u.profiles.includes("Profesor")
        );

        const body = `
                <div class="form-group">
                    <label>Destinatarios</label>
                    <div class="recipient-list" id="recipientList">
                        <!-- Selected recipients will appear here -->
                    </div>
                    <select class="form-control" id="recipientSelect">
                        <option value="">Seleccionar destinatario...</option>
                        <option value="all">Todos</option>
                        ${profiles
                          .map((p) => `<option value="${p}">${p}</option>`)
                          .join("")}
                        ${teachers
                          .map(
                            (t) =>
                              `<option value="teacher-${t.id}">${t.name}</option>`
                          )
                          .join("")}
                    </select>
                    <button class="btn btn-sm" style="margin-top: 10px;" onclick="addRecipient()">Añadir</button>
                </div>
                <div class="form-group">
                    <label>Mensaje</label>
                    <textarea class="form-control" id="messageContent" rows="5" placeholder="Escribe tu mensaje aquí..."></textarea>
                </div>
            `;

        const footer = `
                <button class="btn" onclick="closeModal()">Cancelar</button>
                <button class="btn btn-success" onclick="sendMessage()">Enviar Mensaje</button>
            `;

        showModal("Nuevo Mensaje", body, footer);
      }

      // Action functions
      function handleLogout() {
        currentUser = null;
        currentProfile = null;
        dashboard.style.display = "none";
        loginContainer.style.display = "flex";
        document.getElementById("email").value = "";
        document.getElementById("password").value = "";
      }

      function switchTab(tabId) {
        // Hide all tab contents
        document.querySelectorAll(".tab-content").forEach((tab) => {
          tab.classList.remove("active");
        });

        // Remove active class from all tabs
        document.querySelectorAll(".tab").forEach((tab) => {
          tab.classList.remove("active");
        });

        // Show selected tab content
        document.getElementById(tabId).classList.add("active");

        // Add active class to clicked tab
        event.target.classList.add("active");
      }

      function filterProducts() {
        const categoryFilter = document
          .getElementById("categoryFilter")
          .value.toLowerCase();
        const searchTerm = document
          .getElementById("productSearch")
          .value.toLowerCase();
        const products = document.querySelectorAll(
          "#productList .product-item"
        );

        products.forEach((product) => {
          const category = product.dataset.category.toLowerCase();
          const name = product.dataset.name;

          if (
            (categoryFilter === "" || category === categoryFilter) &&
            (searchTerm === "" || name.includes(searchTerm))
          ) {
            product.style.display = "block";
          } else {
            product.style.display = "none";
          }
        });
      }

      function filterProductsForOrder() {
        const categoryFilter = document
          .getElementById("categoryFilter")
          .value.toLowerCase();
        const searchTerm = document
          .getElementById("productSearch")
          .value.toLowerCase();
        const products = document.querySelectorAll(
          "#productListForOrder .product-item"
        );

        products.forEach((product) => {
          const category = product.dataset.category.toLowerCase();
          const name = product.dataset.name;

          if (
            (categoryFilter === "" || category === categoryFilter) &&
            (searchTerm === "" || name.includes(searchTerm))
          ) {
            product.style.display = "block";
          } else {
            product.style.display = "none";
          }
        });
      }

      function addProductToOrder(productId) {
        const product = db.products.find((p) => p.id === productId);
        if (!product) return;

        // Check if product is already in order
        const existingItem = currentOrder.find((item) => item.id === productId);

        if (existingItem) {
          existingItem.quantity += 1;
        } else {
          currentOrder.push({
            id: product.id,
            name: product.name,
            price: product.price,
            unit: product.unit,
            quantity: 1,
            notes: "",
          });
        }

        updateOrderSummary();
      }

      function updateOrderSummary() {
        const orderItems = document.getElementById("orderItems");
        const orderTotal = document.getElementById("orderTotal");

        if (currentOrder.length === 0) {
          orderItems.innerHTML = "<p>No hay productos en el pedido</p>";
          orderTotal.textContent = "€0.00";
          return;
        }

        let html = "";
        let total = 0;

        currentOrder.forEach((item, index) => {
          const itemTotal = item.price * item.quantity;
          total += itemTotal;

          html += `
                    <div class="order-item">
                        <div>
                            <strong>${item.name}</strong> - ${item.quantity} ${
            item.unit
          } × €${item.price.toFixed(2)} = €${itemTotal.toFixed(2)}
                            <div style="margin-top: 5px;">
                                <input type="text" class="form-control" placeholder="Anotaciones" value="${
                                  item.notes
                                }" onchange="updateOrderNotes(${index}, this.value)">
                            </div>
                        </div>
                        <div>
                            <button class="btn btn-sm" onclick="updateOrderQuantity(${index}, ${
            item.quantity - 1
          })">
                                <i class="fas fa-minus"></i>
                            </button>
                            <span style="margin: 0 10px;">${
                              item.quantity
                            }</span>
                            <button class="btn btn-sm" onclick="updateOrderQuantity(${index}, ${
            item.quantity + 1
          })">
                                <i class="fas fa-plus"></i>
                            </button>
                            <button class="btn btn-sm btn-danger" onclick="removeFromOrder(${index})">
                                <i class="fas fa-trash"></i>
                            </button>
                        </div>
                    </div>
                `;
        });

        orderItems.innerHTML = html;
        orderTotal.textContent = `€${total.toFixed(2)}`;
      }

      function updateOrderQuantity(index, newQuantity) {
        if (newQuantity <= 0) {
          removeFromOrder(index);
          return;
        }

        currentOrder[index].quantity = newQuantity;
        updateOrderSummary();
      }

      function updateOrderNotes(index, notes) {
        currentOrder[index].notes = notes;
      }

      function removeFromOrder(index) {
        currentOrder.splice(index, 1);
        updateOrderSummary();
      }

      function submitOrder() {
        if (currentOrder.length === 0) {
          alert("No hay productos en el pedido");
          return;
        }

        // In a real app, this would send the order to the server
        const newOrder = {
          id: db.orders.length + 1,
          code: `PED-2024-${db.orders.length + 150}`,
          date: new Date().toISOString().split("T")[0],
          professor: currentUser.name,
          products: currentOrder.length,
          status: "Enviado",
          total: currentOrder.reduce(
            (sum, item) => sum + item.price * item.quantity,
            0
          ),
        };

        db.orders.push(newOrder);
        currentOrder = [];

        alert("Pedido enviado correctamente");
        loadTeacherOrders();
      }

      function saveOrderDraft() {
        if (currentOrder.length === 0) {
          alert("No hay productos en el pedido");
          return;
        }

        // In a real app, this would save the draft to the server
        alert("Borrador guardado correctamente");
      }

      function createNewOrder() {
        currentOrder = [];
        loadTeacherOrders();
      }

      function createEventOrder(eventId) {
        currentEvent = eventId;
        currentOrder = [];
        loadTeacherOrders();
      }

      function viewOrderDetails(orderId) {
        const order = db.orders.find((o) => o.id === orderId);
        if (!order) return;

        const body = `
                <div class="order-details">
                    <h4>Detalles del Pedido</h4>
                    <p><strong>Código:</strong> ${order.code}</p>
                    <p><strong>Fecha:</strong> ${order.date}</p>
                    <p><strong>Profesor:</strong> ${order.professor}</p>
                    <p><strong>Estado:</strong> ${order.status}</p>
                    <p><strong>Total:</strong> €${order.total.toFixed(2)}</p>
                    
                    <h4 style="margin-top: 20px;">Productos</h4>
                    <div class="table-responsive">
                        <table class="table">
                            <thead>
                                <tr>
                                    <th>Producto</th>
                                    <th>Cantidad</th>
                                    <th>Precio Unitario</th>
                                    <th>Total</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>Leche</td>
                                    <td>5 litros</td>
                                    <td>€1.20</td>
                                    <td>€6.00</td>
                                </tr>
                                <tr>
                                    <td>Huevos</td>
                                    <td>2 docenas</td>
                                    <td>€2.50</td>
                                    <td>€5.00</td>
                                </tr>
                                <tr>
                                    <td>Harina</td>
                                    <td>3 kg</td>
                                    <td>€0.90</td>
                                    <td>€2.70</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            `;

        const footer = `
                <button class="btn" onclick="closeModal()">Cerrar</button>
                <button class="btn" onclick="downloadOrder(${orderId})">
                    <i class="fas fa-download"></i> Descargar
                </button>
            `;

        showModal(`Detalles del Pedido ${order.code}`, body, footer);
      }

      function downloadOrder(orderId) {
        // In a real app, this would generate and download a PDF/Excel file
        alert(`Descargando pedido ${orderId}...`);
      }

      function cancelOrder(orderId) {
        if (confirm("¿Estás seguro de que quieres cancelar este pedido?")) {
          const orderIndex = db.orders.findIndex((o) => o.id === orderId);
          if (orderIndex !== -1) {
            db.orders.splice(orderIndex, 1);
            alert("Pedido cancelado correctamente");
            loadTeacherOrders();
          }
        }
      }

      function processOrder(orderId) {
        const order = db.orders.find((o) => o.id === orderId);
        if (order) {
          order.status = "Procesado";
          alert("Pedido procesado correctamente");
          loadOrderProcessing();
        }
      }

      function editEvent(eventId) {
        const event = db.events.find((e) => e.id === eventId);
        if (!event) return;

        const body = `
                <div class="form-group">
                    <label>Nombre del Evento</label>
                    <input type="text" class="form-control" id="editEventName" value="${event.name}">
                </div>
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label>Fecha de Apertura</label>
                            <input type="date" class="form-control" id="editEventStartDate" value="${event.startDate}">
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label>Fecha de Cierre</label>
                            <input type="date" class="form-control" id="editEventEndDate" value="${event.endDate}">
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <label>Hora de Cierre</label>
                    <input type="time" class="form-control" id="editEventCloseTime" value="${event.closeTime}">
                </div>
            `;

        const footer = `
                <button class="btn" onclick="closeModal()">Cancelar</button>
                <button class="btn btn-success" onclick="updateEvent(${eventId})">Guardar Cambios</button>
            `;

        showModal("Editar Evento", body, footer);
      }

      function updateEvent(eventId) {
        const event = db.events.find((e) => e.id === eventId);
        if (event) {
          event.name = document.getElementById("editEventName").value;
          event.startDate = document.getElementById("editEventStartDate").value;
          event.endDate = document.getElementById("editEventEndDate").value;
          event.closeTime = document.getElementById("editEventCloseTime").value;

          alert("Evento actualizado correctamente");
          closeModal();
          loadEventManagement();
        }
      }

      function toggleEventStatus(eventId) {
        const event = db.events.find((e) => e.id === eventId);
        if (event) {
          event.active = !event.active;
          alert(
            `Evento ${event.active ? "activado" : "desactivado"} correctamente`
          );
          loadEventManagement();
        }
      }

      function createEvent() {
        const newEvent = {
          id: db.events.length + 1,
          name: document.getElementById("eventName").value,
          startDate: document.getElementById("eventStartDate").value,
          endDate: document.getElementById("eventEndDate").value,
          closeTime: document.getElementById("eventCloseTime").value,
          type: document.getElementById("eventType").value,
          active: true,
        };

        db.events.push(newEvent);
        alert("Evento creado correctamente");
        closeModal();
        loadEventManagement();
      }

      function addProduct() {
        const name = document.getElementById("productName").value;
        const price = parseFloat(document.getElementById("productPrice").value);
        const unit = document.getElementById("productUnit").value;
        let category = document.getElementById("productCategory").value;

        if (category === "new") {
          category = document.getElementById("newCategory").value;
        }

        const newProduct = {
          id: db.products.length + 1,
          name,
          price,
          unit,
          category,
          image: "product",
        };

        db.products.push(newProduct);
        alert("Producto añadido correctamente");
        closeModal();
        loadProductManagement();
      }

      function editProduct(productId) {
        const product = db.products.find((p) => p.id === productId);
        if (!product) return;

        const body = `
                <div class="form-group">
                    <label>Nombre del Producto</label>
                    <input type="text" class="form-control" id="editProductName" value="${
                      product.name
                    }">
                </div>
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label>Precio (€)</label>
                            <input type="number" step="0.01" class="form-control" id="editProductPrice" value="${
                              product.price
                            }">
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label>Unidad de Medida</label>
                            <input type="text" class="form-control" id="editProductUnit" value="${
                              product.unit
                            }">
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <label>Categoría</label>
                    <select class="form-control" id="editProductCategory">
                        ${[...new Set(db.products.map((p) => p.category))]
                          .map(
                            (cat) =>
                              `<option value="${cat}" ${
                                cat === product.category ? "selected" : ""
                              }>${cat}</option>`
                          )
                          .join("")}
                    </select>
                </div>
            `;

        const footer = `
                <button class="btn" onclick="closeModal()">Cancelar</button>
                <button class="btn btn-success" onclick="updateProduct(${productId})">Guardar Cambios</button>
            `;

        showModal("Editar Producto", body, footer);
      }

      function updateProduct(productId) {
        const product = db.products.find((p) => p.id === productId);
        if (product) {
          product.name = document.getElementById("editProductName").value;
          product.price = parseFloat(
            document.getElementById("editProductPrice").value
          );
          product.unit = document.getElementById("editProductUnit").value;
          product.category = document.getElementById(
            "editProductCategory"
          ).value;

          alert("Producto actualizado correctamente");
          closeModal();
          loadProductManagement();
        }
      }

      function deleteProduct(productId) {
        if (confirm("¿Estás seguro de que quieres eliminar este producto?")) {
          const productIndex = db.products.findIndex((p) => p.id === productId);
          if (productIndex !== -1) {
            db.products.splice(productIndex, 1);
            alert("Producto eliminado correctamente");
            loadProductManagement();
          }
        }
      }

      function addTeacher() {
        const name = document.getElementById("teacherName").value;
        const surname = document.getElementById("teacherSurname").value;
        const email = document.getElementById("teacherEmail").value;
        const phone = document.getElementById("teacherPhone").value;
        const type = document.getElementById("teacherType").value;
        const birthdate = document.getElementById("teacherBirthdate").value;
        const status = document.getElementById("teacherStatus").value;

        const newTeacher = {
          id: db.users.length + 1,
          email,
          password: "temp123", // Temporary password
          name: `${name} ${surname}`,
          profiles: ["Profesor"],
        };

        db.users.push(newTeacher);
        alert(
          "Profesor añadido correctamente. Se ha enviado un correo con las credenciales de acceso."
        );
        closeModal();
        loadTeacherManagement();
      }

      function editTeacher(teacherId) {
        const teacher = db.users.find((u) => u.id === teacherId);
        if (!teacher) return;

        const body = `
                <div class="form-group">
                    <label>Nombre</label>
                    <input type="text" class="form-control" id="editTeacherName" value="${teacher.name}">
                </div>
                <div class="form-group">
                    <label>Correo Electrónico</label>
                    <input type="email" class="form-control" id="editTeacherEmail" value="${teacher.email}">
                </div>
                <div class="form-group">
                    <label>Restablecer Contraseña</label>
                    <button class="btn" onclick="resetTeacherPassword(${teacherId})">
                        <i class="fas fa-key"></i> Generar Nueva Contraseña
                    </button>
                </div>
            `;

        const footer = `
                <button class="btn" onclick="closeModal()">Cancelar</button>
                <button class="btn btn-success" onclick="updateTeacher(${teacherId})">Guardar Cambios</button>
            `;

        showModal("Editar Profesor", body, footer);
      }

      function updateTeacher(teacherId) {
        const teacher = db.users.find((u) => u.id === teacherId);
        if (teacher) {
          teacher.name = document.getElementById("editTeacherName").value;
          teacher.email = document.getElementById("editTeacherEmail").value;

          alert("Profesor actualizado correctamente");
          closeModal();
          loadTeacherManagement();
        }
      }

      function resetTeacherPassword(teacherId) {
        if (
          confirm(
            "¿Estás seguro de que quieres restablecer la contraseña de este profesor?"
          )
        ) {
          alert(
            "Se ha generado una nueva contraseña temporal y se ha enviado al profesor por correo electrónico."
          );
        }
      }

      function addProvider() {
        const name = document.getElementById("providerName").value;
        const type = document.getElementById("providerType").value;
        const contact = document.getElementById("providerContact").value;
        const phone = document.getElementById("providerPhone").value;
        const phone2 = document.getElementById("providerPhone2").value;
        const email = document.getElementById("providerEmail").value;
        const address = document.getElementById("providerAddress").value;
        const city = document.getElementById("providerCity").value;
        const postal = document.getElementById("providerPostal").value;
        const notes = document.getElementById("providerNotes").value;

        const newProvider = {
          id: db.providers.length + 1,
          name,
          type,
          contact,
          phone,
          phone2,
          email,
          address,
          city,
          postal,
          notes,
        };

        db.providers.push(newProvider);
        alert("Proveedor añadido correctamente");
        closeModal();
        loadProviderManagement();
      }

      function editProvider(providerId) {
        const provider = db.providers.find((p) => p.id === providerId);
        if (!provider) return;

        const body = `
                <div class="form-group">
                    <label>Nombre de la Empresa</label>
                    <input type="text" class="form-control" id="editProviderName" value="${
                      provider.name
                    }">
                </div>
                <div class="form-group">
                    <label>Persona de Contacto</label>
                    <input type="text" class="form-control" id="editProviderContact" value="${
                      provider.contact
                    }">
                </div>
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label>Teléfono Principal</label>
                            <input type="tel" class="form-control" id="editProviderPhone" value="${
                              provider.phone
                            }">
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label>Teléfono Secundario</label>
                            <input type="tel" class="form-control" id="editProviderPhone2" value="${
                              provider.phone2 || ""
                            }">
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <label>Email</label>
                    <input type="email" class="form-control" id="editProviderEmail" value="${
                      provider.email
                    }">
                </div>
            `;

        const footer = `
                <button class="btn" onclick="closeModal()">Cancelar</button>
                <button class="btn btn-success" onclick="updateProvider(${providerId})">Guardar Cambios</button>
            `;

        showModal("Editar Proveedor", body, footer);
      }

      function updateProvider(providerId) {
        const provider = db.providers.find((p) => p.id === providerId);
        if (provider) {
          provider.name = document.getElementById("editProviderName").value;
          provider.contact = document.getElementById(
            "editProviderContact"
          ).value;
          provider.phone = document.getElementById("editProviderPhone").value;
          provider.phone2 = document.getElementById("editProviderPhone2").value;
          provider.email = document.getElementById("editProviderEmail").value;

          alert("Proveedor actualizado correctamente");
          closeModal();
          loadProviderManagement();
        }
      }

      function deleteProvider(providerId) {
        if (confirm("¿Estás seguro de que quieres eliminar este proveedor?")) {
          const providerIndex = db.providers.findIndex(
            (p) => p.id === providerId
          );
          if (providerIndex !== -1) {
            db.providers.splice(providerIndex, 1);
            alert("Proveedor eliminado correctamente");
            loadProviderManagement();
          }
        }
      }

      function trackDelivery(deliveryId) {
        alert(
          `Seguimiento de entrega ${deliveryId}. En una aplicación real, aquí se mostraría el mapa con la ubicación del repartidor.`
        );
      }

      function viewDeliveryDetails(deliveryId) {
        const body = `
                <div class="delivery-details">
                    <h4>Detalles de la Entrega</h4>
                    <p><strong>Pedido:</strong> PED-2024-148</p>
                    <p><strong>Proveedor:</strong> Papelera del Sur</p>
                    <p><strong>Fecha de Entrega:</strong> 2024-03-17</p>
                    <p><strong>Productos:</strong> 5</p>
                    <p><strong>Estado:</strong> Completado</p>
                    
                    <h4 style="margin-top: 20px;">Productos Entregados</h4>
                    <div class="table-responsive">
                        <table class="table">
                            <thead>
                                <tr>
                                    <th>Producto</th>
                                    <th>Cantidad</th>
                                    <th>Estado</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>Papel A4</td>
                                    <td>2 paquetes</td>
                                    <td><span class="badge badge-success">Entregado</span></td>
                                </tr>
                                <tr>
                                    <td>Bolígrafos</td>
                                    <td>1 caja</td>
                                    <td><span class="badge badge-success">Entregado</span></td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            `;

        const footer = `
                <button class="btn" onclick="closeModal()">Cerrar</button>
            `;

        showModal("Detalles de Entrega", body, footer);
      }

      function generateReport(type, format = "pdf") {
        alert(
          `Generando reporte ${type} en formato ${format.toUpperCase()}. En una aplicación real, esto descargaría el archivo.`
        );
      }

      function viewEventDetails(eventId) {
        const event = db.events.find((e) => e.id === eventId);
        if (!event) return;

        const body = `
                <div class="event-details">
                    <h4>Detalles del Evento</h4>
                    <p><strong>Nombre:</strong> ${event.name}</p>
                    <p><strong>Fecha:</strong> ${event.startDate} - ${
          event.endDate
        }</p>
                    <p><strong>Hora de Cierre:</strong> ${event.closeTime}</p>
                    <p><strong>Tipo:</strong> ${
                      event.type === "regular" ? "Regular" : "Extraordinario"
                    }</p>
                    
                    <h4 style="margin-top: 20px;">Mi Pedido</h4>
                    <div class="table-responsive">
                        <table class="table">
                            <thead>
                                <tr>
                                    <th>Producto</th>
                                    <th>Cantidad</th>
                                    <th>Precio Unitario</th>
                                    <th>Total</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>Leche</td>
                                    <td>3 litros</td>
                                    <td>€1.20</td>
                                    <td>€3.60</td>
                                </tr>
                                <tr>
                                    <td>Huevos</td>
                                    <td>1 docena</td>
                                    <td>€2.50</td>
                                    <td>€2.50</td>
                                </tr>
                                <tr>
                                    <td>Harina</td>
                                    <td>2 kg</td>
                                    <td>€0.90</td>
                                    <td>€1.80</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    <p style="margin-top: 15px; font-weight: 500;">Total: €7.90</p>
                </div>
            `;

        const footer = `
                <button class="btn" onclick="closeModal()">Cerrar</button>
                <button class="btn" onclick="downloadEventReport(${eventId})">
                    <i class="fas fa-download"></i> Descargar Reporte
                </button>
            `;

        showModal(`Detalles del Evento: ${event.name}`, body, footer);
      }

      function downloadEventReport(eventId) {
        alert(
          `Descargando reporte del evento ${eventId}. En una aplicación real, esto descargaría un archivo PDF o Excel.`
        );
      }

      function addRecipient() {
        const select = document.getElementById("recipientSelect");
        const recipientList = document.getElementById("recipientList");
        const value = select.value;

        if (!value) return;

        let recipientText = "";

        if (value === "all") {
          recipientText = "Todos";
        } else if (value.startsWith("teacher-")) {
          const teacherId = parseInt(value.split("-")[1]);
          const teacher = db.users.find((u) => u.id === teacherId);
          recipientText = teacher ? teacher.name : "";
        } else {
          recipientText = value;
        }

        if (recipientText) {
          const tag = document.createElement("div");
          tag.className = "recipient-tag";
          tag.innerHTML = `
                    ${recipientText}
                    <button type="button" onclick="this.parentElement.remove()">×</button>
                `;
          recipientList.appendChild(tag);
        }

        select.value = "";
      }

      function sendMessage() {
        const content = document.getElementById("messageContent").value;
        const recipientTags = document.querySelectorAll(
          "#recipientList .recipient-tag"
        );

        if (!content.trim()) {
          alert("El mensaje no puede estar vacío");
          return;
        }

        if (recipientTags.length === 0) {
          alert("Debes seleccionar al menos un destinatario");
          return;
        }

        const recipients = Array.from(recipientTags).map((tag) =>
          tag.textContent.trim()
        );

        const newMessage = {
          id: db.messages.length + 1,
          sender: currentUser.name,
          recipients,
          content,
          date: new Date().toLocaleString(),
          read: false,
        };

        db.messages.unshift(newMessage);
        updateNotificationBadge();

        alert("Mensaje enviado correctamente");
        closeModal();
        loadMessages();
      }

      function markAsRead(messageId) {
        const message = db.messages.find((m) => m.id === messageId);
        if (message) {
          message.read = true;
          updateNotificationBadge();
          loadMessages();
        }
      }

      function updateNotificationBadge() {
        const unreadCount = db.messages.filter((m) => !m.read).length;
        notificationBadge.textContent = unreadCount;
        notificationBadge.style.display = unreadCount > 0 ? "block" : "none";
      }

      // Initialize the app when DOM is loaded
      document.addEventListener("DOMContentLoaded", init);
    </script>
  </body>
</html>
