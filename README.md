# Restaurante-El-Mexicano-
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Restaurante El Mexicano</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      background-color: #f8f1e7;
    }
    .logo-container {
      display: flex;
      align-items: center;
      gap: 15px;
    }
    h1 {
      color: black;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-bottom: 20px;
    }
    th, td {
      border: 1px solid #999;
      padding: 10px;
      text-align: left;
    }
    .total, .ticket {
      font-size: 1.2em;
      margin-top: 20px;
    }
    button {
      padding: 10px 15px;
      margin-right: 10px;
      background-color: black;
      color: gold;
      border: none;
      cursor: pointer;
    }
    button:hover {
      background-color: #FF00FF;
    }
    #ticket {
      white-space: pre-line;
      background-color: #fff;
      padding: 10px;
      border: 1px dashed #666;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  
    <h1>Restaurante El Mexicano</h1>
  </div>

  <form id="menuForm">
    <h2>Platillos</h2>
    <table>
      <tr><th>Platillo</th><th>Precio</th><th>Cantidad</th></tr>
      <tr><td>Pozole</td><td>$80</td><td><input type="number" name="pozole" value="0" min="0"></td></tr>
      <tr><td>Mole</td><td>$90</td><td><input type="number" name="mole" value="0" min="0"></td></tr>
      <tr><td>Tacos</td><td>$60</td><td><input type="number" name="tacos" value="0" min="0"></td></tr>
      <tr><td>Chiles en nogada</td><td>$100</td><td><input type="number" name="chiles" value="0" min="0"></td></tr>
      <tr><td>Barbacoa</td><td>$120</td><td><input type="number" name="barbacoa" value="0" min="0"></td></tr>
      <tr><td>Carne asada</td><td>$110</td><td><input type="number" name="carne" value="0" min="0"></td></tr>
    </table>

    <h2>Bebidas</h2>
    <table>
      <tr><th>Bebida</th><th>Precio</th><th>Cantidad</th></tr>
      <tr><td>Coca Cola</td><td>$25</td><td><input type="number" name="coca" value="0" min="0"></td></tr>
      <tr><td>Agua de limón</td><td>$20</td><td><input type="number" name="agua" value="0" min="0"></td></tr>
      <tr><td>Michelada</td><td>$45</td><td><input type="number" name="michelada" value="0" min="0"></td></tr>
    </table>

    <h2>Postres</h2>
    <table>
      <tr><th>Postre</th><th>Precio</th><th>Cantidad</th></tr>
      <tr><td>Helado</td><td>$30</td><td><input type="number" name="helado" value="0" min="0"></td></tr>
      <tr><td>Pastel</td><td>$35</td><td><input type="number" name="pastel" value="0" min="0"></td></tr>
      <tr><td>Tarta de zarzamora</td><td>$40</td><td><input type="number" name="tarta" value="0" min="0"></td></tr>
    </table>

    <button type="button" onclick="calcularTotal()">Calcular Total y Generar Ticket</button>
    <button type="button" onclick="imprimirTicket()">Imprimir Ticket</button>

    <p class="total" id="total"></p>
    <div class="ticket" id="ticket"></div>
  </form>

  <script>
    function calcularTotal() {
      const precios = {
        pozole: 80, mole: 90, tacos: 60, chiles: 100,
        barbacoa: 120, carne: 110, coca: 25, agua: 20,
        michelada: 45, helado: 30, pastel: 35, tarta: 40
      };

      const nombres = {
        pozole: "Pozole", mole: "Mole", tacos: "Tacos", chiles: "Chiles en nogada",
        barbacoa: "Barbacoa", carne: "Carne asada", coca: "Coca Cola", agua: "Agua de limón",
        michelada: "Michelada", helado: "Helado", pastel: "Pastel", tarta: "Tarta de zarzamora"
      };

      let total = 0;
      let ticket = " -----RESTAURANTE EL MEXICANO----- \n";
ticket += " ---------TICKET DE COMPRA--------\n";
const fecha = new Date();
ticket += `Fecha: ${fecha.toLocaleDateString()} ${fecha.toLocaleTimeString()}\n`;
ticket += "-----PRODUCTOS COMPRADOS---------\n";
      const form = document.forms['menuForm'];

      for (let item in precios) {
        const cantidad = parseInt(form[item].value) || 0;
        if (cantidad > 0) {
          const subtotal = cantidad * precios[item];
          total += subtotal;
          ticket += `${nombres[item]} x${cantidad} - $${subtotal}\n`;
        }
      }

      ticket += `\nTOTAL A PAGAR: $${total}`;
      document.getElementById('total').innerText = `Total a pagar: $${total}`;
      document.getElementById('ticket').innerText = ticket;
    }

    function imprimirTicket() {
      const contenido = document.getElementById('ticket').innerText;
      if (!contenido) {
        alert("Primero genera el ticket.");
        return;
      }

      const ventana = window.open('', '', 'height=600,width=400');
      ventana.document.write('<html><head><title>Ticket</title></head><body>');
      ventana.document.write('<pre>' + contenido + '</pre>');
      ventana.document.write('</body></html>');
      ventana.document.close();
      ventana.print();
    }
  </script>

</body>
</html>
