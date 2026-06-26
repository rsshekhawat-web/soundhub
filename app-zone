<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AppZone - App Uploader & Downloader</title>
    <style>
        :root {
            --bg-color: #0f172a;
            --card-bg: #1e293b;
            --accent-color: #3b82f6;
            --accent-hover: #2563eb;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --success: #10b981;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            padding-bottom: 60px;
        }

        /* Header Style */
        header {
            background-color: var(--card-bg);
            padding: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid #334155;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
        }

        header .logo {
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--accent-color);
        }

        .search-container input {
            background-color: var(--bg-color);
            border: 1px solid #334155;
            color: var(--text-main);
            padding: 10px 20px;
            border-radius: 50px;
            width: 300px;
            outline: none;
            transition: 0.3s;
        }

        .search-container input:focus {
            border-color: var(--accent-color);
        }

        /* Main Container */
        .container {
            max-width: 1200px;
            margin: 40px auto;
            padding: 0 20px;
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 40px;
        }

        @media (max-width: 900px) {
            .container {
                grid-template-columns: 1fr;
            }
        }

        /* Upload Section Card */
        .upload-card {
            background-color: var(--card-bg);
            padding: 30px;
            border-radius: 16px;
            height: fit-content;
            border: 1px solid #334155;
        }

        .upload-card h2 {
            margin-bottom: 20px;
            font-size: 1.4rem;
        }

        .drop-zone {
            border: 2px dashed #475569;
            border-radius: 12px;
            padding: 40px 20px;
            text-align: center;
            cursor: pointer;
            transition: 0.3s;
            margin-bottom: 20px;
        }

        .drop-zone:hover, .drop-zone.drag-over {
            border-color: var(--accent-color);
            background-color: rgba(59, 130, 246, 0.05);
        }

        .drop-zone p {
            color: var(--text-muted);
            margin-top: 10px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: var(--text-muted);
            font-size: 0.9rem;
        }

        .form-group input, .form-group textarea, .form-group select {
            width: 100%;
            background-color: var(--bg-color);
            border: 1px solid #334155;
            color: var(--text-main);
            padding: 12px;
            border-radius: 8px;
            outline: none;
        }

        .form-group input:focus, .form-group textarea:focus {
            border-color: var(--accent-color);
        }

        .submit-btn {
            width: 100%;
            background-color: var(--accent-color);
            color: white;
            border: none;
            padding: 14px;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
            margin-top: 10px;
        }

        .submit-btn:hover {
            background-color: var(--accent-hover);
        }

        /* App Showcase Section */
        .apps-section h2 {
            margin-bottom: 25px;
            font-size: 1.6rem;
        }

        .apps-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 20px;
        }

        .app-card {
            background-color: var(--card-bg);
            border-radius: 16px;
            padding: 20px;
            border: 1px solid #334155;
            transition: 0.3s;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .app-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.3);
        }

        .app-info {
            display: flex;
            gap: 15px;
            margin-bottom: 15px;
        }

        .app-icon {
            width: 60px;
            height: 60px;
            background-color: #475569;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
        }

        .app-details h3 {
            font-size: 1.1rem;
            margin-bottom: 4px;
        }

        .app-details .version {
            font-size: 0.8rem;
            background-color: #334155;
            padding: 2px 8px;
            border-radius: 20px;
            color: var(--text-muted);
        }

        .app-desc {
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-bottom: 20px;
            line-height: 1.5;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }

        .download-btn {
            background-color: #334155;
            color: var(--text-main);
            text-align: center;
            padding: 10px;
            border-radius: 8px;
            text-decoration: none;
            font-weight: 600;
            transition: 0.3s;
        }

        .download-btn:hover {
            background-color: var(--success);
            color: white;
        }
    </style>
