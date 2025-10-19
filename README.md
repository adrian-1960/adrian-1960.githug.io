<!DOCTYPE html>
<html>
<head>
  <title>Datos del ESP32</title>
  <script src="https://www.gstatic.com/firebasejs/10.5.0/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/10.5.0/firebase-database.js"></script>
</head>
<body>
  <h2>📡 Datos en tiempo real</h2>
  <p>🌡️ Temperatura: <span id="temp">--</span> °C</p>
  <p>💧 Humedad: <span id="hum">--</span> %</p>
  <p>🌞 Luz: <span id="luz">--</span></p>

  <script>
    // 🔧 Configura tu Firebase
    const firebaseConfig = {
      apiKey:"AIzaSyAhDUAaGEsfArtml5dvf49DtobpWmrmBJA",
      authDomain:"esp32-s3-adr.firebaseapp.com",
      databaseURL:"https://esp32-s3-adr-default-rtdb.firebaseio.com",
      projectId:"esp32-s3-adr",
      storageBucket:"esp32-s3-adr.firebasestorage.app",
      messagingSenderId:"22420972699",
      appId: "1:22420972699:web:b6bb1f65e2fc49da1c923e",
    };

    // 🔌 Inicializa Firebase
    const app = firebase.initializeApp(firebaseConfig);
    const db = firebase.database();

    // 📥 Escucha los datos
    db.ref("datos").on("value", (snapshot) => {
      const data = snapshot.val();
      document.getElementById("temp").textContent = data.temperatura;
      document.getElementById("hum").textContent = data.humedad;
      document.getElementById("luz").textContent = data.luz;
    });
  </script>
</body>
</html>
