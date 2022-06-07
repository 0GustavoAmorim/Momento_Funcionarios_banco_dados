
# Momento e Seus Funcionarios

#### Atividade em SQL onde o instuito é realizar algumas consultas e conseguir encontrar as respostas para as perguntas passadas pelo professor Gabriel do Insituto PROA.

### 1 - Inclua suas próprias informações no departamento de tecnologia da empresa.
```
INSERT INTO funcionarios(funcionario_id,primeiro_nome,sobrenome,email,telefone,dataContratacao,ocupacao_id,salario,gerente_id,departamento_id) VALUES (207,'Gustavo','Amorim','gustavoamorilsilva@gmail.com','11971590116','2022-06-05',9,5000.00,null,6);
```

### 2 - A administração está sem funcionários. Inclua os outros elementos do seu grupo do demoday no departamento de administração.
```
INSERT INTO funcionarios(funcionario_id,primeiro_nome,sobrenome,email,telefone,dataContratacao,ocupacao_id,salario,gerente_id,departamento_id) VALUES (208,'Ellen','Silva','ellensilvateixei@momento.org','11971717171','2022-05-06',3,24000.00,NULL,1);
INSERT INTO funcionarios(funcionario_id,primeiro_nome,sobrenome,email,telefone,dataContratacao,ocupacao_id,salario,gerente_id,departamento_id) VALUES (209,'Daniele','Simões','danielesimoes@momento.org','11972727272','2022-05-06',3,24000.00,NULL,1);
INSERT INTO funcionarios(funcionario_id,primeiro_nome,sobrenome,email,telefone,dataContratacao,ocupacao_id,salario,gerente_id,departamento_id) VALUES (210,'Jonathan','Silva','johnconceicao@momento.org','11973737373','2022-05-06',3,24000.00,NULL,1);
INSERT INTO funcionarios(funcionario_id,primeiro_nome,sobrenome,email,telefone,dataContratacao,ocupacao_id,salario,gerente_id,departamento_id) VALUES (211,'Leonardo','Vinicius','leonardopoker25@momento.org','11974747474','2022-05-06',3,24000.00,NULL,1);
INSERT INTO funcionarios(funcionario_id,primeiro_nome,sobrenome,email,telefone,dataContratacao,ocupacao_id,salario,gerente_id,departamento_id) VALUES (212,'Thiago','Antenor','anterthiago@momento.org','11975757575','2022-05-06',3,24000.00,NULL,1);
INSERT INTO funcionarios(funcionario_id,primeiro_nome,sobrenome,email,telefone,dataContratacao,ocupacao_id,salario,gerente_id,departamento_id) VALUES (213,'Gabriel','Marques','marques@momento.org','11976767676','2022-05-06',3,24000.00,NULL,1);
```
### 3 - Agora diga, quantos funcionários temos ao total na empresa?
47

Query
```
SELECT COUNT(*) FROM `funcionarios`;
```

### 4 - Quantos funcionários temos no departamento de finanças?
4

Query
```
SELECT * FROM funcionarios WHERE departamento_id = 10;
```

### 5 - Qual a média salarial do departamento de tecnologia?
5633.33

Query
```
SELECT AVG(salario) FROM funcionarios WHERE departamento_id = 6;
```

### 6 - Quanto o departamento de Transportes gasta em salários?
41200.00

Query
```
SELECT SUM(salario) FROM funcionarios WHERE departamento_id = 5;
```

### 7 - Um novo departamento foi criado. O departamento de inovações. Ele será locado no Brasil. Por favor, adicione-o no banco de dados.
```
INSERT INTO departamento (departamento_name, posicao_id)
VALUES('Inovações',5400);
```

### 8 - Novos Funcionários!
#### Três novos funcionários foram contratados para o departamento de inovações. Por favor, adicione-os: William Ferreira, casado com Inara Ferreira, possui um filho chamado Gabriel que tem 4 anos e adora brincar com cachorros. Ele será programador.Já a Fernanda Lima, que é casada com o Rodrigo, não possui filhos. Ela vai ocupar a posição de desenvolvedora.  Por último, a Gerente do departamento será Fabiana Raulino. Casada, duas filhas (Maya e Laura). 

