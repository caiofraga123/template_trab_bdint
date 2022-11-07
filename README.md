# TRABALHO 01:  DevImperato
Trabalho desenvolvido durante a disciplina de Banco de dados

# Sumário

### 1. COMPONENTES<br>
Integrantes do grupo<br>
Caio Fraga: caiofcintra@gmail.com<br> 
Ricardo Leite: ricardoleiterodriguesbe@gmail.com<br>
Paulo Victor: paulovictoralves.contato@gmail.com<br>
...<br>

### 2.INTRODUÇÃO E MOTIVAÇÃO<br>
Este documento contém a especificação do projeto do banco de dados <nome do projeto> 
<br>e motivação da escolha realizada. <br>

> O restaurante "DevImperato" busca colaborar com desenvolvimento de uma alimentação diversa para a sociedade por meio de entregas. Sabendo-se dos desafios para gerenciar pedidos e visando unir as informações relativas a empregados, alimentos e clientes em um mesmo local, ficamos motivados com o desenvolvimento deste sistema. O Sistema "DevImperato" tem como objetivo gerenciar todas as informações ao desenvolvimento das atividades de projetos em diversas localidades do país. Para realizar suas operações adequadamente e empresa necessita que sistema que armazene informações relativas das Pessoas, Alimentos, Empregados, Entregadores e também armazenar dados sobre Pedidos. O sistema deverá gerar um conjunto de relatórios que por sua vez atenderá os anseios do restaurante em questão.
 

### 3.MINI-MUNDO<br>

Descrever o mini-mundo! (Não deve ser maior do que 30 linhas, se necessário resumir para justar) <br>
Entrevista com o usuário e identificação dos requisitos.(quando for o caso de sistemas com cliente  real)<br>
Descrição textual das regras de negócio definidas como um  subconjunto do mundo real 
cujos elementos são propriedades que desejamos incluir, processar, armazenar, 
gerenciar, atualizar, e que descrevem a proposta/solução a ser desenvolvida.

> O sistema proposto para a "DevImperato" conterá as informacões aqui detalhadas. Das Pessoas serão armazenados o código, ddd do número, telefone e nome. Um Endereço pertencerá a essa pessoa, contendo uf, localidade, tipo_logradouro, num, complemento. Uma pessoa pode ter apenas um endereço e um endereço pode pertencer à apenas uma pessoa. As Pessoas poderão ser Empregados com salario, e os Empregados poderão ser Entregadores, com comissão, tipo do veículo e placa. As Pessoas farão Pedidos, que terão serão armazenados o código do pedido e a data e a hora em que o pedido foi realizado. Um pedido pode ser feito por apenas uma pessoa, enquanto uma pessoa pode realizar vários pedidos. Pedidos são compostos por Alimentos, que tem código, nome e valor. Um pedido pode ter um ou vários alimentos, enquanto um alimento pode fazer parte de um ou vários pedidos. Os Pedidos são entregaues por Entregador, sendo que um Entregador pode entregar um ou vários Pedidos e um pedido pode ser entregue por apenas um Entregador.

### 4.PERGUNTAS A SEREM RESPONDIDAS E TABELA DE DADOS<br>
    
> A Empresa DevImperato precisa inicialmente dos seguintes relatórios:
* Relatório que mostre o nome dos clientes e qual alimento eles compraram.
* Relatório que mostre todos os alimentos pedidos e a quantidade de vezes que eles foram pedidos.
* Relatorio que mostre quais são os clientes que mais pedem.
* Relatório que mostre o tempo que um pedido demorou para chegar ao cliente. 
* Relatório que mostre o valor total arrecadado da DevImperato.

 ### 5.MODELO CONCEITUAL<br>
 
