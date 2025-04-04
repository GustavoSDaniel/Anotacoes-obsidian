
/* MODELAGEM BASICA 
ENTIDADE = TABELA
TRIBUTO = CAMPOS */

Cliente 

IDCLIENTE AUTO_INCREMENTE        
Nome = CARACTER (30)
CPF = NUMERICO (11)
Email = CARACTER (30)
Telefone = CARACTER (30)
Endereco = CARACTER (100)
Sexo = CARACTER (1)

/* Processo de MODELAGEM */

MODELAGEM CONSEITUAL = RASCUNHO
MODELAGEM LOGICA = QUALQUER PROGRAMA DE MODELAGEM
MODELAGEM FISICA = SCRIPTS DE BANCO

/*INICIANDO MODELAGEM FISICA*/

/*CRIANDO BANCO DE DADOS*/

CREATE DATABASE PROJETO;/* (PROJETO É O NOME DO BANCO DE DADOS) /*

/* CONECTANDO SE AO BANCO*/

USE PROJETO;

/* CRIANDO A TABELA CLIENTES (EXEMPLO)/*

CREATE TABLE CLIENTE (
	IDCLIENTE INT PRIMARY KEY AUTO_INCREMENT CHAVE PRIMARIA ELA MESMO CRIA A SUA SEQUENCIA
	NOME VARCHAR(30) NOT NULL, SIGNIFICA QUE O CAMPO É OBRIGATORIO SER PREENCHIDO
	SEXO CHAR (1),
	EMAIL VARCHAR (30),
	CPF INT (11),
	TELEFONE VARCHAR (30),
	ENDERECO VARCHAR (100)
	
);

/* VERIFICANDO AS TABELAS DO BANCO*/

SHOW TABLES;

/* DESCOBRINDO COMO É A ESTRUTURA DE UMA TABELA */

DESC CLIENTE;  /*DESC E O NOME DA TABELA*/

/*SINTAXE BASICA DE INSERCAO DE DADOS = INSERT INTO NOME DA TABELA ...*/

/* FORMA 01 - OMITINDO AS COLUNAS AS INFORMAÇOES TEM QUE ESTAR NA MESMA ORDEM QUE A TABELA FOI CRIADA NÃO É MUITO RECOMENDADO */

INSERT INTO CLIENTE VALUES('JOAO','M','JOAO@GMAIL.COM',988638273,'22923110','MAIA LACERDA - ESTACIO - RIO DE JANEIRO - RJ');

INSERT INTO CLIENTE VALUES('CELIA','F','CELIA@GMAIL.COM',541521456,'25078869','RIACHUELO - CENTRO - RIO DE JANEIRO - RJ');

INSERT INTO CLIENTE VALUES('JORGE','M',NULL,885755896,'58748895','OSCAR CURY - BOM RETIRO - PATOS DE MINAS - MG');

/* FORMA 02 - COLOCANDO AS COLUNAS FORMA MAIS SEGURA */

INSERT INTO CLIENTE(NOME,SEXO,ENDERECO,TELEFONE,CPF) VALUES('LILIAN','F','SENADOR SOARES - TIJUCA - RIO DE JANEIRO - RJ','947785696',887774856);


/* COMANDO SELECT - SELECAO PROJECAO JUNCAO */

/* SELECT É UMA PROJECAO ELE FILTRA AS INFORMACOES EM NIVEL DE COLUNA*/

SELECT MOSTRA ALGO NO BANCO DE DADOS

SELECT NOME, SEXO, EMAIL FROM CLIENTE;/* SELECT TA PUXANDO OS CAMPOS DA TABELA E O FROM TA IDENTIFICANDO QUAL TABELA ELE VAI PUXAR */

SELECT NOME AS CLIENTE, EMAIL FROM CLIENTE; /* O COMANDO 'AS' ESTA SUBISTITUINDO A PALAVRA NOME POR CLIENTE NA HORA DE MOSTRAR A TABELA */


