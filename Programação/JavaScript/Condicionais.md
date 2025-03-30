
// CONDICIONAIS

let x = 10;

// let condicional = (condicao ? "condição se for verdadeira" : "condição se for falso"); EXEMPLO A BAIXO

let mensagem = (x > 5) ? "x é amior que 5" : "x é menor que 5";

// FAÇA UMA CONDICIONAL

// IDADE < 13 => CRIANÇA

//IDADE > 13 && IDADE < 20 => ADOLECENTE

// IDADE > 20 => ADULTO

let idade = 15;

let categoria = (idade < 13) ? "CRIANÇA" : ( idade <= 20) ? "ADOLECENTE" : "adulto"; // CASO A IDADE SEJA MAIOR QUE 20 É ADULTO AI NÃO PRECISA COLOCAR NADA

console.log(categoria);