![Alt text](https://github.com/caiofraga123/template_trab_bdint/blob/main/conceitual.jpeg)
    
    
        
    
#### 5.1 Validação do Modelo Conceitual
    [Grupo01]: Gabriel de Paula Brunetti
    [Grupo02]: Matheus Santos Nascimento

#### 5.2 Descrição dos dados 
    [objeto]: [descrição do objeto]
    
    EXEMPLO:
    ENDERECO: Tabela que armazena as informações relativas ao Endereço. <br>
    uf: Campo que armazena o uf (unidade federativa) da pessoa. <br>
    localidade: Campo que armazena a cidade onde a pessoa mora. <br>
    tipo_logradouro: Campo que armazena o tipo de logradouro (Av, rua, alameda, etc).<br>
    logradouro: Nome do local (Rua Florisbela Dias Corradi).<br>
    num: Campo que armazena o numero do local onde a pessoa reside.<br>
    complemento: Campo que armazena a descrição de onde a pessoa mora ex(perto da loterica).<br>
 <br>
 
    PESSOA: Tabela que armazena as informações relativas a Pessoa. <br>
    codigo: Campo que armazena o codigo da pessoa. <br>
    rg: Campo que armazena o rg da pessoa. <br>
    nome: Campo que armazena o nome da pessoa. <br>
    ddd_num: Campo que armazena o ddd do numero da pessoa. <br>
    telefone: Campo que armazena o numero de celular da pessoa. <br>
 <br>
    EMPREGADO: Tabela que armazena as informações relativas a Empregado, herdando atributos de PESSOA. <br>
    salario:  Campo que armazena o salario do empregado.<br>
 <br>
    ENTREGADOR: Tabela que armazena as informações relativas a Entregador, herdando atributos de EMPREGADO. <br>
    comissao: Campo que armazena o valor da comissao ganha a cada entrega.<br>
    tipo_vei: Campo que armazena o tipo do veiculo usado pelo entregador.<br>
    placa: Campo que armazena a placa do veiculo.<br>
 <br>
    PEDIDOS: Tabela que armazena as informações relativas a Pedidos. <br>
    data_hora: Campo que armazena a data e a hora que o pedido foi feito.<br>
    cod_pedido: Campoq que armazena o codigo do pedido<br>
 <br>
    ALIMENTOS: Tabela que armazena as informações relativas a Alimentos.<br>
    codigo: Campo que armazena o codigo do alimento.<br>
    nome:  Campo que armazena o nome do alimento.<br>
    valor: Campo que armazena o valor do alimento.<br>
    <br>


### 6	MODELO LÓGICO<br>
        a) inclusão do esquema lógico do banco de dados
        b) verificação de correspondencia com o modelo conceitual 
        (não serão aceitos modelos que não estejam em conformidade)
   ![Alt text](https://github.com/caiofraga123/template_trab_bdint/blob/main/logico.jpeg)
 
### 7	MODELO FÍSICO<br>
        drop table if exists pessoa, alimentos, pedidos, pedidos_alimentos, empregado, entregador cascade;

        create table pessoa (
         uf varchar(2),
         localidade varchar(50),
         tipo_logradouro varchar(50),
         logradouro varchar(50),
         num integer,
         complemento varchar(100),
         ddd_num integer,
         telefone integer,
         nome varchar(100),
         codigo integer primary key,
         rg integer
        );

        create table alimentos(
         codigo integer primary key,
         nome varchar(100),
         valor float
        );

        create table pedidos(
         cod_pedido integer primary key,
         fk_PESSOA_codigo integer references pessoa(codigo),
         data_hora_pedido timestamp
        );

        create table pedidos_alimentos(
         fk_PEDIDOS_codigo_pedido integer references pedidos(cod_pedido),
         fk_ALIMENTOS_codigo integer references alimentos(codigo),
         qtd integer
        );

        create table empregado(
         fk_PESSOA_codigo integer,
         salario float
        );

        create table entregador(
         tipo_vei varchar(10),
         placa varchar(7),
         comissao float,
         fk_EMPREGADO_fk_PESSOA_codigo integer,
         fk_PEDIDOS_cod_pedido integer,
         data_hora_entrega timestamp
        );
        
       
### 8	INSERT APLICADO NAS TABELAS DO BANCO DE DADOS<br>
    insert into pessoa(uf, localidade, tipo_logradouro, logradouro, num, complemento, ddd_num, telefone, nome, codigo, rg)
    values
    ('ES', 'Cachoeirinha de Itaúna', 'Aeroporto', 'Casa', 120, 'Proximo ao Aeroporto Golfinho Dalta', 27, 966952413, 'Moisés Savedra Omena', 10, 2756844),
    ('ES', 'Serra', 'Alameda', 'Apartamento', 235, 'Próximo ao Atacado Vem', 27, 978625341, 'Pedro Antônio Barcelos de Oliveira', 20, 3874627),
    ('ES', 'Água Doce do Norte', 'Ponte', 'Apartamento', 50, 'Em frente ao Bar do Jorge', 27, 908743627, 'Halisson Julio Lopes Pereira', 30, 3982754),
    ('ES', 'Barra de São Francisco', 'Avenida', 'Casa', 413, 'À direita do semáforo na frente da Águia Branca', 27, 917284036, 'Gustavo Alves Caetano', 40, 3902094),
    ('ES', 'Cariacica', 'Rua', 'Casa', 60, 'Ao lado ao Parque Santa Bárbara', 27, 927833513, 'Rafael Barbosa Martins', 50, 3895123),
    ('ES', 'Colatina', 'Avenida', 'Casa', 313, 'Próximo à Rodoviária', 27, 904734332, 'Caio Fraga Coelho Cintra', 60, 3413895),
    ('ES', 'Baixo Guandú', 'Viaduto', 'Apartamento', 380, 'Ao lado à linha do trem', 27, 900813324, 'Ricardo Leite Rodrigues', 70, 9934313),
    ('ES', 'Fundão', 'Praça', 'Apartamento', 371, 'Em cima do Skinas Bar', 27, 988974993, 'Fellipy Silva Pereira', 80, 4787731);

    insert into alimentos(codigo, nome, valor)
    values
    (1, 'Sanduíche de peito de peru com cream cheese, alface, tomate e frango desfiado', 7.00),
    (2, 'Sanduíche de carne vegana com rúcula, berinjela, abobrinha, champígnon e pão sírio', 12.00),
    (3, 'Marmita de arroz, feijão tropeiro, batata frita e bife bovino ao molho inglês', 16.50),
    (4, 'Marmita de macarrão, arroz, feijão, aipim frito e peito de frango empanado', 18.00),
    (5, 'Marmita de arroz integral, macarrão, filé de tilápia, ovos de codorna e mini-pastel de carne', 25.00),
    (6, 'Espetinho de carne bovina e suína ao molho branco e farofa yoki', 5.00),
    (7, 'Coxas de frango assada com páprica', 20.00),
    (8, 'Postas de salmão ao molho de maracujá', 37.00),
    (9, 'Batida de frutas tropicais com leite condensado e uma dose de uisque', 11.00),
    (10, 'Frango assado com pimenta do reino, páprica picante, chimichurri e molho de alho', 30.00),
    (12, 'Marmita com lasanha de carne, arroz, feijão fradinho e purê', 25.00),
    (13, 'Marmita com feijoada, arroz, farofa, alface, tomate e pepino', 27.00),
    (14, 'Marmita com strogonoff de frango, baião de dois, tutu de feijão, ', 23.00),
    (15, 'Hamburguer de bife bovino, cebola, alface, queijo e bacon', 21.00),
    (16, 'Porção de batata frita com páprica picante', 31.00),
    (17, 'Porção de aipim frito', 26.00),
    (18, 'Bolo de pote sabor napolitano', 14.00),
    (19, 'Bolo de pote sabor chocolate', 13.00),
    (20, 'Marmita com empadão, arroz, feijão e farofa de bacon', 21.00);

    insert into pedidos(cod_pedido, FK_PESSOA_codigo, data_hora_pedido)
    values
    (1, 40, '2022-10-28 17:30'),
    (2, 50, '2022-10-28 18:30'),
    (3, 60, '2022-10-28 19:00'),
    (4, 70, '2022-10-28 19:13'),
    (5, 80, '2022-10-28 19:21');

    insert into pedidos_alimentos(fk_PEDIDOS_codigo_pedido, fk_ALIMENTOS_codigo, qtd)
    values
    (1, 20, 1),
    (2, 16, 2),
    (3, 15, 3),
    (4, 18, 4),
    (5, 8, 1);

    insert into empregado(salario, fk_PESSOA_codigo)
    values
    (2113.60, 20),
    (2143.30, 30),
    (2310.80, 10);

    insert into entregador(tipo_vei, placa, comissao, fk_EMPREGADO_FK_PESSOA_codigo, FK_PEDIDOS_cod_pedido, data_hora_entrega)
    values
    ('Moto', 'MSP1963', 0.50, 20, 1, '2022-10-28 18:21'),
    ('Moto', 'MSP1963', 1.00, 10, 2, '2022-10-28 19:11'),
    ('Carro', 'TMJ1571', 2.10, 10, 3, '2022-10-28 19:41'),
    ('Moto', 'MSP1963', 1.50, 20, 4, '2022-10-28 19:43'),
    ('Carro', 'TMJ1571', 1.00, 20, 5, '2022-10-28 19:51');


### 9	TABELAS E PRINCIPAIS CONSULTAS<br>
    https://colab.research.google.com/drive/1Ie0mZ6wyT8ukQDK-NIoOL3t9yJ44fnhV?usp=sharing<br>
#### 9.1	CONSULTAS DAS TABELAS COM TODOS OS DADOS INSERIDOS (Todas) <br>

># Marco de Entrega 01: Do item 1 até o item 9.1<br>

#### 9.2	CONSULTAS DAS TABELAS COM FILTROS WHERE (Mínimo 4)<br>
#### 9.3	CONSULTAS QUE USAM OPERADORES LÓGICOS, ARITMÉTICOS E TABELAS OU CAMPOS RENOMEADOS (Mínimo 11)
    a) Criar 5 consultas que envolvam os operadores lógicos AND, OR e Not
    b) Criar no mínimo 3 consultas com operadores aritméticos 
    c) Criar no mínimo 3 consultas com operação de renomear nomes de campos ou tabelas