/* APENAS PARA ESTUDO - NA PRATICA NAO USA ESSE COMANDO */

SELECT * FROM CLIENTE /* NOME DA TABELA */

SELEC NOW() /* MOSTRA A HORA QUE FEZ A TABELA OU INSERIU ALGUM DADO */

SELECT NOW() AS DATA_HORA;
SELECT NOW() AS DATA_HORA FROM CLIENTE;


/*FILTRANDO OS DADOS COM WHERE E LIKE */ /*WHERE SIGNIFICA 'ONDE' */

SELECT NOME, SEXO FROM CLIENTE  /* PROJECAO VAI MOSTRAR AS INFORMACOES DA TABELA */
WHERE SEXO = 'M'; /* SELECAO VAI FILTRAR AS TABELAS ATRAVES DO QUE FOI PEDIDO*/

SELECT NOME, SEXO FROM CLIENTE /* PROJECAO VAI MOSTRAR AS INFORMACOES DA TABELA */
WHERE SEXO = 'F'; /* SELECAO VAI FILTRAR AS TABELAS ATRAVES DO QUE FOI PEDIDO*/

/* LIKE SUBSTITUI O = (IGUAL) ELE É MAIS ESPECIFICO NA HORA DE FILTRAR USA ELE QUANDO A PALAVRA FOR EXATAMENTE AQUILO */
/* % SIGINIFICA QUALQUER COISA ANTES SE COLOCADO O % NA FRENTE OU QUALQUER COISA SE COLOCADO O % DEPOIS */

SELECT NOME, SEXO FROM CLIENTE /* PROJECAO VAI MOSTRAR AS INFORMACOES DA TABELA */
WHERE ENDERECO LIKE '%RJ'; /* SELECAO VAI FILTRAR AS TABELAS ATRAVES DO QUE FOI PEDIDO*/

SELECT NOME, SEXO, ENDERECO FROM CLIENTE /* PROJECAO VAI MOSTRAR AS INFORMACOES DA TABELA */
WHERE ENDERECO LIKE '%RJ'; /* SELECAO VAI FILTRAR AS TABELAS ATRAVES DO QUE FOI PEDIDO*/

SELECT NOME, SEXO, ENDERECO FROM CLIENTE /* PROJECAO VAI MOSTRAR AS INFORMACOES DA TABELA */
WHERE ENDERECO LIKE 'OSCAR%'; /* SELECAO VAI FILTRAR AS TABELAS ATRAVES DO QUE FOI PEDIDO*/

SELECT NOME, SEXO, ENDERECO FROM CLIENTE /* PROJECAO VAI MOSTRAR AS INFORMACOES DA TABELA */
WHERE ENDERECO LIKE '%CENTRO%'; /* SELECAO VAI FILTRAR AS TABELAS ATRAVES DO QUE FOI PEDIDO*/

STATUS; /* mostra eu qual banco de dados eu estou*/

/* operadores logicos*/ /* SE NÃO PUXAR NADA NA TABELA SIGNIFICA QUE TODAS AS CONDIÇÕES SÃO FALSAS */

/* 'OR' PARA QUE UMA QUERI SEJA VERDADEIRA BASTA QUE UMA DAS CONDIÇÕES SEJA VERDADEIRA */

/* AND PARA QUE A QUERI SEJA VERDADEIRA AS DUAS CONDIÇÕES TEM QUE SER VERDADEURAS */

/* OR 'OU' */

SELECT SEXO, NOME, ENDERECO FROM CLIENTE WHERE SEXO = 'M' OR ENDERECO LIKE '%RJ%'; /* PELO MENOS UMA DAS CONDIÇOES TEM QUE SER VERDADEIRA PARA PUXAR NA TABELA*/


/* AND 'E' */

SELECT SEXO, NOME, ENDERECO FROM CLIENTE WHERE SEXO = 'M' AND ENDERECO LIKE '%RJ%'; /* TODAS AS CCONDIÇÕES TEM QUE SER VERDADEIRAS PARA PUXAR NA TABELA */

