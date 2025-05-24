/* Este sistema tem como objetivo filtrar os clientes maiores de idade de uma loja. O cadastro do cliente deve conter: nome, idade e e-mail.
Após o filtro, também será possível cadastrar clientes para visualizar no HTML.
Criando nossa base de dados (lista-array) de clientes em um arquivo par chave-valor: */

// Adicionar mais 7 usuários e criar um design com CSS
let clientes=[
    {
    nome: "Anna",
    idade: 25,
    email: "anna@gmail.com"
},
{
    nome: "Gabriel",
    idade: 30,
    email: "gabriel@gmail.com"
},
{
    nome: "Isabella",
    idade: 18,
    email: "isa@gmail.com"
},
{
    nome: "Vitória",
    idade: 21,
    email: "vitsluna@gmail.com"
},
{
    nome: "Kaua",
    idade: 26,
    email: "marson@gmail.com"
},
{
    nome: "Lucas",
    idade: 60,
    email: "olegario@gmail.com"
},
{
    nome: "Mimi",
    idade: 32,
    email: "heitor@gmail.com"
},
{
    nome: "Cecilia",
    idade: 24,
    email: "cici@gmail.com"
},
{
    nome: "Beatriz",
    idade: 19,
    email: "beabea@gmail.com"
},
{
    nome: "Taylor",
    idade: 34,
    email: "swift13@gmail.com"}
];

// Esta função acessa os objetos (clientes) com idade maior ou igual a 18 anos e retorna os dados
function filtrarClientesAdultos(clientes) {
    return clientes.idade >= 18;
}

// Esta função é invocada quando clicamos no botão mostrarClientesAdultos
function mostrarClientesAdultos() {
    let clientesAdultos = clientes.filter(filtrarClientesAdultos);

    let lista = document.getElementById("listaClientesAdultos");

    lista.innerHTML = ""; //Limpa os dados antes de mostrar no HTML
    
    //Animação
    lista.classList.remove("fade-in");
    void lista.offsetWidth;
    lista.classList.add("fade-in");

    // Percorre o array e cria um novo item de lista
    for (let i = 0; i < clientesAdultos.length; i++){
        let item = document.createElement("li"); //Cria um novo item de lista (<li>) para cada cliente adulto.
        //Exibe os dados no ítem da lista criada: nome do cliente, idade do cliente e o e-mail do cliente (filtrados) e armazenados na variável clientesAdultos.
        item.textContent = clientesAdultos[i].nome + " (" + clientesAdultos[i].idade + " anos) - " + clientesAdultos[i].email; lista.appendChild(item);
    }
}

// Cadastra novo cliente na lista
function cadastrarCliente() {
    let nome = document.getElementById("nomeCliente").value;
    let idade = parseInt(document.getElementById("idadeCliente").value);
    let email = document.getElementById("emailCliente").value;

// Validação simples: nome deve ter nome preenchido/idade e e-mail também, caso contrário exibe msg
if (nome && idade && email) {
    clientes.push({nome: nome, idade: idade, email: email });

    document.getElementById("mensagemCadastro").textContent = "Cliente cadastrado com sucesso!";
    document.getElementById("nomeCliente").value = "";
    document.getElementById("idadeCliente").value = "";
    document.getElementById("emailCliente").value = "";

    mostrarClientesAdultos(); // Atualiza a lista automaticamente
} else {
    document.getElementById("mensagemCadastro").textContent = "Por favor, preencha todos os campos."
}
}
