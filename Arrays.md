
let numeros = [1, 2, 3, 4];

console.log(numeros);

let frutas = ["maça", "banana", "laranja"];

console.log(frutas);

// [1, 2, 3, 4]

// 0 1 2 3 <= INDEX que significa a posição da variavel dentro do array

console.log(numeros[2]); // <= PARA MOSTRAS O QUE TEM NO ARRAY NA POSIÇÃO 2 no caso seria o NUMERO 3

frutas [2] = "goiaba"; // SUBISTITUINDO O LARANJA QUE ESTÁ NA POSIÇÃO 2 NO ARRAY DE FRUTAS PARA GOIABA

// CRIANDO UMA MATRIX

let matrix = [

[1,2,3], //MATRIX DE INDECE 0

[1,2,3], // MATRIX DE INDECE 1

[1,2,3] // MATRIX DE INDICE 2

]


console.log(matrix[0]); // PARA MOSTRAR A PRIMEIRA LINHA DA MATRIX

console.log(matrix[0][1]); // VAI NA MATRIX 0 E DENTRO DESSA MATRIX VAI NA POSIÇÃO(INDECE)1

console.log(frutas.length); // ESSE COMANDO FALA QUANTOS ITENS TEM DENTRO DO ARRAY

// PUSH ADICIONA UM ELEMENTO NO FINAL DO ARRAY

frutas.push("MELANCIA");


//POP REMOVE O ULTIMO ELEMENTOO DO ARRAY

frutas.pop(); // <= REMOVENDO O ULTIMO ELEMENTO

let ultimaFruta = frutas.pop(); // <= PARA MOSTRAR QUAL FOI O ULTIMO ELEMENTO REMOVIDO

console.log(frutas);

console.log(ultimaFruta);


// SHIFT REMOVE O PRIMEIRO ELEMENTO DO ARRAY

frutas.shift(); // <= REMOVENDO O PRIMEIRO ELEMENTO

let primeiraFruta = frutas.shift(); // <= PARA MOSTRAR QUAL FOI O PRIMEIRO ELEMENTO REMOVIDO

console.log(frutas);

console.log(primeiraFruta);

  
// UNSHIFT

  
frutas.unshift("MAMÃO"); // <= ADICIONA UM ELEMENTO NO ARRAY NA PRIMEIRA POSIÇÃO(0)

let novaFruta = frutas.unshift(); // <= MOSTRA O NOVO ELEMENTO NA PRIMEIRA POSIÇÃO(0)

console.log(frutas);

console.log(novaFruta);

// SLICE ELE COPIA UMA PARTE DA MATRIX

  

let novasFrutas = ["maça", "banana", "laranja", "PERA"];

let sliceArray = novasFrutas.slice(1,3); // VAI PEGAR A POSIÇÃO 1 E 2 *NÃO PEGA A ULTIMA POSIÇÃO NESSE CASO A POSIÇÃO 3

console.log(novasFrutas);

  

//SPLICE ADICIONA OU REMOVE ELEMENTOS ESPECIFICOS NO INDECE

  

frutas.splice(1,2); // <= VAI DELETAR OS 2 ELEMENTOS QUE ESTÁ NESSA POSIÇÃO

let deletandoFrutas = frutas.splice(1,2); // PARA MOSTRAR QUAIS ELEMENTOS FORAM DELETADOS

console.log(frutas);

console.log(deletandoFrutas);

  

let adicionandoFrutas = frutas.splice(1,2, "NOVA FRUTA NA POSIÇÃO 1", "NOVA FRUTA NA POSIÇÃO 2"); // PARA MOSTRAR QUAIS ELEMENTOS FORAM FORAM ADICIONADOS

console.log(adicionandoFrutas);