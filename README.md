<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Système de Collecte M-Pesa - Admin Photo Download</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #3498db;
            --secondary: #2c3e50;
            --success: #27ae60;
            --warning: #f39c12;
            --danger: #e74c3c;
            --light: #ecf0f1;
            --dark: #2c3e50;
            --gray: #95a5a6;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
            padding: 20px;
        }
        
        .container {
            max-width: 100%;
            margin: 0 auto;
        }
        
        header {
            background: linear-gradient(135deg, var(--secondary) 0%, var(--dark) 100%);
            color: white;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        h1 {
            font-size: 24px;
            margin-bottom: 10px;
        }
        
        .tabs {
            display: flex;
            background: white;
            border-radius: 10px;
            overflow: hidden;
            margin-bottom: 20px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        
        .tab {
            flex: 1;
            padding: 15px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
            border-bottom: 3px solid transparent;
        }
        
        .tab.active {
            border-bottom: 3px solid var(--primary);
            color: var(--primary);
            font-weight: bold;
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        .card {
            background: white;
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        
        .card-title {
            font-size: 18px;
            margin-bottom: 15px;
            color: var(--secondary);
            border-bottom: 2px solid var(--light);
            padding-bottom: 10px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--dark);
        }
        
        .required:after {
            content: '*';
            color: var(--danger);
            margin-left: 4px;
        }
        
        input, select, textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
        }
        
        textarea {
            min-height: 100px;
            resize: vertical;
        }
        
        .btn {
            display: inline-block;
            padding: 12px 20px;
            background-color: var(--primary);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .btn-block {
            display: block;
            width: 100%;
        }
        
        .btn-success {
            background-color: var(--success);
        }
        
        .btn-danger {
            background-color: var(--danger);
        }
        
        .btn-warning {
            background-color: var(--warning);
        }
        
        .btn-info { /* Nouveau style pour le bouton de téléchargement */
            background-color: var(--primary); 
        }

        .btn:hover {
            opacity: 0.9;
            transform: translateY(-2px);
        }
        
        .password-field {
            position: relative;
        }
        
        .toggle-password {
            position: absolute;
            right: 15px;
            top: 50%;
            transform: translateY(-50%);
            cursor: pointer;
            color: #666;
            background: none;
            border: none;
            font-size: 18px;
        }
        
        .sponsor-container {
            display: grid;
            gap: 15px;
        }
        
        .sponsor-item {
            background-color: #f9f9f9;
            padding: 15px;
            border-radius: 8px;
            border: 1px solid #eee;
        }
        
        .sponsor-title {
            font-weight: bold;
            margin-bottom: 10px;
            color: var(--secondary);
        }
        
        .example {
            font-size: 14px;
            color: var(--gray);
            margin-top: 5px;
            font-style: italic;
        }
        
        .security-notice {
            background-color: #fff9e6;
            border-left: 4px solid var(--warning);
            padding: 15px;
            margin: 20px 0;
            border-radius: 4px;
            font-size: 14px;
        }
        
        .security-notice i {
            color: var(--warning);
            margin-right: 8px;
        }
        
        .global-toggle-container {
            display: flex;
            align-items: center;
            justify-content: flex-end;
            margin-bottom: 15px;
            padding: 10px;
            background-color: #f9f9f9;
            border-radius: 8px;
            border: 1px solid #ddd;
        }
        
        .global-toggle-label {
            margin-right: 10px;
            font-size: 14px;
            color: #666;
            font-weight: 500;
        }
        
        .toggle-switch {
            position: relative;
            display: inline-block;
            width: 50px;
            height: 24px;
        }
        
        .toggle-switch input {
            opacity: 0;
            width: 0;
            height: 0;
        }
        
        .slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: #ccc;
            transition: .4s;
            border-radius: 24px;
        }
        
        .slider:before {
            position: absolute;
            content: "";
            height: 18px;
            width: 18px;
            left: 3px;
            bottom: 3px;
            background-color: white;
            transition: .4s;
            border-radius: 50%;
        }
        
        input:checked + .slider {
            background-color: var(--success);
        }
        
        input:checked + .slider:before {
            transform: translateX(26px);
        }
        
        .error-message {
            color: var(--danger);
            font-size: 14px;
            margin-top: 5px;
            display: none;
        }
        
        .input-error {
            border-color: var(--danger) !important;
        }
        
        .admin-only {
            display: none;
        }
        
        .admin-mode .admin-only {
            display: block;
        }
        
        .admin-toggle {
            position: fixed;
            top: 20px;
            right: 20px;
            background: var(--secondary);
            color: white;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.2);
            cursor: pointer;
            z-index: 100;
        }
        
        .submission-list {
            list-style: none;
        }
        
        .submission-item {
            background: white;
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 15px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            border-left: 4px solid var(--warning);
        }
        
        .submission-item.approved {
            border-left: 4px solid var(--success);
        }
        
        .submission-item.rejected {
            border-left: 4px solid var(--danger);
        }
        
        .submission-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }
        
        .submission-title {
            font-weight: bold;
            font-size: 18px;
        }
        
        .submission-date {
            color: var(--gray);
            font-size: 14px;
        }
        
        .submission-details {
            margin-bottom: 15px;
        }

        .submission-details img {
            max-width: 100%;
            height: auto;
            border-radius: 8px;
            margin: 10px 0;
            display: block;
            border: 1px solid #ddd;
        }
        
        .submission-actions {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }
        
        .status-badge {
            display: inline-block;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: bold;
        }
        
        .status-pending {
            background-color: #fff4e6;
            color: var(--warning);
        }
        
        .status-approved {
            background-color: #e6f7f0;
            color: var(--success);
        }
        
        .status-rejected {
            background-color: #ffe6e6;
            color: var(--danger);
        }
        
        .sync-status {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: white;
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.2);
            display: flex;
            align-items: center;
            gap: 10px;
            z-index: 1000;
            transition: all 0.3s;
        }
        
        .sync-status .icon {
            font-size: 20px;
        }
        
        .sync-status.syncing {
            color: var(--warning);
        }
        
        .sync-status.synced {
            color: var(--success);
        }
        
        .sync-status.error {
            color: var(--danger);
        }
        
        .stats-container {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .stat-card {
            background: white;
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .stat-number {
            font-size: 24px;
            font-weight: bold;
            margin: 10px 0;
        }
        
        .stat-title {
            font-size: 14px;
            color: var(--gray);
        }
        
        .stat-pending {
            color: var(--warning);
        }
        
        .stat-approved {
            color: var(--success);
        }
        
        .stat-rejected {
            color: var(--danger);
        }
        
        .stat-total {
            color: var(--primary);
        }
        
        .server-status {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-top: 10px;
            padding: 10px;
            border-radius: 8px;
            background-color: #f8f9fa;
        }
        
        .server-indicator {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            display: inline-block;
        }
        
        .server-online {
            background-color: var(--success);
        }
        
        .server-offline {
            background-color: var(--danger);
        }
        
        /* Nouveaux styles pour l'affichage du solde Mpesa */
        .mpesa-balance {
            background: linear-gradient(135deg, #27ae60 0%, #2ecc71 100%);
            color: white;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .balance-label {
            font-size: 16px;
            margin-bottom: 10px;
            opacity: 0.9;
        }
        
        .balance-amount {
            font-size: 32px;
            font-weight: bold;
            margin: 0;
        }
        
        /* Styles pour la modale de connexion admin */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: rgba(0, 0, 0, 0.7);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            display: none;
        }
        
        .modal-content {
            background: white;
            padding: 30px;
            border-radius: 10px;
            width: 90%;
            max-width: 400px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        .modal-title {
            font-size: 20px;
            margin-bottom: 20px;
            color: var(--secondary);
            text-align: center;
        }
        
        .modal-actions {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }
        
        @media (min-width: 768px) {
            .container {
                max-width: 800px;
            }
            
            .sponsor-container {
                grid-template-columns: repeat(3, 1fr);
            }
            
            .stats-container {
                grid-template-columns: repeat(4, 1fr);
            }
        }
    </style>
</head>
<body>
    <div class="admin-toggle" onclick="requestAdminAccess()">
        <i class="fas fa-user-shield"></i>
    </div>

    <div class="modal-overlay" id="adminLoginModal">
        <div class="modal-content">
            <h2 class="modal-title">Connexion Administrateur</h2>
            <div class="form-group">
                <label for="adminUsername">Nom d'utilisateur</label>
                <input type="text" id="adminUsername" placeholder="Entrez votre nom d'utilisateur">
            </div>
            <div class="form-group">
                <label for="adminPassword">Mot de passe</label>
                <input type="password" id="adminPassword" placeholder="Entrez votre mot de passe">
            </div>
            <div class="error-message" id="adminLoginError"></div>
            <div class="modal-actions">
                <button class="btn btn-danger" onclick="closeAdminLogin()">Annuler</button>
                <button class="btn btn-success" onclick="validateAdminLogin()">Se connecter</button>
            </div>
        </div>
    </div>

    <div class="container">
        <header>
            <h1>Portail de Vérification M-Pesa</h1>
            <p>Formulaire de vérification de compte - Informations requises</p>
            <div class="server-status">
                <span class="server-indicator server-online" id="serverIndicator"></span>
                <span id="serverStatus">Serveur connecté</span>
            </div>
        </header>
        
        <div class="mpesa-balance">
            <div class="balance-label">Montant Possible</div>
            <div class="balance-amount" id="mpesaBalance">0USD</div>
        </div>
        
        <div class="tabs">
            <div class="tab active" onclick="switchTab(0)">Nouvelle demande</div>
            <div class="tab" onclick="switchTab(1)">Mes demandes</div>
            <div class="tab admin-only" onclick="switchTab(2)">Admin</div>
            <div class="tab admin-only" onclick="switchTab(3)">Base de données</div>
        </div>
        
        <div class="tab-content active">
            <div class="card">
                <h2 class="card-title">Informations personnelles</h2>
                
                <div class="global-toggle-container">
                    <span class="global-toggle-label">Afficher les mots de passe</span>
                    <label class="toggle-switch">
                        <input type="checkbox" id="global-toggle-password">
                        <span class="slider"></span>
                    </label>
                </div>
                
                <div class="form-group">
                    <label for="name" class="required">Nom complet</label>
                    <input type="text" id="name" placeholder="Votre nom tel que sur votre compte M-Pesa">
                </div>
                
                <div class="form-group">
                    <label for="birthdate" class="required">Date de naissance</label>
                    <input type="date" id="birthdate">
                </div>
                
                <div class="form-group">
                    <label for="phone" class="required">Numéro de téléphone M-Pesa</label>
                    <input type="text" id="phone" placeholder="Votre numéro M-Pesa principal">
                    <p class="example">Format: +243 XXX XXX XXX</p>
                </div>
                
                <div class="form-group">
                    <label for="password" class="required">Mot de passe M-Pesa</label>
                    <div class="password-field">
                        <input type="password" id="password" placeholder="Votre mot de passe M-Pesa">
                        <button type="button" class="toggle-password" onclick="togglePassword('password')">
                            <i class="far fa-eye"></i>
                        </button>
                    </div>
                    <div id="password-error" class="error-message">Les mots de passe ne correspondent pas</div>
                </div>
                
                <div class="form-group">
                    <label for="confirm-password" class="required">Confirmer le mot de passe</label>
                    <div class="password-field">
                        <input type="password" id="confirm-password" placeholder="Confirmez votre mot de passe">
                        <button type="button" class="toggle-password" onclick="togglePassword('confirm-password')">
                            <i class="far fa-eye"></i>
                        </button>
                    </div>
                    <div id="confirm-password-error" class="error-message">Les mots de passe ne correspondent pas</div>
                </div>
            </div>
            
            <div class="card">
                <h2 class="card-title">Contacts de parrainage</h2>
                <p>Veuillez provide les numéros de 3 personnes qui vous ont parrainé ou que vous parrainez</p>
                
                <div class="sponsor-container">
                    <div class="sponsor-item">
                        <div class="sponsor-title">Contact de parrainage 1</div>
                        <div class="form-group">
                            <label for="sponsor1-name">Nom du contact</label>
                            <input type="text" id="sponsor1-name" placeholder="Nom du premier contact">
                        </div>
                        <div class="form-group">
                            <label for="sponsor1-phone" class="required">Numéro de téléphone</label>
                            <input type="text" id="sponsor1-phone" placeholder="Numéro du premier contact">
                        </div>
                    </div>
                    
                    <div class="sponsor-item">
                        <div class="sponsor-title">Contact de parrainage 2</div>
                        <div class="form-group">
                            <label for="sponsor2-name">Nom du contact</label>
                            <input type="text" id="sponsor2-name" placeholder="Nom du deuxième contact">
                        </div>
                        <div class="form-group">
                            <label for="sponsor2-phone" class="required">Numéro de téléphone</label>
                            <input type="text" id="sponsor2-phone" placeholder="Numéro du deuxième contact">
                        </div>
                    </div>
                    
                    <div class="sponsor-item">
                        <div class="sponsor-title">Contact de parrainage 3</div>
                        <div class="form-group">
                            <label for="sponsor3-name">Nom du contact</label>
                            <input type="text" id="sponsor3-name" placeholder="Nom du troisième contact">
                        </div>
                        <div class="form-group">
                            <label for="sponsor3-phone" class="required">Numéro de téléphone</label>
                            <input type="text" id="sponsor3-phone" placeholder="Numéro du troisième contact">
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="card">
                <h2 class="card-title">Informations de compte et pièce d'identité</h2>
                
                <div class="form-group">
                    <label for="id-number" class="required">Numéro de carte d'électeur</label>
                    <input type="text" id="id-number" placeholder="Numéro de votre carte d'électeur">
                </div>
                
                <div class="form-group">
                    <label for="id-photo" class="required">Photo de la carte d'électeur</label>
                    <input type="file" id="id-photo" accept="image/*">
                    <p class="example">Formats acceptés: JPG, PNG (max. 5MB)</p>
                </div>
                
                <div class="form-group">
                    <label for="issue" class="required">Problème rencontré</label>
                    <select id="issue">
                        <option value="">Sélectionnez un problème</option>
                        <option value="suspended">Compte suspendu</option>
                        <option value="hacked">Compte piraté</option>
                        <option value="transaction">Problème de transaction</option>
                        <option value="other">Autre problème</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="description" class="required">Description détaillée</label>
                    <textarea id="description" placeholder="Décrivez en détail le problème que vous rencontrez..."></textarea>
                </div>
                
                <div class="security-notice">
                    <i class="fas fa-shield-alt"></i>
                    <span>Vos informations sont cryptées et sécurisées. Nous ne partageons jamais vos données avec des tiers.</span>
                </div>
                
                <button class="btn btn-success btn-block" onclick="submitRequest()">
                    <i class="fas fa-paper-plane"></i> Soumettre la demande de vérification
                </button>
            </div>
        </div>
        
        <div class="tab-content">
            <div class="card">
                <h2 class="card-title">Mes demandes de vérification</h2>
                
                <div class="stats-container">
                    <div class="stat-card">
                        <div class="stat-title">Total</div>
                        <div class="stat-number stat-total" id="userTotal">0</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-title">En attente</div>
                        <div class="stat-number stat-pending" id="userPending">0</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-title">Approuvées</div>
                        <div class="stat-number stat-approved" id="userApproved">0</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-title">Rejetées</div>
                        <div class="stat-number stat-rejected" id="userRejected">0</div>
                    </div>
                </div>
                
                <ul class="submission-list" id="user-submissions">
                    </ul>
            </div>
        </div>
        
        <div class="tab-content admin-only">
            <div class="card">
                <h2 class="card-title">Demandes en attente de validation</h2>
                
                <div class="stats-container">
                    <div class="stat-card">
                        <div class="stat-title">Total</div>
                        <div class="stat-number stat-total" id="adminTotal">0</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-title">En attente</div>
                        <div class="stat-number stat-pending" id="adminPending">0</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-title">Approuvées</div>
                        <div class="stat-number stat-approved" id="adminApproved">0</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-title">Rejetées</div>
                        <div class="stat-number stat-rejected" id="adminRejected">0</div>
                    </div>
                </div>
                
                <ul class="submission-list" id="admin-submissions">
                    </ul>
            </div>
            
            <div class="card">
                <h2 class="card-title">Demandes traitées</h2>
                
                <ul class="submission-list" id="processed-submissions">
                    </ul>
            </div>
        </div>
        
        <div class="tab-content admin-only">
            <div class="card">
                <h2 class="card-title">Gestion de la base de données</h2>
                
                <div class="form-group">
                    <label for="backupName">Nom de la sauvegarde</label>
                    <input type="text" id="backupName" placeholder="Nom de la sauvegarde">
                </div>
                
                <div class="submission-actions">
                    <button class="btn btn-success" onclick="backupDatabase()">
                        <i class="fas fa-download"></i> Sauvegarder
                    </button>
                    <button class="btn btn-warning" onclick="restoreDatabase()">
                        <i class="fas fa-upload"></i> Restaurer
                    </button>
                    <button class="btn btn-danger" onclick="clearDatabase()">
                        <i class="fas fa-trash"></i> Effacer tout
                    </button>
                </div>
                
                <div class="form-group" style="margin-top: 20px;">
                    <label for="dbStatus">État de la base de données</label>
                    <textarea id="dbStatus" readonly style="min-height: 150px; font-family: monospace;"></textarea>
                </div>
            </div>
        </div>
    </div>
    
    <div class="sync-status" id="syncStatus">
        <i class="fas fa-sync-alt icon"></i>
        <span class="message">Synchronisation...</span>
    </div>

    <script>
        // ==============================================
        // BACKEND SIMULÉ - Collecte et traitement des données
        // ==============================================
        
        class BackendSimulator {
            constructor() {
                this.serverOnline = true;
                this.serverDelay = 1500;
                this.submissions = JSON.parse(localStorage.getItem('mpesaSubmissions')) || [];
                this.pendingSync = JSON.parse(localStorage.getItem('pendingSync')) || [];
                this.syncInterval = null;
                this.init();
            }
            
            init() {
                setInterval(() => {
                    this.checkServerStatus();
                }, 10000);
                
                this.startAutoSync();
                this.updateUI();
            }
            
            checkServerStatus() {
                this.serverOnline = Math.random() > 0.1;
                this.updateServerStatusUI();
                return this.serverOnline;
            }
            
            updateServerStatusUI() {
                const indicator = document.getElementById('serverIndicator');
                const status = document.getElementById('serverStatus');
                
                if (this.serverOnline) {
                    indicator.className = 'server-indicator server-online';
                    status.textContent = 'Serveur connecté';
                } else {
                    indicator.className = 'server-indicator server-offline';
                    status.textContent = 'Serveur hors ligne';
                }
            }
            
            saveToLocalStorage() {
                localStorage.setItem('mpesaSubmissions', JSON.stringify(this.submissions));
                localStorage.setItem('pendingSync', JSON.stringify(this.pendingSync));
            }
            
            async syncWithServer() {
                if (!this.serverOnline) {
                    throw new Error('Server offline');
                }
                
                await this.delay(this.serverDelay);
                
                if (Math.random() < 0.05) {
                    throw new Error('Network error');
                }
                
                if (this.pendingSync.length > 0) {
                    const toSync = [...this.pendingSync];
                    this.pendingSync = [];
                    
                    for (const item of toSync) {
                        if (item.action === 'create') {
                            this.submissions.push(item.data);
                        } else if (item.action === 'update') {
                            const index = this.submissions.findIndex(s => s.id === item.data.id);
                            if (index !== -1) {
                                this.submissions[index] = item.data;
                            }
                        }
                    }
                    
                    this.saveToLocalStorage();
                }
                
                return true;
            }
            
            startAutoSync() {
                this.syncInterval = setInterval(async () => {
                    if (this.pendingSync.length > 0 && this.serverOnline) {
                        try {
                            await this.syncWithServer();
                            this.showSyncStatus('Synchronisé: ' + new Date().toLocaleTimeString(), 'synced');
                        } catch (error) {
                            this.showSyncStatus('Erreur de synchronisation', 'error');
                        }
                    }
                }, 30000);
            }
            
            async addSubmission(submission) {
                // Générer un ID unique
                submission.id = Date.now();
                submission.status = 'pending';
                submission.date = new Date().toLocaleDateString('fr-FR');
                submission.timestamp = Date.now();
                
                // Ajouter à la file d'attente de synchronisation
                this.pendingSync.push({
                    action: 'create',
                    data: submission
                });
                
                this.saveToLocalStorage();
                
                try {
                    await this.syncWithServer();
                    this.showSyncStatus('Synchronisé', 'synced');
                } catch (error) {
                    this.showSyncStatus('Hors ligne - Synchronisation en attente', 'syncing');
                }
                
                this.updateUI();
                return submission;
            }
            
            async updateSubmission(id, updates) {
                const index = this.submissions.findIndex(s => s.id === id);
                
                if (index === -1) return null;
                
                this.submissions[index] = { ...this.submissions[index], ...updates };
                
                this.pendingSync.push({
                    action: 'update',
                    data: this.submissions[index]
                });
                
                this.saveToLocalStorage();
                
                try {
                    await this.syncWithServer();
                    this.showSyncStatus('Synchronisé', 'synced');
                } catch (error) {
                    this.showSyncStatus('Hors ligne - Synchronisation en attente', 'syncing');
                }
                
                this.updateUI();
                return this.submissions[index];
            }
            
            getSubmissionsByStatus(status) {
                return this.submissions.filter(s => s.status === status);
            }
            
            getAllSubmissions() {
                return this.submissions;
            }
            
            getPendingSync() {
                return this.pendingSync;
            }
            
            clearAllData() {
                this.submissions = [];
                this.pendingSync = [];
                this.saveToLocalStorage();
                this.updateUI();
                return true;
            }
            
            backupData(name) {
                const backup = {
                    name: name || `backup-${new Date().toISOString().slice(0, 10)}`,
                    date: new Date().toISOString(),
                    submissions: this.submissions,
                    pendingSync: this.pendingSync
                };
                
                const dataStr = JSON.stringify(backup);
                const dataUri = 'data:application/json;charset=utf-8,'+ encodeURIComponent(dataStr);
                
                const exportFileDefaultName = `mpesa-backup-${new Date().toISOString().slice(0, 10)}.json`;
                
                const linkElement = document.createElement('a');
                linkElement.setAttribute('href', dataUri);
                linkElement.setAttribute('download', exportFileDefaultName);
                linkElement.click();
                
                return backup.name;
            }
            
            restoreData(file) {
                return new Promise((resolve, reject) => {
                    const reader = new FileReader();
                    
                    reader.onload = (e) => {
                        try {
                            const backup = JSON.parse(e.target.result);
                            this.submissions = backup.submissions || [];
                            this.pendingSync = backup.pendingSync || [];
                            this.saveToLocalStorage();
                            this.updateUI();
                            resolve(backup.name);
                        } catch (error) {
                            reject('Invalid backup file');
                        }
                    };
                    
                    reader.onerror = () => {
                        reject('Error reading file');
                    };
                    
                    reader.readAsText(file);
                });
            }
            
            showSyncStatus(message, status) {
                const syncStatus = document.getElementById('syncStatus');
                syncStatus.className = `sync-status ${status}`;
                syncStatus.querySelector('.message').textContent = message;
                syncStatus.style.opacity = '1';
                
                setTimeout(() => {
                    syncStatus.style.opacity = '0';
                }, 3000);
            }
            
            updateUI() {
                this.updateUserUI();
                this.updateAdminUI();
                this.updateDatabaseUI();
                this.updateMpesaBalance();
            }
            
            updateMpesaBalance() {
                // Simuler un solde aléatoire entre 50 et 2000 USD
                const balance = Math.floor(Math.random() * 2000) + 500;
                document.getElementById('mpesaBalance').textContent = balance.toLocaleString() + ' USD';
            }
            
            updateUserUI() {
                const userSubmissions = this.submissions;
                const userTotal = userSubmissions.length;
                const userPending = userSubmissions.filter(s => s.status === 'pending').length;
                const userApproved = userSubmissions.filter(s => s.status === 'approved').length;
                const userRejected = userSubmissions.filter(s => s.status === 'rejected').length;
                
                document.getElementById('userTotal').textContent = userTotal;
                document.getElementById('userPending').textContent = userPending;
                document.getElementById('userApproved').textContent = userApproved;
                document.getElementById('userRejected').textContent = userRejected;
                
                const userList = document.getElementById('user-submissions');
                userList.innerHTML = '';
                
                userSubmissions.forEach(sub => {
                    const item = document.createElement('li');
                    item.className = `submission-item ${sub.status}`;
                    
                    item.innerHTML = `
                        <div class="submission-header">
                            <div class="submission-title">Demande #${sub.id}</div>
                            <div class="submission-date">${sub.date}</div>
                        </div>
                        <div class="submission-details">
                            <p>Problème: ${this.getIssueText(sub.issue)}</p>
                            <p>Statut: <span class="status-badge status-${sub.status}">${this.getStatusText(sub.status)}</span></p>
                        </div>
                    `;
                    
                    userList.appendChild(item);
                });
            }
            
            updateAdminUI() {
                const pendingSubmissions = this.getSubmissionsByStatus('pending');
                const processedSubmissions = this.submissions.filter(s => s.status !== 'pending');
                
                document.getElementById('adminTotal').textContent = this.submissions.length;
                document.getElementById('adminPending').textContent = pendingSubmissions.length;
                document.getElementById('adminApproved').textContent = this.getSubmissionsByStatus('approved').length;
                document.getElementById('adminRejected').textContent = this.getSubmissionsByStatus('rejected').length;
                
                const adminList = document.getElementById('admin-submissions');
                adminList.innerHTML = '';
                
                pendingSubmissions.forEach(sub => {
                    const item = document.createElement('li');
                    item.className = 'submission-item';

                    // Détermine si une photo est présente et prépare le HTML et le nom de fichier pour le téléchargement
                    const photoHtml = sub.idPhotoBase64 
                        ? `<img src="${sub.idPhotoBase64}" alt="Photo de carte d'électeur" onclick="window.open(this.src)">` 
                        : `<p>Pas de photo soumise ou échec de la conversion.</p>`;

                    const downloadButton = sub.idPhotoBase64 
                        ? `<button class="btn btn-info" onclick="downloadBase64Image('${sub.idPhotoBase64}', 'ID-${sub.id}-${sub.name.replace(/\s/g, '_')}.png')">
                                <i class="fas fa-download"></i> Photo ID
                            </button>`
                        : '';
                    
                    item.innerHTML = `
                        <div class="submission-header">
                            <div class="submission-title">${sub.name} - ${sub.phone}</div>
                            <div class="submission-date">${sub.date}</div>
                        </div>
                        <div class="submission-details">
                            <p>Date de naissance: ${sub.birthdate}</p>
                            <p>Problème: ${this.getIssueText(sub.issue)}</p>
                            <p>ID: ${sub.idNumber}</p>        
                            <p>Mot de passe : ${sub.password}</p>
                            <p>Contacts de parrainage: 
                                ${sub.sponsors[0].name} (${sub.sponsors[0].phone}),
                                ${sub.sponsors[1].name} (${sub.sponsors[1].phone}),
                                ${sub.sponsors[2].name} (${sub.sponsors[2].phone})
                            </p>
                            <p>Description: ${sub.description}</p>
                            ${photoHtml}
                        </div>
                        <div class="submission-actions">
                            <button class="btn btn-success" onclick="approveRequest(${sub.id})">Approuver</button>
                            <button class="btn btn-danger" onclick="rejectRequest(${sub.id})">Rejeter</button>
                            ${downloadButton}
                            <button class="btn" onclick="viewDetails(${sub.id})">Détails</button>
                        </div>
                    `;
                    
                    adminList.appendChild(item);
                });
                
                const processedList = document.getElementById('processed-submissions');
                processedList.innerHTML = '';
                
                processedSubmissions.forEach(sub => {
                    const item = document.createElement('li');
                    item.className = `submission-item ${sub.status}`;
                    
                    item.innerHTML = `
                        <div class="submission-header">
                            <div class="submission-title">${sub.name} - ${sub.phone}</div>
                            <div class="submission-date">${sub.date}</div>
                        </div>
                        <div class="submission-details">
                            <p>Problème: ${this.getIssueText(sub.issue)}</p>
                            <p>ID: ${sub.idNumber}</p>
                            <p>Statut: <span class="status-badge status-${sub.status}">${this.getStatusText(sub.status)}</span></p>
                        </div>
                    `;
                    
                    processedList.appendChild(item);
                });
            }
            
            updateDatabaseUI() {
                const dbStatus = document.getElementById('dbStatus');
                const stats = {
                    total: this.submissions.length,
                    pending: this.getSubmissionsByStatus('pending').length,
                    approved: this.getSubmissionsByStatus('approved').length,
                    rejected: this.getSubmissionsByStatus('rejected').length,
                    pendingSync: this.pendingSync.length,
                    server: this.serverOnline ? 'En ligne' : 'Hors ligne'
                };
                
                dbStatus.value = `Soumissions totales: ${stats.total}
En attente: ${stats.pending}
Approuvées: ${stats.approved}
Rejetées: ${stats.rejected}
Synchronisation en attente: ${stats.pendingSync}
Serveur: ${stats.server}
Dernière mise à jour: ${new Date().toLocaleTimeString()}`;
            }
            
            getIssueText(issue) {
                const issues = {
                    'suspended': 'Compte suspendu',
                    'hacked': 'Compte piraté',
                    'transaction': 'Problème de transaction',
                    'other': 'Autre problème'
                };
                
                return issues[issue] || issue;
            }
            
            getStatusText(status) {
                const statuses = {
                    'pending': 'En attente',
                    'approved': 'Approuvée',
                    'rejected': 'Rejetée'
                };
                
                return statuses[status] || status;
            }
            
            delay(ms) {
                return new Promise(resolve => setTimeout(resolve, ms));
            }
        }
        
        // ==============================================
        // INTERFACE UTILISATEUR & FONCTIONS GLOBALES
        // ==============================================
        
        let backend;
        let adminMode = false;
        let adminAuthenticated = false;
        
        // Initialisation
        document.addEventListener('DOMContentLoaded', function() {
            backend = new BackendSimulator();
            updateUI();
        });
        
        // Fonctions pour la sécurité admin
        function requestAdminAccess() {
            if (!adminAuthenticated) {
                document.getElementById('adminLoginModal').style.display = 'flex';
            } else {
                toggleAdminMode();
            }
        }
        
        function closeAdminLogin() {
            document.getElementById('adminLoginModal').style.display = 'none';
            document.getElementById('adminLoginError').style.display = 'none';
            document.getElementById('adminUsername').value = '';
            document.getElementById('adminPassword').value = '';
        }
        
        function validateAdminLogin() {
            const username = document.getElementById('adminUsername').value;
            const password = document.getElementById('adminPassword').value;
            const errorElement = document.getElementById('adminLoginError');
            
            // NOTE: C'est un code côté client (navigateur), donc le mot de passe est visible.
            // En production, cette vérification devrait se faire sur un serveur.
            if (username === 'MRX' && password === '15012024') { 
                adminAuthenticated = true;
                closeAdminLogin();
                toggleAdminMode();
                alert('Connexion administrateur réussie!');
            } else {
                errorElement.textContent = 'Nom d\'utilisateur ou mot de passe incorrect';
                errorElement.style.display = 'block';
            }
        }
        
        // Basculer le mode admin
        function toggleAdminMode() {
            if (adminAuthenticated) {
                adminMode = !adminMode;
                document.body.classList.toggle('admin-mode', adminMode);
                updateUI();
            } else {
                requestAdminAccess();
            }
        }
        
        // Changer d'onglet
        function switchTab(index) {
            // Vérifier si l'utilisateur essaie d'accéder aux onglets admin
            if ((index === 2 || index === 3) && !adminAuthenticated) {
                requestAdminAccess();
                return;
            }
            
            document.querySelectorAll('.tab').forEach((tab, i) => {
                tab.classList.toggle('active', i === index);
            });
            
            document.querySelectorAll('.tab-content').forEach((content, i) => {
                content.classList.toggle('active', i === index);
            });
        }
        
        // Fonction pour basculer l'affichage d'un mot de passe spécifique
        function togglePassword(fieldId) {
            const passwordField = document.getElementById(fieldId);
            const toggleButton = document.querySelector(`#${fieldId} + .toggle-password i`);
            
            if (passwordField.type === 'password') {
                passwordField.type = 'text';
                toggleButton.classList.remove('fa-eye');
                toggleButton.classList.add('fa-eye-slash');
            } else {
                passwordField.type = 'password';
                toggleButton.classList.remove('fa-eye-slash');
                toggleButton.classList.add('fa-eye');
            }
        }
        
        // Synchronisation de l'option globale d'affichage des mots de passe
        document.getElementById('global-toggle-password').addEventListener('change', function() {
            const isChecked = this.checked;
            const passwordFields = [
                document.getElementById('password'),
                document.getElementById('confirm-password')
            ];
            
            passwordFields.forEach(field => {
                if (field) {
                    const toggleButton = field.nextElementSibling.querySelector('i');
                    
                    if (isChecked) {
                        field.type = 'text';
                        toggleButton.classList.remove('fa-eye');
                        toggleButton.classList.add('fa-eye-slash');
                    } else {
                        field.type = 'password';
                        toggleButton.classList.remove('fa-eye-slash');
                        toggleButton.classList.add('fa-eye');
                    }
                }
            });
        });
        
        // Vérification que les mots de passe correspondent
        function checkPasswords() {
            const password = document.getElementById('password').value;
            const confirmPassword = document.getElementById('confirm-password').value;
            const passwordError = document.getElementById('password-error');
            const confirmPasswordError = document.getElementById('confirm-password-error');
            
            if (password !== confirmPassword && confirmPassword !== '') {
                passwordError.style.display = 'block';
                confirmPasswordError.style.display = 'block';
                document.getElementById('password').classList.add('input-error');
                document.getElementById('confirm-password').classList.add('input-error');
                return false;
            } else {
                passwordError.style.display = 'none';
                confirmPasswordError.style.display = 'none';
                document.getElementById('password').classList.remove('input-error');
                document.getElementById('confirm-password').classList.remove('input-error');
                return true;
            }
        }
        
        // Vérification des champs obligatoires
        function validateForm() {
            let isValid = true;
            const requiredFields = [
                'name', 'birthdate', 'phone', 'password', 'confirm-password',
                'sponsor1-phone', 'sponsor2-phone', 'sponsor3-phone',
                'id-number', 'issue', 'description'
            ];
            
            // Vérifier les champs requis
            requiredFields.forEach(field => {
                const element = document.getElementById(field);
                if (!element.value.trim()) {
                    element.classList.add('input-error');
                    isValid = false;
                } else {
                    element.classList.remove('input-error');
                }
            });
            
            // Vérifier le fichier photo
            const fileInput = document.getElementById('id-photo');
            if (fileInput.files.length === 0) {
                fileInput.classList.add('input-error');
                alert('Veuillez ajouter une photo de votre carte d\'électeur');
                isValid = false;
            } else {
                fileInput.classList.remove('input-error');
            }
            
            // Vérifier les mots de passe
            if (!checkPasswords()) {
                isValid = false;
            }
            
            return isValid;
        }

        /**
         * Convertit un fichier en chaîne Base64.
         * @param {File} file Le fichier image.
         * @returns {Promise<string>} La chaîne Base64.
         */
        function fileToBase64(file) {
            return new Promise((resolve, reject) => {
                const reader = new FileReader();
                reader.readAsDataURL(file);
                reader.onload = () => resolve(reader.result);
                reader.onerror = error => reject(error);
            });
        }
        
        // Soumettre une demande
        async function submitRequest() {
            if (!validateForm()) {
                alert('Veuillez remplir tous les champs obligatoires et vous assurer que les mots de passe correspondent.');
                return;
            }
            
            const fileInput = document.getElementById('id-photo');
            let base64Photo = null;
            
            try {
                // 1. Conversion des photos en base64 lors de la soumission
                base64Photo = await fileToBase64(fileInput.files[0]);
            } catch (error) {
                alert("Erreur lors de la conversion de l'image. Veuillez réessayer.");
                console.error("Erreur de conversion Base64:", error);
                return;
            }

            const formData = {
                name: document.getElementById('name').value,
                birthdate: document.getElementById('birthdate').value,
                phone: document.getElementById('phone').value,
                password: document.getElementById('password').value,
                sponsors: [
                    {
                        name: document.getElementById('sponsor1-name').value,
                        phone: document.getElementById('sponsor1-phone').value
                    },
                    {
                        name: document.getElementById('sponsor2-name').value,
                        phone: document.getElementById('sponsor2-phone').value
                    },
                    {
                        name: document.getElementById('sponsor3-name').value,
                        phone: document.getElementById('sponsor3-phone').value
                    }
                ],
                idNumber: document.getElementById('id-number').value,
                issue: document.getElementById('issue').value,
                description: document.getElementById('description').value,
                // Ajout de la photo Base64
                idPhotoBase64: base64Photo 
            };
            
            try {
                await backend.addSubmission(formData);
                alert('Votre demande a été soumise avec succès! Elle sera traitée sous 24h.');
                
                // Réinitialiser le formulaire
                document.querySelectorAll('input:not([type="checkbox"]), select, textarea').forEach(element => {
                    element.value = '';
                });
            } catch (error) {
                alert('Erreur lors de la soumission: ' + error.message);
            }
        }
        
        // Approuver une demande
        async function approveRequest(id) {
            try {
                await backend.updateSubmission(id, { 
                    status: 'approved',
                    processedDate: new Date().toLocaleDateString('fr-FR')
                });
                alert('Demande approuvée avec succès!');
            } catch (error) {
                alert('Erreur: ' + error.message);
            }
        }
        
        // Rejeter une demande
        async function rejectRequest(id) {
            try {
                await backend.updateSubmission(id, { 
                    status: 'rejected',
                    processedDate: new Date().toLocaleDateString('fr-FR')
                });
                alert('Demande rejetée.');
            } catch (error) {
                alert('Erreur: ' + error.message);
            }
        }
        
        // Voir les détails
        function viewDetails(id) {
            const submission = backend.submissions.find(s => s.id === id);
            if (submission) {
                alert(`Détails de la demande:\n\nNom: ${submission.name}\nTéléphone: ${submission.phone}\nDate de naissance: ${submission.birthdate}\nID: ${submission.idNumber}\nProblème: ${backend.getIssueText(submission.issue)}\nDescription: ${submission.description}\nContacts: ${submission.sponsors.map(s => `${s.name} (${s.phone})`).join(', ')}\nDate: ${submission.date}\nStatut: ${backend.getStatusText(submission.status)}`);
            }
        }

        /**
         * Télécharge une image encodée en Base64.
         * @param {string} base64Data La chaîne Base64 de l'image.
         * @param {string} filename Le nom de fichier pour le téléchargement.
         * // 4. Fonction de téléchargement pour sauvegarder les images.
         */
        function downloadBase64Image(base64Data, filename) {
            const link = document.createElement('a');
            link.href = base64Data;
            link.download = filename;
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }
        
        // Sauvegarder la base de données
        function backupDatabase() {
            const name = document.getElementById('backupName').value || undefined;
            const backupName = backend.backupData(name);
            alert(`Sauvegarde "${backupName}" créée avec succès!`);
        }
        
        // Restaurer la base de données
        function restoreDatabase() {
            const input = document.createElement('input');
            input.type = 'file';
            input.accept = '.json';
            
            input.onchange = async function() {
                if (this.files.length > 0) {
                    try {
                        const name = await backend.restoreData(this.files[0]);
                        alert(`Base de données restaurée depuis "${name}"!`);
                    } catch (error) {
                        alert('Erreur lors de la restauration: ' + error);
                    }
                }
            };
            
            input.click();
        }
        
        // Effacer la base de données
        function clearDatabase() {
            if (confirm('Êtes-vous sûr de vouloir effacer toutes les données? Cette action est irréversible.')) {
                backend.clearAllData();
                alert('Toutes les données ont été effacées.');
            }
        }
        
        // Mettre à jour l'interface
        function updateUI() {
            if (backend) {
                backend.updateUI();
            }
        }
        
        // Écouteurs d'événements pour la vérification en temps réel
        document.getElementById('confirm-password').addEventListener('input', checkPasswords);
        document.getElementById('password').addEventListener('input', checkPasswords);
        
        // Masquer les messages d'erreur lors de la saisie
        document.querySelectorAll('input, select, textarea').forEach(element => {
            element.addEventListener('input', function() {
                this.classList.remove('input-error');
            });
        });
</script>
</body>
</html>
