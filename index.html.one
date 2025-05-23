<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>BETWINS - Inscripción</title>
  <script src="https://unpkg.com/@supabase/supabase-js"></script>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: url('betwins_background_watermark.png') no-repeat center center fixed;
      background-size: cover;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
      flex-direction: column;
      backdrop-filter: brightness(0.9);
    }

    .formulario {
      background-color: rgba(255, 255, 255, 0.85);
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.2);
      text-align: center;
    }

    h1 {
      color: #333;
      margin-bottom: 20px;
    }

    input {
      padding: 10px;
      width: 280px;
      font-size: 16px;
      border: 1px solid #ccc;
      border-radius: 5px;
      margin-bottom: 15px;
    }

    button {
      padding: 10px 20px;
      font-size: 16px;
      background-color: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background-color: #0056b3;
    }

    .mensaje {
      margin-top: 15px;
      font-size: 14px;
      color: green;
    }

    .error {
      color: red;
    }
  </style>
</head>
<body>
  <div class="formulario">
    <h1>Inscribite al Sorteo BETWINS</h1>
    <input type="text" id="usuario" placeholder="Nombre de usuario" required />
    <br />
    <button onclick="inscribirse()">Inscribirme</button>
    <p class="mensaje" id="mensaje"></p>
  </div>

  <script>
    const supabaseUrl = 'https://dmmbpeawuipjeufzcqqz.supabase.co';
    const supabaseKey = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImRtbWJwZWF3dWlwamV1ZnpjcXF6Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NDc3OTYyMDcsImV4cCI6MjA2MzM3MjIwN30.VIPMc_f7DFds8t86Ggz3iQYRRZaU6fEwAakd34iKYaI';
    const supabase = supabase.createClient(supabaseUrl, supabaseKey);

    async function inscribirse() {
      const usuarioInput = document.getElementById('usuario');
      const mensaje = document.getElementById('mensaje');
      const usuario = usuarioInput.value.trim().toLowerCase();
      mensaje.textContent = '';
      mensaje.classList.remove('error');

      if (!usuario) {
        mensaje.textContent = 'Por favor, ingresá un nombre de usuario.';
        mensaje.classList.add('error');
        return;
      }

      const { data: existente, error: errorCheck } = await supabase
        .from('usuarios')
        .select('USUARIO')
        .eq('USUARIO', usuario)
        .single();

      if (existente) {
        mensaje.textContent = 'Este usuario ya está inscrito.';
        mensaje.classList.add('error');
        return;
      }

      const { error } = await supabase
        .from('usuarios')
        .insert([{ USUARIO: usuario }]);

      if (error) {
        mensaje.textContent = 'Error al inscribirse. Intentá de nuevo.';
        mensaje.classList.add('error');
      } else {
        mensaje.textContent = '¡Inscripción exitosa!';
        usuarioInput.value = '';
      }
    }
  </script>
</body>
</html>