/* CONTANDO OS REGISTROS DA TABELA COMANDO 'COUNT(*)' */

SELECT COUNT(*) FROM CLIENTE;

SELECT COUNT(*) AS 'CONTANDO A QUANTIDADE DE CLIENTES DA TABELA CLIENTE' FROM CLIENTE;

/* COMANDO 'GROUP BY' ESSE COMANDO DIVIDE EM GRUPO O QUE FOI SELECIONADO E JUNTO COM O COMANDO 'COUNT(*)' CONTA QUANTOS TIPOS TEM DE CADA GRUPO'*/

SELECT COUNT(*), SEXO FROM CLIENTE GROUP BY SEXO; /* SELECIONA O SEXO E CONTA DA TABELA CLIENTE E AGRUPA O SEXO PELAS QUANTIDADE DE TIPOS ( NESSE CASO 'F' E 'M' */

/*FILTRANDO VALORES NULOS (VAZIOS) O 'IS' SIFNIFICA É */

SELECT NOME, SEXO, ENDERECO FROM CLIENTE WHERE EMAIL IS NULL;

/* FILTRANDO VALORES NÃO NULOS USANDO 'IS NOT' SIGNIFICA NÃO É */

SELECT NOME, SEXO, ENDERECO FROM CLIENTE WHERE EMAIL IS NOT NULL;

/* ATUALIZAR DADOS DA TABELA 'UPDATE' */

SELECT * FROM CLIENTE WHERE NOME = "NOME DE QUEM VAI SER INSERIDO O EMAIL"; 
UPDATE CLIENTE SET EMAIL = "EXEMPLO@GMAIL.COM" WHERE = "NOME DE QUEM VAI SER INSERIDO O EMAIL";

/*DELETANDO REGISTROS DA TABELA */

SELECT * FROM CLIENTE WHERE NOME = "NOME DE QUEM VAI TER O REGISTRO DELETADO";
DELETE FROM CLIENTE WHERE NOME = "ANA";

/* PRIMEIRA FORMA NORMAL PARA MODELAR UM BANCO */