#### 9.4	CONSULTAS QUE USAM OPERADORES LIKE E DATAS (Mínimo 12) <br>
    a) Criar outras 5 consultas que envolvam like ou ilike
    b) Criar uma consulta para cada tipo de função data apresentada.

#### 9.5	INSTRUÇÕES APLICANDO ATUALIZAÇÃO E EXCLUSÃO DE DADOS (Mínimo 6)<br>
    a) Criar minimo 3 de exclusão
    b) Criar minimo 3 de atualização

#### 9.6	CONSULTAS COM INNER JOIN E ORDER BY (Mínimo 6)<br>
    a) Uma junção que envolva todas as tabelas possuindo no mínimo 2 registros no resultado
    b) Outras junções que o grupo considere como sendo as de principal importância para o trabalho

#### 9.7	CONSULTAS COM GROUP BY E FUNÇÕES DE AGRUPAMENTO (Mínimo 6)<br>
    a) Criar minimo 2 envolvendo algum tipo de junção

#### 9.8	CONSULTAS COM LEFT, RIGHT E FULL JOIN (Mínimo 4)<br>
    a) Criar minimo 1 de cada tipo

#### 9.9	CONSULTAS COM SELF JOIN E VIEW (Mínimo 6)<br>
        a) Uma junção que envolva Self Join (caso não ocorra na base justificar e substituir por uma view)
        b) Outras junções com views que o grupo considere como sendo de relevante importância para o trabalho

