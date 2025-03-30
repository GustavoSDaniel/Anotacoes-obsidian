
let pessoa = {

nome: "Anna",

idade: 24,

estudante: false

}

  
console.log(pessoa);

  

// IMPRIMNDO APENAS UMA INFORMAÇÃO DO OBJETO

  

console.log(pessoa.nome);

  

// MODIFICANDO UM ATRIBUTO DO OBJETO

  

pessoa.idade = 55;

console.log(pessoa.idade);

  

// ADICIONANDO UMA NOVA PROPIEDADE NO BOJETO

  

pessoa.profissao = "Engenheiro de software";

console.log(pessoa);

console.log(pessoa.profissao);

  

// EXCLUINDO UMA PROPIEDADE DO OBJETO

  

delete pessoa.estudante;

console.log(estudante);

  

// CHECANDO SE A PROPIEDADE EXISTE

  

console.log('nome' in pessoa); // EXISTE A VARIAVEL NOME NO OBJETO PESSOA ? VAI RETORNAR UM BOOLEANO