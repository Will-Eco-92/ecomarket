<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>EcoMarket - Comparateur de prix</title>

<style>
body {
  font-family: Arial, sans-serif;
  background-color: #f4f6f7;
  margin: 0;
  padding: 20px;
}

h1 {
  text-align: center;
  color: #2e7d32;
}

.container {
  background: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0px 2px 5px rgba(0,0,0,0.2);
}

button {
  background: #2e7d32;
  color: white;
  border: none;
  padding: 12px;
  border-radius: 6px;
  margin-top: 10px;
  width: 100%;
  font-size: 16px;
}

select {
  width: 100%;
  padding: 10px;
  margin-top: 10px;
}

.result {
  margin-top: 20px;
  background: #e8f5e9;
  padding: 15px;
  border-radius: 8px;
}
</style>

</head>

<body>

<h1>🛒 EcoMarket</h1>

<div class="container">

<h3>Choisir un produit :</h3>

<select id="produit">
  <option value="riz5">Riz (5kg)</option>
  <option value="riz10">Riz (10kg)</option>
  <option value="savon">Savon</option>
  <option value="lait">Boîte de lait</option>
</select>

<button onclick="comparer()">Comparer les prix</button>

<div id="resultat" class="result"></div>

</div>

<script>

function comparer() {

let produit = document.getElementById("produit").value;

let data = {

riz5: [
{magasin:"San Gel (Oloumi)", prix:5500},
{magasin:"San Gel (Charbonnages)", prix:5300},
{magasin:"Prix Import (Awendjé)", prix:5200},
{magasin:"Prix Import (Carrefour SNI)", prix:5100},
{magasin:"Ckdo (Lalala à droite)", prix:5600},
{magasin:"Ckdo (Carrefour SNI)", prix:5000},
{magasin:"Ckdo (Carrefour Gigi)", prix:5400},
{magasin:"SNI Gel (Owendo)", prix:5050}
],

riz10: [
{magasin:"San Gel", prix:9800},
{magasin:"Prix Import", prix:9500},
{magasin:"Ckdo", prix:10000}
],

savon: [
{magasin:"Prix Import", prix:700},
{magasin:"Ckdo", prix:650}
],

lait: [
{magasin:"Prix Import", prix:1200},
{magasin:"San Gel", prix:1100}
]

};

let liste = data[produit];

liste.sort((a,b)=>a.prix-b.prix);

let moinsCher = liste[0];
let plusCher = liste[liste.length-1];

let html = `
<h3>📊 Résultat</h3>
<p>🥇 Moins cher : <b>${moinsCher.magasin}</b> (${moinsCher.prix} FCFA)</p>

<p>📈 Classement :</p>
`;

liste.forEach((item,index)=>{
html += `${index+1} - ${item.magasin} : ${item.prix} FCFA<br>`;
});

html += `<br>💸 Plus cher : <b>${plusCher.magasin}</b> (${plusCher.prix} FCFA)`;

document.getElementById("resultat").innerHTML = html;

}

</script>

</body>
</html>
