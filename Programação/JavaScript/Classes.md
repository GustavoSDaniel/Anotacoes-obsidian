
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

// Criando varios obejetos dentro de um objeto
let estudante = {
    nome: "Bob",
    cursos: {
        matematica: true,
        ciencia: false,
    } // UM OBJETO DENTRO DE OUTRO BOJETO
}
console.log(estudante);
console.log(estudante.cursos.matematica); // Acessabdo o iten do objeto

//DESESTRUTURAÇÃO DE OBJETOS
let {nome, cursos} = estudante; // VAI PUXAR AS INFORMAÇÕES DO OBJETO ESTUDANTE NESSE CASO NOME E CURSOS
console.log(nome);
console.log(cursos);