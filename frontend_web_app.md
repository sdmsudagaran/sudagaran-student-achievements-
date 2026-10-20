<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sudagaran Student Achievements</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Manrope:wght@400;500;600;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --primary: #152B4A;
      --secondary: #315EE8;
      --secondary-hover: #264ac2;
      --bg-color: #F4F7F9;
      --card-bg: #FFFFFF;
      --text-main: #333333;
      --text-muted: #666666;
      --border-color: #E2E8F0;
      --error: #DC2626;
      --success: #059669;
      --radius: 12px;
      --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Manrope', sans-serif;
      background-color: var(--bg-color);
      color: var(--text-main);
      line-height: 1.6;
      display: flex;
      flex-direction: column;
      align-items: center;
      min-height: 100vh;
    }

    .container {
      width: 100%;
      max-width: 800px;
      padding: 2rem 1.5rem;
      margin: 0 auto;
    }

    /* Header & Logo */
    .header-logo {
      text-align: center;
      margin-bottom: 2rem;
    }
    .header-logo img {
      max-width: 150px;
      height: auto;
    }

    /* Card Layout */
    .card {
      background: var(--card-bg);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding: 2rem;
      border: 1px solid var(--border-color);
      transition: opacity 0.3s ease;
    }

    .hidden {
      display: none !important;
    }

    h1, h2 {
      color: var(--primary);
      text-align: center;
      margin-bottom: 0.5rem;
    }

    p.subtitle {
      text-align: center;
      color: var(--text-muted);
      margin-bottom: 2rem;
      font-size: 0.95rem;
    }

    /* Form Styles */
    .form-group {
      margin-bottom: 1.5rem;
    }

    .form-row {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1.5rem;
    }

    label {
      display: block;
      font-weight: 600;
      margin-bottom: 0.5rem;
      color: var(--primary);
      font-size: 0.9rem;
    }

    .required {
      color: var(--error);
    }

    input, select, textarea {
      width: 100%;
      padding: 0.75rem 1rem;
      border: 1px solid var(--border-color);
      border-radius: 8px;
      font-family: inherit;
      font-size: 1rem;
      color: var(--text-main);
      background-color: #F8FAFC;
      transition: border-color 0.2s, box-shadow 0.2s;
    }

    input:focus, select:focus {
      outline: none;
      border-color: var(--secondary);
      box-shadow: 0 0 0 3px rgba(49, 94, 232, 0.1);
      background-color: #FFFFFF;
    }

    input[readonly] {
      background-color: #E2E8F0;
      color: var(--text-muted);
      cursor: not-allowed;
    }

    .file-input-wrapper {
      position: relative;
      border: 2px dashed var(--border-color);
      border-radius: 8px;
      padding: 2rem;
      text-align: center;
      background: #F8FAFC;
      cursor: pointer;
      transition: border-color 0.2s;
    }

    .file-input-wrapper:hover {
      border-color: var(--secondary);
    }

    .file-input-wrapper input[type="file"] {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      opacity: 0;
      cursor: pointer;
    }

    .file-info {
      margin-top: 0.5rem;
      font-size: 0.85rem;
      color: var(--text-muted);
    }

    /* Buttons */
    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      padding: 0.75rem 1.5rem;
      font-weight: 600;
      border-radius: 8px;
      border: none;
      cursor: pointer;
      font-family: inherit;
      font-size: 1rem;
      transition: all 0.2s;
    }

    .btn-primary {
      background-color: var(--secondary);
      color: white;
      width: 100%;
    }

    .btn-primary:hover {
      background-color: var(--secondary-hover);
    }

    .btn-secondary {
      background-color: transparent;
      color: var(--text-muted);
      border: 1px solid var(--border-color);
    }

    .btn-secondary:hover {
      background-color: #F8FAFC;
      color: var(--text-main);
    }

    .btn-danger {
      background-color: transparent;
      color: var(--error);
      border: 1px solid rgba(220, 38, 38, 0.3);
    }
    
    .btn-danger:hover {
      background-color: #FEF2F2;
    }

    .form-actions {
      display: flex;
      gap: 1rem;
      margin-top: 2rem;
      padding-top: 1.5rem;
      border-top: 1px solid var(--border-color);
    }

    .form-actions .btn {
      flex: 1;
    }

    /* Alerts */
    .alert {
      padding: 1rem;
      border-radius: 8px;
      margin-bottom: 1.5rem;
      font-size: 0.9rem;
      display: none;
    }
    .alert.show {
      display: block;
    }
    .alert-error {
      background-color: #FEF2F2;
      color: var(--error);
      border: 1px solid #FCA5A5;
    }
    .alert-success {
      background-color: #ECFDF5;
      color: var(--success);
      border: 1px solid #6EE7B7;
    }

    /* User Profile Header */
    .profile-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background: var(--primary);
      color: white;
      padding: 1rem 1.5rem;
      border-radius: var(--radius);
      margin-bottom: 2rem;
    }
    .profile-info h3 {
      font-size: 1.1rem;
      margin-bottom: 0.2rem;
    }
    .profile-info p {
      font-size: 0.85rem;
      opacity: 0.8;
    }

    /* Loader */
    .loader-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(255, 255, 255, 0.8);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 9999;
      visibility: hidden;
      opacity: 0;
      transition: opacity 0.3s;
    }
    .loader-overlay.active {
      visibility: visible;
      opacity: 1;
    }
    .spinner {
      width: 40px;
      height: 40px;
      border: 4px solid #E2E8F0;
      border-top: 4px solid var(--secondary);
      border-radius: 50%;
      animation: spin 1s linear infinite;
      margin-bottom: 1rem;
    }
    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    /* Responsive */
    @media (max-width: 640px) {
      .form-row {
        grid-template-columns: 1fr;
        gap: 0;
      }
      .form-actions {
        flex-direction: column-reverse;
      }
      .profile-header {
        flex-direction: column;
        align-items: flex-start;
        gap: 1rem;
      }
      .profile-header .btn {
        width: 100%;
      }
    }
  </style>