Query
```
-- Add William

INSERT INTO funcionarios
(funcionario_id,primeiro_nome,sobrenome,email,telefone,dataContratacao,ocupacao_id,salario,gerente_id,departamento_id) 
VALUES (214,'William','Ferreira','williamferreira@momento.org','11977777777','2022-05-06',20,9000.00,NULL,20);


-- Add Fernanda Lima

INSERT INTO funcionarios
(funcionario_id,primeiro_nome,sobrenome,email,telefone,dataContratacao,ocupacao_id,salario,gerente_id,departamento_id) 
VALUES (215,'Fernanda','Lima','fernandalima@momento.org','11978787878','2022-05-06',20,10000.00,NULL,20);


-- Add gerenete Fabiana Raulino

INSERT INTO funcionarios
(funcionario_id,primeiro_nome,sobrenome,email,telefone,dataContratacao,ocupacao_id,salario,gerente_id,departamento_id) 
VALUES (216,'Fabiana','Raulino','fabianaraulino@momento.org','11979797979','2022-05-06',21,20000.00,NULL,20);

-- ADICIONANDO DEPENDENTES

-- Dependentes William

INSERT INTO dependentes(primeiro_nome, sobrenome, parentesco, funcionario_id)
VALUES('Inara', 'Ferreira', 'cônjuge',214);

INSERT INTO dependentes(primeiro_nome, sobrenome, parentesco, funcionario_id)
VALUES('Gabriel', 'Ferreira', 'filho(a)', 214);

-- Dependentes Fernanda Lima

INSERT INTO dependentes (primeiro_nome, sobrenome, parentesco, funcionario_id) VALUES('Rodrigo', 'Lima', 'cônjuge', 215);
```

### 9 - Informe todas as regiões em que a empresa atua acompanhadas de seus países.

```
SELECT paises.pais_name AS Pais, regiao.regiao_name FROM paises INNER JOIN regiao WHERE paises.regiao_id = regiao.regiao_id;
```

### 10 - Joe Sciarra é filho de quem?

Filho de Ismael Sciarra

Query
```
SELECT funcionarios.primeiro_nome, funcionarios.sobrenome FROM dependentes INNER JOIN funcionarios WHERE dependentes.funcionario_id = funcionarios.funcionario_id AND dependentes.primeiro_nome LIKE '%Joe%' AND dependentes.sobrenome LIKE '%Sciarra%';
```

### 11 - Jose Manuel possui filhos?

Não possui filhos
```
SELECT funcionarios.primeiro_nome, dependentes.primeiro_nome FROM dependentes INNER JOIN funcionarios WHERE dependentes.funcionario_id = funcionarios.funcionario_id AND dependentes.sobrenome LIKE '%Manuel%';
```

### 12 - Qual região possui mais países?

Europa com 25 Países
```
SELECT regiao.regiao_name, COUNT(paises.regiao_id) FROM paises INNER JOIN regiao WHERE regiao.regiao_id = paises.regiao_id;
```

### 13 - Exiba o nome cada funcionário acompanhado de seus dependentes.
```
SELECT funcionarios.primeiro_nome, funcionarios.sobrenome, dependentes.primeiro_nome, dependentes.sobrenome FROM funcionarios INNER JOIN dependentes WHERE funcionarios.funcionario_id = dependentes.funcionario_id;
```

### 14 - Karen Partners possui um cônjuge?

Sim, Alec Partners
```
SELECT dependentes.primeiro_nome, dependentes.sobrenome FROM dependentes INNER JOIN funcionarios WHERE funcionarios.funcionario_id = dependentes.funcionario_id AND funcionarios.primeiro_nome LIKE '%Karen%' AND funcionarios.sobrenome LIKE '%Partners%';
```

### 15 - O ID da tabela de países não segue um padrão numérico. Na sua visão, qual o impacto disso no desenvolvimento do banco?

Resposta: 
```
Nenhum, pois o ID atende os requisitos de chave primaria e é identificado pelas siglas dos paises, exemplo: HongKong = HK.
```

### 16 - Escolha um país para se mudar. Qual seria esse país? Por que escolheria esse país? E o departamento. O que seria? Como seriam seus funcionários?
Resposta:
```
Criaria o Departamento do TDAH, adicionaria as pessoas mais legais e quase produtivas, no Reino Unido, mais especificamente em Londres, é acho que meus funcionários do Demoday gostariam de Londres. 
```

### 17 - Atualize as informações na tabela para que seu departamento seja criado.
Query
```
INSERT INTO posicao (endereco, cidade, pais_id)
VALUES ('Gherkin', 'London', 'UK');

INSERT INTO departamento (departamento_name, posicao_id)
VALUES('Departamento do TDAH',5401);
```