/* 1 - TODO CAMPO VETORIZADO SE TORNARA OUTRA TABELA EM OUTRA PALAVRA SE PODE TER MAIS DE É UM É CAMPO VETORIZADO EX TELEFONE
   2 - TODO CAMPO MUITVALORADO SE TORNARA OUTRA TABELA, QUANDO O CAMPO FOR DIVISIVEL EX ENDEREÇO QUE PODE TER RUA BAIRRO ESTADO
   3 - TODA TABEELA PRECISA DE UM CAMPO QUE IDENTIFICA TODO O REGISTRO SENDO UM UNICO EM OUTRA PALAVRAS A FAMOSA CHAVE PRIMARIA QUE GERALMENTE É SEMPRE UM 'IDNOMEDATABELA' */
   
   /* CARDIALIDADE 1,1 - 1,N - 0,1 - 0,N ===> SE COMEÇA COM ZERO (0) É PQ NÃO É OBRIGATORIO, SE COMEÇA COM UM (1) É PQ É OBRIGATORIO JA A SEGUNDA PARTE SE TEM UM (1) É PQ NO MINIMO OU NO MAXIMO TEM QUE SER UM (1), AGORA SE FOR N PODE SER MAIS DE UM (1) */
   
   /* QUANDO FOR JUNTAR AS CARDIALIDADES É SO PEGAR O SEGUNDO PAR DE CADA ENTIDADE */
   
   /* CHAVE ESTRANGEIRA - É A CHAVE PRIMARIA DE UMA TABELA QUE VAI ATÉ A OUTRA TABELA PARA FAZER REFERENCIA ENTRE OS REGISTROS */
   
   	/*LINCANDO A CHAVE SECUNDARIA (FK) */
	
	FOREIGN KEY (ID_CLIENTE) /*ID DA CHAVE SECUNDARIA */
	REFERENCES CLIENTE(IDCLIENTE) /* DE ONDE TA PEGANDO A CHAVE PRIMARIA (QUE VIRA A CHAVE SECUNDARIA NA TABELA (ID_CLIENTE) */

	/* EM RELACIONAMENTO 1 PARA 1 A CHAVE SECUNDARIA (FK) FICA NA TABELA MAIS FRACA E EM RELACIONAMENTO 1 PARA 1 A CHAVE ESTRANGEIRA NÃO SE REPETE, EM RELACIONAMENTO 1 PRA N A CHAVE SECUNDARIA (FK) FICA NA TABELA AONTE TA O 'N' DA CARDIALIDADE */
	
	/*COMANDO PARA APAGAR TABABELA */
	
	DROP TABLE NOMEDATABELA;
	
	/* SELEÇÃO, PROJEÇÃO, JUNÇÃO */
	
	/* PROJEÇÃO => É TUDO QUE VC QUER VER NA TELA */
	
	/* SELEÇÃO => É FRILTAR UMA TABELA, SELECIONAR ATRIBUTOS DE UMA TABELA OU DE VARIAS EX: SEXO = "F" ( SEXO = F NO CASO É O FILTRO VAI ESTA CHAMANDO ATRIBUTOS QUE TEM A CARACTERISTICA "F"  O QUE VAI SER MOSTRADO NA TELA (PROJEÇÃO) QUEM SELECIONA (FILTRA) É O WHERE 
	
	SELECT NOME, SEXO, EMAIL => PROJETA NA TELA
	FROM CLIENTE => MOSTRA QUAL TABELA QUE É
	WHERE SEXO = "F" => SELECIONA (FILTRA)
	*/
	
	/* JUNÇÃO => JOIN JUNTAR AS TABELAS EX: SELECT NOME, SEXO, BAIRRO, CIDADE => MOSTRE
											FROM CLIENTE => MOSTRA QUAL TABELA QUE É
											INNER JOIN ENDERECO => JUNTE COM A TABELA (NESSE CASO ENDERECO)
											ON IDCLIENTE = ID_CLIENTE => AONDE A CHAVE PRIMARIA TEM OS MESMO 'ID' QUE A CHAVE SECUNDARIA
											WHERE SEXO = "F"; => FILTRA NA TABELA NO NESSE CASO QUEM FOI MULHER 'F'

	*/
	
	/* QUANDO FORMO JUNTAR MAIS DE UMA TABELA DEVEMOS IDENTIFICAR DE QUE TABELA SÃO OS ATRIBUTOS PELO QUAL ESTAMOS JUTNADO EX:
	
	SELECT CLIENTE.NOME, CLIENTE.SEXO, ENDERECO.BAIRRO, ENDERECO.CIDADE, TELEFONE.TIPO, TELEFONE.NUMEROTELEFONE
	FROM CLIENTE
	INNER JOIN ENDERECO
	ON CLIENTE.IDCLIENTE = ENDERECO.ID_CLIENTE
	INNER JOIN TELEFONE
	ON CLIENTE.IDCLIENTE = TELEFONE.ID_CLIENTE; IDENTIFCANDO DE ONDE VEM CADA ATRIBUTO 
	
	OUTRA FORMA DE FAZER QUE É MAIS UTILIZADA É ASSIM: USANDO AS INICIAIS DAS TABELAS
	
	SELECT C.NOME, C.SEXO, E.BAIRRO, E.CIDADE, T.TIPO, T.NUMEROTELEFONE
	FROM CLIENTE C
	INNER JOIN ENDERECO E
	ON C.IDCLIENTE = E.ID_CLIENTE
	INNER JOIN TELEFONE T
	ON C.IDCLIENTE = T.ID_CLIENTE;           */
	
	/* DICA ANTES DE FAZWE QUALQUER ATUALIZAÇÃO FILTRA O REGISTRO QUE VC QUER ATUALIZAR ATRAVES DO ID ANTE PARA TER CERTEZA QUE É ESSE O ENDEREÇO EX: SELEC FROM * CLIENTE 
						WHRE IDCLIENTE = 7; 
						
						UPDATE CLIENTE
						SET SEXO = 'F'    => NO CASO ESTOU ALTERANDO O SEXO DE 'M' PARA 'F'
						WHERE IDCLIENTE = 7;
						
						*/
						
	/* ALTERA TABELA */
	
	ALTER TABLE NOMEDATABELA  /*AONDE VAI OCORRE ALTERAÇOES NOS TRIBUTOS DA TABELA */
	MODIFY NOVONOME INT NOT NULL ETC /* NA FRENTE PODE COLOCAR TBM OS TIPOS QUE VC QUER ALTERAR */
	
	/* ADICIONANDO UMA COLUNA */
	
	ALTER TABLE NOMEDATABELA /* AONDE VAI OCRRER A MUDANÇA DA COLUNA DA TABELA */
	ADD NOMEDACOLUNA INT FLOAT NOT NULL ETC /* O NOME E O TIPO DA NOVA COLUNA */
	
	/* APAGANDO UMA COLUNA DA TABELA */
	
	ALTER TABLE NOMEDATABELA /*NOME DA TABELA AONDE A COLUNA VAI SER APAGADA */
	DROP COLUMN NOMEDACOLUNA /* NOME DA COLUNA AONDE VAI SER APAGADO */
	
	/* ADICIONANDO UMA COLUNA EM UMA POSIÇÃO ESPECIFICA */
	
	ALTER TABLE NOMEDATABELA
	ADD COLUMN NOMEDACOLUNA FLOAT INT CHAR VARCHAR ENUM ETC /* ADICIONANDO A COLUNA */
	AFTER NOMEDACOLUNAQUEVCQUERQUECOLOCADEPOIS /* NOME DA COLUNA QUE VAI SER COLOCADO NA FRENTE ( A COLUNA ADICIONADA VAI SER DEPOIS DESSA */
	
	/* ADICIONANDO UMA NOVA COLUNA SO QUE NA PRIMEIRA POSIÇÃO DA TABELA */
	
	ALTER TABLE NOMEDATABELA
	ADD COLUMN NOMEDACOLUNA FLOAT INT CHAR VARCHAR ENUM ETC /* ADICIONANDO A COLUNA */
	FIRST; /* ESSE COMANDO FAZ COM QUE A COLUNA ADICIONADA SEJA A PRIMEIRA NA TABELA*
	
	
	/* USANDO O 'IN' PARA IDENTIFICAR ALGO NA TABELA PARA SELEÇÃO */]
	
	UPDATE CLIENTE SET SEXO = 'F'
	WHERE IDCLIENTE IN (12,13,18,20);  /* NESSE EXEMPLO ESTOU TROCANDO O SEXO DO CLIENTE PARA 'F' AONDE O IDCLIENTE FOR ESSES 	RESPECTIVOS NUMEROS*/
	
	
	/* A TABELA COM MAIS LIGAÇÃO ELE SEMPRE VEM PRIMEIRO NA HORA DE FAZER A QUERY*/
	
	/* IFNULL É UMA FUNÇÃO AONDE ESTIVER NULO EU POSSO MUDAR A MENSAGEM PARA OUTRA COISA EX "NÃO TEM REGISTRO" */
	
	SELECT C.NOME, IFNULL(C.EMAIL, 'MENSAGEM NO LUGAR DO NULL') EMAIL, E.ESTADO, T.NUMEROTELEFONE
	FROM CLIENTE C
	INNER JOIN ENDERECO E
	ON C.IDCLIENTE = E.ID_CLIENTE
	INNER JOIN TELEFONE T
	ON C.IDCLIENTE = T.ID_CLIENTE;
	
	
	/* VIEW ELE OTIMOZA O TEMPO SALVANDO UM UMA TABELA QUE GERALMENTE SE USA NO DIA DIA */
	
	CREATE VIEW VIEW_NOMEDAPALAVRAQUEVAICHAMARATABELA AS /* E PARA ACESSAR É SO DA O SEGUINTE COMANDO 'SELECT * FROM NOMEDAPALAVRAQUEVAICHAMARATABELA É SEMPRE BOM NA HORA DE CRIAR UMA VIEW IDENTIFICAR QUE ELA É UMA VIEW POIS ELA APARECE JUNTO COM AS TABELAS NA HORA DE PESQUISAR*/
	SELECT C.NOME, C.SEXO, C.EMAIL, T.TIPO, T.NUMEROTELEFONE, E.BAIRRO, E.CIDADE, E.ESTADO
	FROM CLIENTE C
	INNER JOIN ENDERECO E
	ON C.IDCLIENTE = E.ID_CLIENTE 
	INNER JOIN TELEFONE T
	ON C.IDCLIENTE = T.ID_CLIENTE;
	
	/* PARA APAGAR UMA VIEW É SO USAR O COMANDO DROP VIEW NOMEDAVIEW */
	
	DROP VIEW NOMEDAVIEW;
	
	/* COM A VIEW VC PODE USAR ELA PARA CHAMAR A TABELA QUE FOI CRIADA */
	
	
	EXEMPLO:
	SELECT NOME, ESTADO, NUMEROTELEFONE
    FROM VIEW_NOMEDAVIEWCRIADA;
	
	/* NA VIEW QUE TEM INNER JOIN É PERMITIDO FAZER UPDATE MAS NÃO É PERMITIDO FAZER INSET NEM DELETE */
	
	/*JA NA QUE NÃO TEM INNER JOIN ( MAIS DE UMA TABELA JUNTO) PODE FAZER UPDATE E INSERT ALEM DE UPDATE */
	
	/*ORDERNANDO COLUNA VC PODE USAR COMO BASE A ORDEM DA COLUNA COMO 1,2,3,ETC OU POR NOME DA COLUNA*/
	
	SELECT (PODE COLOCAR O NOME DA COLUNA AQUI TBM SEM O *) * FROM NOMEDATABELA
	ORDER BY NOMEDACOLUNA;
	
	/*ORDERNANDO POR NUMERO DE COLUNA (COLAR EM ORDEM NUMERICA OU ALFABETICA OU MAIOR PARA O MENOS*/
	
	SELECT (PODE COLOCAR O NOME DA COLUNA AQUI TBM SEM O *) * FROM NOMEDATABELA
	ORDER BY 1,2,3; /* ORDERNA A COLUNA NUMERO 1,2,3 */
	
	SELECT (PODE COLOCAR O NOME DA COLUNA AQUI TBM SEM O *) * FROM NOMEDATABELA
	ORDER BY 1 DESC,2,3 DESC; /*COM ESSE COMANDO A TABELA É ORDENADA DO MAIOR PARA O MENOR DESCENDENTE NA COLUNA AONDE QUER ORDERNA POR DESCENDENTE TEM QUE COLOCAR O DESC NA FRENTE*/
	
	SELECT C.NOME, C.EMAIL, T.NUMEROTELEFONE
	FROM CLIENTE C
	INNER JOIN TELEFONE T
	ON C.IDCLIENTE = T.ID_CLIENTE
	INNER JOIN ENDERECO E
	ON C.IDCLIENTE = E.ID_CLIENTE
	ORDER BY 2 DESC; /* NESSE EXEMPLO ESTOU ORDENANDO A COLUNA 2 QUE SERIA O NOME DA TABELA ( EU PODERIA TBM COLOCAR O NOME DA COLUNA 'C.NOME' QUE DARIA CERTO DA MESMA FORMA) E TBM ELE TA DESCENDENTE NO CASO DE LETRA ELA TA INDO DE Z ATÉ A */
	
	/*MUDAR O FINAL DO CODIGO O ONDE MOSTRA QUE ACABOU O COMANDO */
	
	DELIMITER $
	
	/* PROCEDURES */
	
	DELIMITER $
	CREATE PROCEDURE NOMEDOMETODO()
	BEGIN
			QUALQUER COMANDO;
	SELECT
	END
	$
	
	CALL NUMEDOMETODO();
	
	/* EXEMPLO DE COMO USAR UMA PROCEDURES*/
	
	CREATE TABLE CURSO(
	IDCURSOS INT PRIMARY KEY AUTO_INCREMENT,
	NOME VARCHAR(50) NOT NULL,
	HORAS INT(3) NOT NULL,
	VALOR FLOAT(10,2) NOT NULL
);

	SHOW TABLES;

	INSERT INTO CURSO VALUE(NULL, "JAVA", 55, 700.20);
	INSERT INTO CURSO VALUE(NULL, "BANCO DE DADOS", 30, 550.00);

	DELIMITER $

	CREATE PROCEDURE CADASTRO_CURSO(P_NOME VARCHAR(50),
									P_HORAS INT, 
									P_PRECO FLOAT(10,2))
	BEGIN

		INSERT INTO CURSO VALUES(NULL, P_NOME, P_HORAS, P_PRECO);
		
	END
	$

	CALL CADASTRO_CURSO("BI SQL SERVER", 45, 250.60);
	CALL CADASTRO_CURSO("POWER BI", 35, 850.60);
	CALL CADASTRO_CURSO("TABLEU", 20, 350.60);
	
	/* OUTRO EXEMPLO DE PROCEDURE*/
	
	DELIMITER $
	CREATE PROCEDURE ACHAR_CURSO(P_IDCURSO INT)
	BEGIN
	SELECT NOME, HORAS, VALOR
	FROM CURSO
	WHERE IDCURSOS = P_IDCURSO;
	END
	$

	/* PARA CHARMAR ESSE PROCEDURE BASTA USAR O COMANDO CALL ACHAR_CURSO(NUMERO DO CURSO QUE DESEJA ACHAR PELO ID) */

	CALL ACHAR_CURSO(1);
	
	/* MAX TRAS O MAIOR VALOR DE UMA COLUNA */
	
	SELECT MAX(NOME DA COLUNA) 
	FROM NOME DA TABELA;
	
	/* MIN TRAS O MENOR VALOR DA COLUNA */
	
	SELECT MIN(NOME DA COLUNA)
	FROM NOME DA TABELA;
	
	/* AVG TRAZ O VALOR MEDIO DA COLUNA */
	
	SELECT AVG(NOME DA COLUNA)
	FROM NOME DA TABELA;
	
	/* TRUNCATE ELE CORTA NUMEROS DEPOS DA VIRGULA (DECIMAIS) */
	
	EX 
	
	SELECT TRUNCATE(AVG(NOME DA COLUNA),2) /* NESSE CASO ELE ESTA PEGANDO O NUMERO DO NOME DA COLUNA E DEIXANDO COM 2 CASAS DECIMAIS POR ISSO DO DOIS ALI DEPOIS DA VIRGULA*/
	FROM NOME DA TABELA;
	
	/* SUM() ELE SOLA OS VALORES DA COLUNA E MOSTRA O TOTAL */
	
	SELECT SUM(NOME DA COLUNA) AS VALOR_TOTAL_DA_COLUNA
	FROM NOME DA TABELA;

	/* SUBQUERIES QUANDO UMA QUERI TEM UMA OUTRA QUERI DENTRO*/
	
	
	SELECT COLUNA1, COLUNA2 FROM NOMEDATABELA
	WHERE COLUNA2 > (SELECT AVG(COLUNA2) FROM VENDEDORES); /* AONDE A COLUNA TEM É AMIOR QUE A MEDIA DELA MESMO */
	
	/* MOSTRANDO RESULTADOS POR LINHA */
	
	SELECT NOME, JANEIRO, FEVEREIRO, MARCO,
			(JANEIRO + FEVEREIRO + MARCO) AS TOTAL,
			TRUNCATE((JANEIRO + FEVEREIRO + MARCO)/3,2) AS MEDIA /*ESSE 2 É PARA MOSTRAR QUE VAI TER 2 CASASS DECIMAIS */
			FROM VENDEDORES;


	/* COMO ADICIONAR ALGO EM UMA TABELA JA CRIADA */
	
	ALTER TABLE NOMEDATABELA
	ADD ALGUMA FUNÇÃO (NOMEDACOLUNA);
	
	/*ADICIONANDO UMA NOVA COLUNA */
	
	ALTER TABLE NOMEDATABELA
	ADD NOMEDANOVACOLUNA TIPODACOLUNA;
	
	/*ADICIONANDO UMA NOVA COLUNA EM UMA POSICAO ESPECIFICA */
	
	ALTER TABLE NOMEDATABELA
	ADD COLUMN NOMEDACOLUNA TIPODACOLUNA
	AFTER NOMEDACOLUNAEMQUEELAVAIVIRDEPOIS;
	
	/*MODIFICANDO O TIPO DO CAMPO DA COLUNA */
	
	ALTER TABLE NOMEDATABELA MODIFY NOMEDACOLUNA DATE O NOVO TIPO DA COLUNA; /*DATA É UM TIPO NAO FAZ PARTE DO COMANDO*/
	
	/*RENOMEANDO NOME DA TABELA */
	
	ALTER TABLE NOMEDATABELA
	RENAME NOVONOMEDATABELA;
	
	/* ORGANIZANDO CHAVES CONSTRAINT */
	
	ADICIONANDO UMA CHAVE PRIMARIA FORA DA TABELA (JEITO CERTO DE FAZER) 

	ALTER TABLE NOMEDATABELA ADD CONSTRAINT PK_CLIENTE /*NOME DA CHAVE PK SIGNIFICA CHAVE PRIMARIA PRIMARY KEY*/
	PRIMARY KEY (NOMEDACOLUNA);
	
	ALTER TABLE NOMEDATABELASECUNDARIA ADD CONSTRAINT FK_CLIENTE_TELEFONE /*NOME DA CHAVE SECUNDARIA FK NOME DA TABELA AONDE A CHAVE SECUNDARIA ESTÁ E O NOME DE ONDE ELA VEIO NESSE CASO DA TABELA CLIENTE */
	FOREIGN KEY (ID_CLIENTE) REFERENCES NOMEDATABELA (IDCLIENTE);
	
	/*DICIONARIO DE DADOS*/
	
	 USE information_schema
	 USE MYSQL
	 USE performance_schema


	/* TABELA DE ENTIDADE ASSOCIATIVA N X N (N PARA N) */
	
	É UMA TABELA QUE UNA AS 2 OUTRAS TABELAS POIS É UM RELAÇÃO DE N PARA N (MUITOS PARA MUITOS)
	
	EX  CREATE TABLE CARRO_COR(   /* NESSE EXEMPLO UM CARRO PODE TER VARIAS CORES E PODE TER MAIS DE UMA COR NO CARRO*/
		ID_CARRO INT,
		ID_COR INT
		PRIMARY KEY(ID_CARRO,ID_COR)
		);
		
		
	/* ESTRUTURA DE UMA TRIGGER */
	
	CREATE TRIGGER NOME
	BEFORE/AFTER INSERT/DELETE/UPDATE ON TABELA
	FOR EACH ROW (PARA CADA LINHA)
	BEGIN -> INICIO
	
		QUALQUER COMANDO SQL
		
	END -> FIM
	
	-----------------------------------------------------------------
	
	/*FAZENDO UM BACKUP DA TABELA */
	
	DELEMITADOR $
	
	CREATE TRIGGER BACKUP_USER
	BEFORE DELETE ON USUARIO
	FOR EACH ROW 
	BEGIN  
	
		INSERT INTO BKP_USUARIO VALUES(NULL,OLRD.IDUSUARIO, OLD.NOME, OLD.LOGIN);
		
	END 
	$