</head>
<body>

  <!-- Loading Overlay -->
  <div id="loader" class="loader-overlay">
    <div class="spinner"></div>
    <div id="loader-text" style="color: var(--primary); font-weight: 600;">Memproses...</div>
  </div>

  <div class="container">
    <div class="header-logo">
      <img src="https://i.ibb.co.com/vCKNHYDW/logo-sekolah1.png" alt="Logo Sekolah Sudagaran">
    </div>

    <!-- VIEW: LOGIN -->
    <div id="view-login" class="card">
      <h1>Portal Prestasi Siswa</h1>
      <p class="subtitle">Masuk menggunakan Nomor Induk Siswa (NIS) untuk mencatat prestasi Anda.</p>
      
      <div id="login-alert" class="alert alert-error"></div>

      <form id="form-login" onsubmit="handleLogin(event)">
        <div class="form-group">
          <label for="login-nis">Nomor Induk Siswa (NIS)</label>
          <input type="text" id="login-nis" placeholder="Masukkan NIS Anda" required autocomplete="off">
        </div>
        <button type="submit" class="btn btn-primary">Masuk</button>
      </form>
    </div>

    <!-- VIEW: DASHBOARD / FORM -->
    <div id="view-dashboard" class="hidden">
      
      <div class="profile-header">
        <div class="profile-info">
          <h3 id="display-nama">Nama Siswa</h3>
          <p>NIS: <span id="display-nis"></span> | Kelas: <span id="display-kelas"></span></p>
        </div>
        <button type="button" class="btn btn-danger" onclick="logout()" style="color: white; border-color: rgba(255,255,255,0.3);">Keluar</button>
      </div>

      <div class="card">
        <h2>Formulir Prestasi</h2>
        <p class="subtitle">Catat Prestasi, Inspirasi Masa Depan</p>

        <div id="form-alert" class="alert"></div>

        <form id="form-achievement" onsubmit="handleSubmit(event)">
          
          <!-- Informasi Kejuaraan -->
          <div class="form-group">
            <label for="event-name">Nama Event Kejuaraan <span class="required">*</span></label>
            <input type="text" id="event-name" required placeholder="Contoh: OSN Tingkat Provinsi, O2SN Kabupaten">
          </div>

          <div class="form-row">
            <div class="form-group">
              <label for="achievement">Juara / Capaian <span class="required">*</span></label>
              <select id="achievement" required onchange="handleAchievementChange()">
                <option value="" disabled selected>Pilih Capaian...</option>
                <option value="Juara 1">Juara 1</option>
                <option value="Juara 2">Juara 2</option>
                <option value="Juara 3">Juara 3</option>
                <option value="Harapan 1">Harapan 1</option>
                <option value="Harapan 2">Harapan 2</option>
                <option value="Harapan 3">Harapan 3</option>
                <option value="Finalis">Finalis</option>
                <option value="Peserta">Peserta</option>
                <option value="Medali Emas">Medali Emas</option>
                <option value="Medali Perak">Medali Perak</option>
                <option value="Medali Perunggu">Medali Perunggu</option>
                <option value="Lainnya">Lainnya</option>
              </select>
            </div>
            
            <div class="form-group hidden" id="achievement-other-group">
              <label for="achievement-other">Sebutkan Capaian <span class="required">*</span></label>
              <input type="text" id="achievement-other" placeholder="Ketik capaian lainnya">
            </div>
          </div>

          <div class="form-row">
            <div class="form-group">
              <label for="category">Kategori <span class="required">*</span></label>
              <select id="category" required>
                <option value="" disabled selected>Pilih Kategori...</option>
                <option value="Akademik">Akademik</option>
                <option value="Non Akademik">Non Akademik</option>
              </select>
            </div>
            <div class="form-group">
              <label for="branch">Cabang Lomba <span class="required">*</span></label>
              <input type="text" id="branch" required placeholder="Contoh: Matematika, Renang, Pidato">
            </div>
          </div>

          <div class="form-row">
            <div class="form-group">
              <label for="date">Waktu Pelaksanaan <span class="required">*</span></label>
              <input type="date" id="date" required>
            </div>
            <div class="form-group">
              <label for="organizer">Penyelenggara <span class="required">*</span></label>
              <select id="organizer" required>
                <option value="" disabled selected>Pilih Penyelenggara...</option>
                <option value="Pemerintah (Puspresnas, Dinas, dll)">Pemerintah (Puspresnas, Dinas, dll)</option>
                <option value="Institusi Pendidikan / Sekolah">Institusi Pendidikan / Sekolah</option>
                <option value="Non Pemerintah / Yayasan / Swasta">Non Pemerintah / Yayasan / Swasta</option>
              </select>
            </div>
          </div>

          <!-- File Upload -->
          <div class="form-group">
            <label>Sertifikat / Piagam <span class="required">*</span></label>
            <div class="file-input-wrapper">
              <input type="file" id="certificate" accept=".pdf, .jpg, .jpeg, .png" required onchange="handleFileChange()">
              <div id="file-display">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="var(--secondary)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="margin-bottom: 8px;"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path><polyline points="17 8 12 3 7 8"></polyline><line x1="12" y1="3" x2="12" y2="15"></line></svg>
                <p>Klik atau seret file ke sini untuk mengunggah</p>
                <p class="file-info">Mendukung PDF, JPG, PNG. Maksimal 8 MB.</p>
              </div>
            </div>
          </div>

          <div class="form-actions">
            <button type="button" class="btn btn-secondary" onclick="resetForm()">Reset Formulir</button>
            <button type="submit" class="btn btn-primary">Kirim Data Prestasi</button>
          </div>
        </form>
      </div>
    </div>
  </div>

  <script>
    // State Management
    let session = {
      nis: null,
      token: null,
      nama: null,
      kelas: null
    };

    let base64File = null;
    const MAX_FILE_SIZE = 8 * 1024 * 1024; // 8 MB

    // UI Helpers
    function showLoader(text = 'Memproses...') {
      document.getElementById('loader-text').innerText = text;
      document.getElementById('loader').classList.add('active');
    }

    function hideLoader() {
      document.getElementById('loader').classList.remove('active');
    }

    function showAlert(elementId, message, type) {
      const alertEl = document.getElementById(elementId);
      alertEl.innerText = message;
      alertEl.className = `alert alert-${type} show`;
      alertEl.scrollIntoView({ behavior: 'smooth', block: 'center' });
    }

    function hideAlert(elementId) {
      document.getElementById(elementId).classList.remove('show');
    }

    function switchView(viewName) {
      document.getElementById('view-login').classList.add('hidden');
      document.getElementById('view-dashboard').classList.add('hidden');
      document.getElementById(`view-${viewName}`).classList.remove('hidden');
      window.scrollTo(0,0);
    }

    // Login Flow
    function handleLogin(event) {
      event.preventDefault();
      hideAlert('login-alert');
      const nisInput = document.getElementById('login-nis').value.trim();

      if (!nisInput) return;

      showLoader('Memverifikasi data siswa...');
      
      google.script.run
        .withSuccessHandler(function(response) {
          hideLoader();
          if (response.success) {
            session = response.data;
            document.getElementById('display-nama').innerText = session.nama;
            document.getElementById('display-nis').innerText = session.nis;
            document.getElementById('display-kelas').innerText = session.kelas;
            
            document.getElementById('form-login').reset();
            switchView('dashboard');
          } else {
            showAlert('login-alert', response.message, 'error');
          }
        })
        .withFailureHandler(function(error) {
          hideLoader();
          showAlert('login-alert', 'Kesalahan jaringan: ' + error.message, 'error');
        })
        .loginStudent(nisInput);
    }

    function logout() {
      session = { nis: null, token: null, nama: null, kelas: null };
      resetForm();
      hideAlert('form-alert');
      switchView('login');
    }

    // Form Interactions
    function handleAchievementChange() {
      const select = document.getElementById('achievement');
      const otherGroup = document.getElementById('achievement-other-group');
      const otherInput = document.getElementById('achievement-other');
      
      if (select.value === 'Lainnya') {
        otherGroup.classList.remove('hidden');
        otherInput.required = true;
      } else {
        otherGroup.classList.add('hidden');
        otherInput.required = false;
        otherInput.value = '';
      }
    }

    function handleFileChange() {
      const input = document.getElementById('certificate');
      const display = document.getElementById('file-display');
      const file = input.files[0];
      base64File = null;

      if (!file) {
        display.innerHTML = `
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="var(--secondary)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="margin-bottom: 8px;"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path><polyline points="17 8 12 3 7 8"></polyline><line x1="12" y1="3" x2="12" y2="15"></line></svg>
          <p>Klik atau seret file ke sini untuk mengunggah</p>
          <p class="file-info">Mendukung PDF, JPG, PNG. Maksimal 8 MB.</p>
        `;
        return;
      }

      if (file.size > MAX_FILE_SIZE) {
        alert('Ukuran file melebihi 8 MB. Silakan kompres file Anda.');
        input.value = ''; 
        return;
      }

      const reader = new FileReader();
      reader.onload = function(e) {
        const result = e.target.result;
        base64File = result.split(',')[1];
        
        display.innerHTML = `
          <strong style="color: var(--primary);">${file.name}</strong>
          <p class="file-info">Ukuran: ${(file.size / (1024*1024)).toFixed(2)} MB | Siap diunggah</p>
        `;
      };
      reader.onerror = function(e) {
        alert('Gagal membaca file.');
        input.value = '';
      };
      reader.readAsDataURL(file);
    }

    function resetForm() {
      document.getElementById('form-achievement').reset();
      handleAchievementChange();
      document.getElementById('certificate').value = '';
      handleFileChange(); 
    }

    // Submission
    function handleSubmit(event) {
      event.preventDefault();
      hideAlert('form-alert');

      if (!session.nis || !session.token) {
        showAlert('form-alert', 'Sesi Anda telah berakhir. Silakan logout dan login kembali.', 'error');
        return;
      }

      const fileInput = document.getElementById('certificate');
      if (!fileInput.files.length || !base64File) {
        showAlert('form-alert', 'Silakan pilih file sertifikat/piagam terlebih dahulu.', 'error');
        return;
      }

      const file = fileInput.files[0];
      let achievementVal = document.getElementById('achievement').value;
      if (achievementVal === 'Lainnya') {
        achievementVal = document.getElementById('achievement-other').value.trim();
      }

      const payload = {
        nis: session.nis,
        token: session.token,
        eventName: document.getElementById('event-name').value.trim(),
        achievement: achievementVal,
        category: document.getElementById('category').value,
        branch: document.getElementById('branch').value.trim(),
        date: document.getElementById('date').value,
        organizer: document.getElementById('organizer').value,
        fileName: file.name,
        mimeType: file.type,
        fileBase64: base64File
      };

      showLoader('Mengunggah file dan menyimpan data...');

      google.script.run
        .withSuccessHandler(function(response) {
          hideLoader();
          if (response.success) {
            resetForm();
            showAlert('form-alert', `${response.message} (ID: ${response.recordId})`, 'success');
          } else {
            showAlert('form-alert', response.message, 'error');
          }
        })
        .withFailureHandler(function(error) {
          hideLoader();
          showAlert('form-alert', 'Terjadi kesalahan sistem: ' + error.message, 'error');
        })
        .submitAchievement(payload);
    }
  </script>
</body>
</html>