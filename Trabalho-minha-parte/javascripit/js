// FUNÇÃO PARA VALIDAÇÃO DOS FORMULÁRIOS DE ANÁLISE DE CRÉDITO
function testa_form(formName) {
  // Obtém o formulário pelo nome
  var form = document.forms[formName];

  // Validação específica para cada tipo de formulário
  if (formName === "analisedecreditocnpj") {
    // Valida campo "razaosocial"
    if (form["razaosocial"].value.trim() === "") {
      alert("A razão social deve ser informada.");
      form["razaosocial"].focus();
      return false;
    }
    // Valida campo "cnpj"
    if (form["cnpj"].value.trim() === "") {
      alert("O CNPJ deve ser informado.");
      form["cnpj"].focus();
      return false;
    }
  } else if (formName === "analisedecreditocpf") {
    // Valida campo "nome"
    if (form["nome"].value.trim() === "") {
      alert("O nome deve ser informado.");
      form["nome"].focus();
      return false;
    }
    // Valida campo "cpf"
    if (form["cpf"].value.trim() === "") {
      alert("O CPF deve ser informado.");
      form["cpf"].focus();
      return false;
    }
  }

  // Valida os campos comuns aos dois formulários

  // Endereço
  if (form["endereco"].value.trim() === "") {
    alert("O endereço deve ser informado.");
    form["endereco"].focus();
    return false;
  }
  
  // Número
  if (form["numero"].value.trim() === "") {
    alert("O número deve ser informado.");
    form["numero"].focus();
    return false;
  }
  
  // CEP
  if (form["cep"].value.trim() === "") {
    alert("O CEP deve ser informado.");
    form["cep"].focus();
    return false;
  }
  
  // Cidade
  if (form["cidade"].value.trim() === "") {
    alert("A cidade deve ser informada.");
    form["cidade"].focus();
    return false;
  }
  
  // Estado (no select, verifica se foi selecionada uma opção válida)
  if (form["estado"].value === "") {
    alert("O estado deve ser selecionado.");
    form["estado"].focus();
    return false;
  }
  
  // Telefone
  if (form["telefone"].value.trim() === "") {
    alert("O telefone deve ser informado.");
    form["telefone"].focus();
    return false;
  }
  
  // E-mail
  if (form["e-mail"].value.trim() === "") {
    alert("O e-mail deve ser informado.");
    form["e-mail"].focus();
    return false;
  }
  
  // Data de abertura
  if (form["data"].value.trim() === "") {
    alert("A data de abertura deve ser informada.");
    form["data"].focus();
    return false;
  }
  
  // Anexo (arquivo)
  if (form["pdffile"].value.trim() === "") {
    alert("O documento deve ser anexado.");
    form["pdffile"].focus();
    return false;
  }
  
  // Se todas as validações passarem, permite o envio
  return true;
}

// FUNÇÃO PARA APLICAÇÃO DE MÁSCARAS NOS CAMPOS
function mascara(input) {
  // Obtém o valor atual do campo de entrada
  var v = input.value;

  // Impede a entrada de caracteres não numéricos
  if (isNaN(v[v.length - 1])) {
    input.value = v.substring(0, v.length - 1);
    return;
  }

  // Obtém o tipo de máscara a partir do atributo data-mask
  var tipo = input.getAttribute("data-mask");

  // Máscara para CPF (formato: ###.###.###-##)
  if (tipo === "cpf") {
    input.setAttribute("maxlength", "14");
    if (v.length === 3 || v.length === 7) input.value += ".";
    if (v.length === 11) input.value += "-";
  }

  // Máscara para CNPJ (formato: ##.###.###/####-##)
  if (tipo === "cnpj") {
    input.setAttribute("maxlength", "18");
    if (v.length === 2 || v.length === 6) input.value += ".";
    if (v.length === 10) input.value += "/";
    if (v.length === 15) input.value += "-";
  }

  // Máscara para CEP (formato: #####-###)
  if (tipo === "cep") {
    input.setAttribute("maxlength", "9");
    if (v.length === 5) input.value += "-";
  }

  // Máscara para Telefone (formato: (##) ####-#### ou (##) #####-####)
  if (tipo === "telefone") {
    input.setAttribute("maxlength", "14");
    if (v.length === 1) input.value = "(" + v;
    if (v.length === 3) input.value += ") ";
    if (v.length === 9) input.value += "-";
  }
  
  // Máscara para Data (formato: DD/MM/AAAA)
  if (tipo === "data") {
    input.setAttribute("maxlength", "10");
    if (v.length === 2 || v.length === 5) input.value += "/";
  }
 // index.js

// Importações
const express = require('express');
const session = require('express-session');
const bodyParser = require('body-parser');
const path = require('path');

// Criação da aplicação Express
const app = express();
const port = 3000;

// Usuário e senha "fixos" para demonstração
const login = "nome.aleatorio";
const senha = "12345";

// Configuração da sessão
app.use(session({
  secret: 'hcioudhcuoshdiso',
  resave: false,
  saveUninitialized: true
}));

// Configuração do body-parser
app.use(bodyParser.urlencoded({ extended: true }));

// Arquivos estáticos (pasta public)
app.use(express.static(path.join(__dirname, 'public')));

// Configuração de views e EJS
app.engine('html', require('ejs').renderFile);
app.set('view engine', 'html');
app.set('views', path.join(__dirname, 'views'));

// Rota POST para /login
app.post('/login', (req, res) => {
  // Verifica se usuário e senha conferem
  if (req.body.login === login && req.body.password === senha) {
    // Logado com sucesso
    req.session.login = login;
  }
  // Independente do resultado, redireciona para a rota principal
  res.redirect('/');
});

// Rota GET para /
app.get('/', (req, res) => {
  // Se o usuário estiver logado (sessão), renderiza index, senão login
  if (req.session.login) {
    res.render('index');
  } else {
    res.render('login');
  }
});

}