#### 9.10	SUBCONSULTAS (Mínimo 4)<br>
     a) Criar minimo 1 envolvendo GROUP BY
     b) Criar minimo 1 envolvendo algum tipo de junção

># Marco de Entrega 02: Do item 9.2 até o ítem 9.10<br>

### 10 RELATÓRIOS E GRÁFICOS (Usar template disponibilizado)
[Template de relatórios](https://github.com/discipbdint/public_samples/blob/main/BD_Exemplo_Relatorios_Empresa_VA.ipynb "Template relatórios")

#### a) análises e resultados provenientes do banco de dados desenvolvido (usar modelo disponível)
#### b) link com exemplo de relatórios será disponiblizado pelo professor no AVA
#### OBS: Esta é uma atividade de grande relevância no contexto do trabalho. Mantenha o foco nos 5 principais relatórios/resultados visando obter o melhor resultado possível.

    

### 11	AJUSTES DA DOCUMENTAÇÃO, CRIAÇÃO DOS SLIDES E VÍDEO PARA APRESENTAÇAO FINAL <br>

#### a) Modelo (pecha kucha)<br>
#### b) Tempo de apresentação 6:40 

># Marco de Entrega 03: Itens 10 e 11<br>
<br>
<br>
<br> 



### 12 FORMATACAO NO GIT:<br> 
https://help.github.com/articles/basic-writing-and-formatting-syntax/
<comentario no git>
    
##### About Formatting
    https://help.github.com/articles/about-writing-and-formatting-on-github/
    
##### Basic Formatting in Git
    
    https://help.github.com/articles/basic-writing-and-formatting-syntax/#referencing-issues-and-pull-requests
    
    
##### Working with advanced formatting
    https://help.github.com/articles/working-with-advanced-formatting/
#### Mastering Markdown
    https://guides.github.com/features/mastering-markdown/

    
### OBSERVAÇÕES IMPORTANTES

#### Todos os arquivos que fazem parte do projeto (Imagens, pdfs, arquivos fonte, etc..), devem estar presentes no GIT. Os arquivos do projeto vigente não devem ser armazenados em quaisquer outras plataformas.
1. <strong>Caso existam arquivos com conteúdos sigilosos<strong>, comunicar o professor que definirá em conjunto com o grupo a melhor forma de armazenamento do arquivo.

#### Todos os grupos deverão fazer Fork deste repositório e dar permissões administrativas ao usuário do git "profmoisesomena", para acompanhamento do trabalho.

#### Os usuários criados no GIT devem possuir o nome de identificação do aluno (não serão aceitos nomes como Eu123, meuprojeto, pro456, etc). Em caso de dúvida comunicar o professor.


Link para BrModelo:<br>
http://www.sis4.com/brModelo/download.html
<br>


Link para curso de GIT<br>
![https://www.youtube.com/curso_git](https://www.youtube.com/playlist?list=PLo7sFyCeiGUdIyEmHdfbuD2eR4XPDqnN2?raw=true "Title")


