function carregarDadosSheets() {
  const SPREADSHEET_ID = 'SEU_ID_DA_PLANILHA';
  const API_KEY = 'SUA_API_KEY';
  const RANGE = 'Sheet1!A1:E'; // Ajuste o range

  const url = `https://sheets.googleapis.com/v4/spreadsheets/${SPREADSHEET_ID}/values/${RANGE}?key=${API_KEY}`;

  fetch(url)
    .then(response => response.json())
    .then(data => {
      // Exemplo: preencher tabela no dashboard
      const tabela = document.getElementById('minha-tabela');
      let html = '';
      data.values.forEach(row => {
        html += `<tr><td>${row[0]}</td><td>${row[1]}</td><td>R$ ${row[2]}</td><td>${row[3]}</td><td>${row[4]}</td></tr>`;
      });
      tabela.innerHTML = html;
    })
    .catch(error => console.error('Erro:', error));
}

// Chame na carga da página
window.onload = carregarDadosSheets;# Sistemas-Vendas-Bioengenharia
Sistema automatizado de vendas e dashboard para visualização em tempo real do andamento do sistema.
