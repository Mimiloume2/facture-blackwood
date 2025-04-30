<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Facture Blackwood</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: #f8f4ee;
      color: #2e2e2e;
    }
    header {
      background-color: #b48c64;
      color: white;
      padding: 1rem 2rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    header img {
      height: 60px;
    }
    main {
      max-width: 800px;
      background: white;
      margin: 2rem auto;
      padding: 2rem;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      border-radius: 8px;
    }
    h1 {
      text-align: center;
      color: #5c4327;
    }
    label {
      display: block;
      margin-top: 1rem;
      font-weight: bold;
    }
    input, select, textarea {
      width: 100%;
      padding: 8px;
      margin-top: 0.5rem;
      border: 1px solid #ccc;
      border-radius: 4px;
      font-size: 1rem;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 2rem;
    }
    th, td {
      border: 1px solid #b48c64;
      padding: 10px;
      text-align: center;
    }
    thead {
      background-color: #e7d4bf;
    }
    .total-line {
      text-align: right;
      margin-top: 1rem;
    }
    button {
      background-color: #b48c64;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 4px;
      font-size: 1rem;
      cursor: pointer;
      margin-top: 1rem;
      margin-right: 1rem;
    }
    button:hover {
      background-color: #91653e;
    }
  </style>
</head>
<body>
  <header>
    <img src="logo.png" alt="Logo Blackwood">
    <div>
      <strong>Blackwood Saloon</strong><br>
      Facturation
    </div>
  </header>
  <main>
    <h1>Générateur de Facture</h1>

    <label for="client">Nom du client :</label>
    <input type="text" id="client" placeholder="Nom du client">

    <label for="date">Date :</label>
    <input type="date" id="date">

    <label for="facture">Numéro de facture :</label>
    <input type="text" id="facture" placeholder="N° facture">

    <label for="compte">Nom du compte :</label>
    <input type="text" id="compte" value="Blackwood Saloon">

    <label for="iban">Numéro de compte :</label>
    <input type="text" id="iban" value="20075">

    <label for="remarques">Remarques :</label>
    <textarea id="remarques" rows="3"></textarea>

    <label><input type="checkbox" id="paye"> Facture payée</label>

    <table>
      <thead>
        <tr>
          <th>Description</th>
          <th>PU ($)</th>
          <th>Quantité</th>
          <th>Total</th>
        </tr>
      </thead>
      <tbody id="table-body">
        <tr>
          <td>Produit A</td>
          <td class="unit-price">50</td>
          <td><input type="number" min="0" placeholder="0"></td>
          <td class="line-total">0</td>
        </tr>
        <tr>
          <td>Produit B</td>
          <td class="unit-price">30</td>
          <td><input type="number" min="0" placeholder="0"></td>
          <td class="line-total">0</td>
        </tr>
      </tbody>
    </table>

    <label for="taux-tva">TVA (%) :</label>
    <input type="number" id="taux-tva" value="20">

    <div class="total-line">
      Sous-total : <span id="subtotal">0</span> $<br>
      TVA (<span id="tva-rate-display">20</span>%) : <span id="tva">0</span> $<br>
    </div>

    <label for="reduction-type">Type de réduction :</label>
    <select id="reduction-type">
      <option value="montant">Montant ($)</option>
      <option value="pourcentage">Pourcentage (%)</option>
    </select>
    <input type="number" id="reduction" value="0">

    <div class="total-line">
      Total TTC : <span id="total">0</span> $
    </div>

    <button onclick="generatePDF()">Télécharger en PDF</button>
    <button onclick="resetForm()">Réinitialiser</button>
  </main>
</body>
</html>