</head>
<body>

    <header>
        <div class="logo">🚀 AppZone</div>
        <div class="search-container">
            <input type="text" id="searchBar" placeholder="Search apps or APKs...">
        </div>
    </header>

    <div class="container">
        
        <div class="upload-card">
            <h2>Upload New App</h2>
            <form id="uploadForm">
                <div class="drop-zone" id="dropZone">
                    <span style="font-size: 2rem;">📂</span>
                    <p>Drag & Drop APK/File here <br><span style="font-size: 0.8rem;">or click to browse</span></p>
                    <input type="file" id="fileInput" style="display: none;" required>
                </div>
                
                <div id="fileInfo" style="margin-bottom: 15px; color: var(--success); font-size: 0.9rem; display: none;"></div>

                <div class="form-group">
                    <label for="appName">App Name</label>
                    <input type="text" id="appName" placeholder="e.g. PubG Mobile" required>
                </div>

                <div class="form-group">
                    <label for="appVersion">Version</label>
                    <input type="text" id="appVersion" placeholder="e.g. 1.0.2" required>
                </div>

                <div class="form-group">
                    <label for="appCategory">Category</label>
                    <select id="appCategory">
                        <option value="Games">Games</option>
                        <option value="Tools">Tools</option>
                        <option value="Productivity">Productivity</option>
                        <option value="Social">Social</option>
                    </select>
                </div>

                <div class="form-group">
                    <label for="appDesc">Description</label>
                    <textarea id="appDesc" rows="3" placeholder="Tell users what your app does..." required></textarea>
                </div>

                <button type="submit" class="submit-btn">Publish App</button>
            </form>
        </div>

        <div class="apps-section">
            <h2>Available Applications</h2>
            <div class="apps-grid" id="appsGrid">
                
                <div class="app-card" data-name="pixel racer">
                    <div>
                        <div class="app-info">
                            <div class="app-icon" style="background-color: #f59e0b;">🏎️</div>
                            <div class="app-details">
                                <h3>Pixel Racer</h3>
                                <span class="version">v2.4 (Games)</span>
                            </div>
                        </div>
                        <p class="app-desc">An exciting retro style 2D racing game with ultimate car tuning features and fast tracks.</p>
                    </div>
                    <a href="#" class="download-btn" onclick="alert('Downloading Pixel Racer APK...')">Download APK</a>
                </div>

                <div class="app-card" data-name="secure vpn">
                    <div>
                        <div class="app-info">
                            <div class="app-icon" style="background-color: #10b981;">🛡️</div>
                            <div class="app-details">
                                <h3>Secure VPN</h3>
                                <span class="version">v1.0 (Tools)</span>
                            </div>
                        </div>
                        <p class="app-desc">Protect your online privacy and browse anonymously with high-speed secure global proxy servers.</p>
                    </div>
                    <a href="#" class="download-btn" onclick="alert('Downloading Secure VPN APK...')">Download APK</a>
                </div>

            </div>
        </div>

    </div>

    <script>
        const dropZone = document.getElementById('dropZone');
        const fileInput = document.getElementById('fileInput');
        const fileInfo = document.getElementById('fileInfo');
        const uploadForm = document.getElementById('uploadForm');
        const appsGrid = document.getElementById('appsGrid');
        const searchBar = document.getElementById('searchBar');

        // Drag and drop events
        dropZone.addEventListener('click', () => fileInput.click());

        dropZone.addEventListener('dragover', (e) => {
            e.preventDefault();
            dropZone.classList.add('drag-over');
        });

        dropZone.addEventListener('dragleave', () => {
            dropZone.classList.remove('drag-over');
        });

        dropZone.addEventListener('drop', (e) => {
            e.preventDefault();
            dropZone.classList.remove('drag-over');
            if(e.dataTransfer.files.length) {
                fileInput.files = e.dataTransfer.files;
                showFileName(e.dataTransfer.files[0].name);
            }
        });

        fileInput.addEventListener('change', () => {
            if(fileInput.files.length) showFileName(fileInput.files[0].name);
        });

        function showFileName(name) {
            fileInfo.textContent = `Selected File: ${name}`;
            fileInfo.style.display = 'block';
        }

        // Add App dynamically on Form Submit (Simulation)
        uploadForm.addEventListener('submit', (e) => {
            e.preventDefault();

            const name = document.getElementById('appName').value;
            const version = document.getElementById('appVersion').value;
            const category = document.getElementById('appCategory').value;
            const desc = document.getElementById('appDesc').value;

            // Simple random emoji picker for app icon
            const emojis = ['📱', '🎮', '🎵', '📷', '💬', '🚀', '🔥'];
            const randomEmoji = emojis[Math.floor(Math.random() * emojis.length)];

            // Create new app card element
            const newCard = document.createElement('div');
            newCard.className = 'app-card';
            newCard.setAttribute('data-name', name.toLowerCase());
            newCard.innerHTML = `
                <div>
                    <div class="app-info">
                        <div class="app-icon" style="background-color: #3b82f6;">${randomEmoji}</div>
                        <div class="app-details">
                            <h3>${name}</h3>
                            <span class="version">v${version} (${category})</span>
                        </div>
                    </div>
                    <p class="app-desc">${desc}</p>
                </div>
                <a href="#" class="download-btn" onclick="alert('Downloading ${name} APK...')">Download APK</a>
            `;

            // Insert to the top of the grid
            appsGrid.insertBefore(newCard, appsGrid.firstChild);

            // Reset form
            uploadForm.reset();
            fileInfo.style.display = 'none';
            alert('Success! Your app has been published on the board below.');
        });

        // Search Filter Logic
        searchBar.addEventListener('input', (e) => {
            const term = e.target.value.toLowerCase();
            const cards = document.querySelectorAll('.app-card');
            
            cards.forEach(card => {
                const appName = card.getAttribute('data-name');
                if(appName.includes(term)) {
                    card.style.display = 'flex';
                } else {
                    card.style.display = 'none';
                }
            });
        });
    </script>
</body>
</html>
