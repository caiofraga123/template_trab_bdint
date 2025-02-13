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
 
![Alt text](https://github.com/caiofraga123/template_trab_bdint/blob/main/Modelo%20Conceitual%20DevImperato.jpeg)
    
    
#### 5.1 Validação do Modelo Conceitual
    [Grupo01]: Gabriel de Paula Brunetti
    [Grupo02]: Matheus Santos Nascimento

#### 5.2 Descrição dos dados 
 <br>
    ENDERECO: Tabela que armazena as informações relativas ao Endereço. <br>
    uf: Campo que armazena o uf (unidade federativa) da pessoa. <br>
    cidade: Campo que armazena a cidade onde a pessoa reside. <br>
    tipo_logradouro: Campo que armazena o tipo de logradouro, ex:(Av, rua, alameda, etc).<br>
    logradouro: Nome do local, ex:(Rua Florisbela Dias Corradi).<br>
    num: Campo que armazena o numero do local onde a pessoa reside.<br>
    bairro: Campo que armazena o bairro que a pessoa reside.<br>
 <br>
    COMPLEMENTO: Campo que armazena informações relativas ao Complemento do Endereco.<br>
    codigo: Campo relativo ao codigo do complemento.<br>
    descricao: Campo relativo a descrição do complemento.<br>
 <br>
    PESSOA: Tabela que armazena as informações relativas a Pessoa. <br>
    codigo: Campo que armazena o codigo da pessoa. <br>
    rg: Campo que armazena o rg da pessoa. <br>
    nome: Campo que armazena o nome da pessoa. <br>
    telefone: Campo que armazena o numero de celular da pessoa. <br>
 <br>
    EMPREGADO: Tabela que armazena as informações relativas a Empregado, herdando atributos de PESSOA. <br>
    salario:  Campo que armazena o salario do empregado.<br>
 <br>
    ENTREGADOR: Tabela que armazena as informações relativas a Entregador, herdando atributos de EMPREGADO. <br>
    comissao: Campo que armazena o valor da comissao ganha a cada entrega.<br>
    placa: Campo que armazena a placa do veiculo.<br>
 <br>
    VEICULO: Tabela que armazena as informações relativas ao veiculo usado pelo Entregador.<br>
    codigo: Campo que armazena o codigo do veiculo.<br>
    tipo_vei: Campo que armazena o tipo de veiculo usado pelo entregador.<br>
<br>
    PEDIDOS: Tabela que armazena as informações relativas a Pedidos. <br>
    data_hora_pedido: Campo que armazena a data e a hora que o pedido foi feito.<br>
    cod_pedido: Campo que armazena o codigo do pedido<br>
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
   ![Alt text](https://github.com/caiofraga123/template_trab_bdint/blob/main/Modelo%20Logico%20DevImperato.jpeg)
 
### 7	MODELO FÍSICO<br>
    drop table if exists pessoa, complemento, empregado, entregador, veiculo, pedidos, pedidos_alimentos, alimentos, atendimento cascade;

    create table pessoa (
     codigo integer,
     rg integer,
     nome varchar(100),
     telefone integer,
     uf varchar(2),
     cidade varchar(50),
     bairro varchar(60),
     tipo_logradouro varchar(50),
     logradouro varchar(50),
     num integer,
     primary key (codigo)
    );

    create table veiculo (
     codigo integer,
     tipo_vei varchar(20),
     primary key(codigo)
    );

    create table empregado(
     cod_empregado integer references pessoa(codigo),
     salario float,
     primary key(cod_empregado),
     unique(cod_empregado)
    );

    create table entregador(
     cod_entregador integer references empregado(cod_empregado),
     comissao float,
     fk_veiculo_codigo integer references veiculo(codigo),
     placa varchar(7),
     primary key(cod_entregador)
    );

    create table complemento (
     fk_pessoa_codigo integer references pessoa(codigo),
     descricao varchar(75)
    );

    create table alimentos(
     codigo integer primary key,
     nome varchar(100),
     valor float
    );

    create table pedidos(
     cod_pedido integer,
     fk_ENTREGADOR_codigo integer references entregador(cod_entregador),
     data_hora_inicio timestamp,
     data_hora_entrega timestamp,
     primary key(cod_pedido),
     unique(cod_pedido)
    );

    create table pedidos_alimentos(
     fk_PEDIDOS_cod_pedido integer references pedidos(cod_pedido),
     fk_ALIMENTOS_codigo integer references alimentos(codigo),
     qtd integer
    );

    create table atendimento(
     fk_PEDIDOS_cod_pedido integer references pedidos(cod_pedido),
     fk_PESSOA_codigo integer references pessoa(codigo),
     fk_EMPREGADO_codigo integer references empregado(cod_empregado)
    );
       
### 8	INSERT APLICADO NAS TABELAS DO BANCO DE DADOS<br>

    insert into pessoa(codigo, rg, nome, telefone, uf, cidade, bairro, tipo_logradouro, num)
    values
    (10, 2756844, 'Elizeu Faria Lima', 966952413, 'ES', 'Cachoeirinha de Itaúna', 'Cristovão Colombo', 'Aeroporto', 120),
    (20, 3874627, 'Pedro Antônio Barcelos de Oliveira', 978625341, 'ES', 'Serra', 'Ribamar Limão', 'Alameda', 235),
    (30, 3982754, 'Halisson Julio Lopes Pereira', 908743627, 'ES', 'Água Doce do Norte', 'Vila Nelita', 'Ponte', 50),
    (40, 3902094, 'Gustavo Alves Caetano', 917284036, 'ES', 'Barra de São Francisco', 'Vila Pavão', 'Avenida', 413),
    (50, 3895123, 'Rafael Barbosa Martins', 927833513, 'ES', 'Cariacica', 'Santa Bárbara','Rua', 60),
    (60, 3413895, 'Caio Fraga Coelho Cintra', 904734332, 'ES', 'Colatina', 'Santa Terezinha' ,'Avenida', 313),
    (70, 9934313, 'Ricardo Leite Rodrigues', 900813324, 'ES', 'Baixo Guandú', 'Cristo Rei', 'Viaduto', 380),
    (80, 4787731, 'Fellipy Silva Pereira', 988974993, 'ES', 'Fundão', 'Frentinha', 'Praça', 371);

    insert into veiculo(codigo, tipo_vei)
    values
    (1, 'Moto'),
    (2, 'Carro'),
    (3, 'Bicicleta');

    insert into empregado(cod_empregado, salario)
    values
    (20, 2113.60),
    (30, 2143.30),
    (60, 2310.80);

    insert into entregador(cod_entregador, comissao, fk_veiculo_codigo, placa)
    values
    (20, 47.90, 1, 'MSP1963'),
    (30, 53.40, 2, 'TMJ1996');

    insert into complemento(fk_pessoa_codigo, descricao)
    values
    (10, 'B20'),
    (40, 'D45'),
    (50, '67L'),
    (70, '27B');

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

    insert into pedidos(cod_pedido, fk_entregador_codigo, data_hora_inicio, data_hora_entrega)
    values
    (1, 30, '2022-10-28 17:30', '2022-10-28 18:12'),
    (2, 20, '2022-10-28 18:30', '2022-10-28 19:11'),
    (3, 20, '2022-10-28 19:00', '2022-10-28 19:37'),
    (4, 30, '2022-10-28 19:13', '2022-10-28 19:58'),
    (5, 30, '2022-10-28 19:21', '2022-10-28 20:07');

    insert into pedidos_alimentos(fk_PEDIDOS_codigo_pedido, fk_ALIMENTOS_codigo, qtd)
    values
    (1, 20, 1),
    (2, 16, 2),
    (3, 15, 3),
    (4, 18, 4),
    (5, 8, 1);

    insert into atendimento(fk_PEDIDOS_cod_pedido, fk_PESSOA_codigo, fk_EMPREGADO_codigo)
    values
    (1, 70, 30),
    (2, 40, 20),
    (3, 10, 20),
    (4, 70, 30),
    (5, 80, 30);

### 9	TABELAS E PRINCIPAIS CONSULTAS<br>
    https://colab.research.google.com/drive/1Ie0mZ6wyT8ukQDK-NIoOL3t9yJ44fnhV?usp=sharing
    
#### 9.1	CONSULTAS DAS TABELAS COM TODOS OS DADOS INSERIDOS (Todas) <br>

># Marco de Entrega 01: Do item 1 até o item 9.1<br>

#### 9.2	CONSULTAS DAS TABELAS COM FILTROS WHERE (Mínimo 4)<br>
     SELECT codigo, nome FROM alimentos WHERE nome LIKE 'Marmita%';

     SELECT codigo, nome, telefone FROM pessoa WHERE tipo_logradouro = 'Avenida';

     SELECT cod_pedido, data_hora_entrega FROM pedidos WHERE fk_entregador_codigo = 20;

     SELECT fk_pedidos_cod_pedido, fk_alimentos_codigo FROM pedidos_alimentos WHERE qtd >= 2;

     SELECT cod_empregado FROM empregado WHERE salario < 2200;

#### 9.3	CONSULTAS QUE USAM OPERADORES LÓGICOS, ARITMÉTICOS E TABELAS OU CAMPOS RENOMEADOS (Mínimo 11) <br>
    select fk_pedidos_cod_pedido as cod_do_pedido, fk_alimentos_codigo as cod_do_alimento from pedidos_alimentos;
    
    select cod_entregador as cod_do_entregador, comissao, fk_veiculo_codigo as cod_do_veiculo, placa from entregador;
    
    select cod_pedido, fk_entregador_codigo as cod_do_entregador, data_hora_inicio as horario_do_pedido, data_hora_entrega as horario_da_entrega
    from pedidos;
    
    select  a.nome ,data_hora_entrega - data_hora_inicio as "Tempo de espera"from pedidos p 
                            inner join pedidos_alimentos pa 
                            on(pa.fk_pedidos_cod_pedido = p.cod_pedido)
                            inner join alimentos a 
                            on(a.codigo = pa.fk_alimentos_codigo);
    
    select empregado.salario, empregado.salario + (entregador.comissao * count(pedidos.fk_entregador_codigo)) as salario_comissao from empregado
                            inner join entregador
                            on empregado.cod_empregado = entregador.cod_entregador
                            inner join pedidos
                            on entregador.cod_entregador = pedidos.fk_entregador_codigo
                            group by empregado.salario, entregador.comissao;
                            
                            
    select salario, salario - (salario * 0.1) as salario_menos_10_porcento from empregado;
    
    select valor from alimentos where valor > 5 and valor < 15;
    
    select valor from alimentos where valor is not null;
    
    select valor from alimentos where valor > 22 or valor < 10;
    
    select qtd from pedidos_alimentos where qtd > 1 and qtd < 5 ;
                           
    select cod_pedido from pedidos where cod_pedido > 2 and cod_pedido < 10;    

#### 9.4	CONSULTAS QUE USAM OPERADORES LIKE E DATAS (Mínimo 12) <br>
    a) Criar outras 5 consultas que envolvam like ou ilike
      select * from alimentos a 
      where a.nome ilike 'Bolo%'
      order by a.codigo asc 
      
      select p.nome from pessoa p 
      where p.codigo in (select c.fk_pessoa_codigo  from complemento c) and p.nome ilike 'r%'
      
      select a.nome from alimentos a 
      where a.nome like 'Porção%'
      
      select p.nome from pessoa p 
      where p.nome like '%Rodrigues%'
      order by p.nome

      select p.cidade, count(p.cidade)  from pessoa p 
      where p.cidade ilike 'c%'
      group by p.cidade
      order by p.cidade desc 
     
    b) Criar uma consulta para cada tipo de função data apresentada.
    
      select cast(p.data_hora_inicio as DATE), count(cast(p.data_hora_inicio as DATE)) as "Pedidos" from pedidos p  
      group by cast(p.data_hora_inicio as DATE)
      order by count(p.data_hora_inicio) desc 
      
#### 9.5	INSTRUÇÕES APLICANDO ATUALIZAÇÃO E EXCLUSÃO DE DADOS (Mínimo 6)<br>
     DELETE FROM alimentos WHERE valor > 35;
 
     DELETE FROM empregado WHERE cod_empregado = 100;

     DELETE FROM pessoa WHERE codigo = 100;

     UPDATE empregado SET salario = 2257.80 WHERE cod_empregado = 90;

     UPDATE alimentos SET valor = 26.50 WHERE codigo = 14;

     UPDATE alimentos SET valor = 23.50 WHERE codigo = 20;

#### 9.6	CONSULTAS COM INNER JOIN E ORDER BY (Mínimo 6)<br>

   select pessoa.nome, pessoa.cidade, pessoa.bairro, 
                            pessoa.tipo_logradouro, alimentos.nome as nome_alimento, 
                            veiculo.tipo_vei, complemento.descricao from pedidos
                            inner join pedidos_alimentos
                            on pedidos.cod_pedido = pedidos_alimentos.fk_PEDIDOS_cod_pedido
                            inner join alimentos 
                            on pedidos_alimentos.fk_PEDIDOS_cod_pedido = alimentos.codigo
                            inner join entregador
                            on pedidos.fk_entregador_codigo = entregador.cod_entregador
                            inner join veiculo
                            on entregador.fk_veiculo_codigo = veiculo.codigo
                            inner join atendimento
                            on pedidos.cod_pedido = atendimento.fk_pedidos_cod_pedido
                            inner join empregado
                            on entregador.cod_entregador = empregado.cod_empregado
                            inner join pessoa
                            on empregado.cod_empregado = pessoa.codigo
                            inner join complemento
                            on pessoa.codigo = complemento.fk_pessoa_codigo
 
   select pessoa.nome as nome_pessoa,  alimentos.nome as nome_alimentos from pessoa
                            inner join atendimento
                            on  pessoa.codigo = atendimento.fk_pessoa_codigo
                            inner join pedidos
                            on atendimento.fk_pedidos_cod_pedido = pedidos.cod_pedido
                            inner join pedidos_alimentos 
                            on pedidos.cod_pedido = pedidos_alimentos.fk_pedidos_cod_pedido
                            inner join alimentos
                            on pedidos_alimentos.fk_pedidos_cod_pedido = alimentos.codigo;
 
 select alimentos.nome as nome_alimentos,  pedidos_alimentos.qtd from alimentos
                            inner join pedidos_alimentos
                            on  alimentos.codigo = pedidos_alimentos.fk_alimentos_codigo;
 
 select pessoa.nome as cliente_que_mais_pedem, pedidos_alimentos.qtd from pessoa
                            inner join atendimento
                            on  pessoa.codigo = atendimento.fk_pessoa_codigo
                            inner join pedidos
                            on atendimento.fk_pedidos_cod_pedido = pedidos.cod_pedido
                            inner join pedidos_alimentos 
                            on pedidos.cod_pedido = pedidos_alimentos.fk_pedidos_cod_pedido
                            inner join alimentos
                            on pedidos_alimentos.fk_pedidos_cod_pedido = alimentos.codigo
                            order by qtd desc;
 
 select pessoa.nome as nome_pessoa,  alimentos.nome as nome_alimentos,
 pedidos.data_hora_entrega - pedidos.data_hora_inicio as tempo_de_espera from pessoa
                            inner join atendimento
                            on  pessoa.codigo = atendimento.fk_pessoa_codigo
                            inner join pedidos
                            on atendimento.fk_pedidos_cod_pedido = pedidos.cod_pedido
                            inner join pedidos_alimentos 
                            on pedidos.cod_pedido = pedidos_alimentos.fk_pedidos_cod_pedido
                            inner join alimentos
                            on pedidos_alimentos.fk_pedidos_cod_pedido = alimentos.codigo
 
 select sum(valor) as total from alimentos
                            inner join pedidos_alimentos 
                            on alimentos.codigo = pedidos_alimentos.fk_alimentos_codigo
                            inner join pedidos
                            on pedidos_alimentos.fk_pedidos_cod_pedido = pedidos.cod_pedido;
 
#### 9.7	CONSULTAS COM GROUP BY E FUNÇÕES DE AGRUPAMENTO (Mínimo 6)<br>
    a) Criar minimo 2 envolvendo algum tipo de junção
       select cast(p.data_hora_inicio as DATE), count(cast(p.data_hora_inicio as DATE)) as "Pedidos" from pedidos p  
       group by cast(p.data_hora_inicio as DATE)
       order by count(p.data_hora_inicio) desc 

       select p.nome as "Cliente que nunca pediram" from pessoa p 
       where p.nome not in (select p.nome from empregado e 
       inner join pessoa p
       on(e.cod_empregado = p.codigo)
       ) and p.nome not in (
       select p.nome from empregado e
       inner join atendimento a
       on(p.codigo = a.fk_pessoa_codigo))
       order by p.nome

       select p.nome as "Cliente", al.nome as "Alimento", al.valor as "Valor pago" from pessoa p
       inner join atendimento a
       on(p.codigo = a.fk_pessoa_codigo)
       inner join pedidos pe 
       on(a.fk_pedidos_cod_pedido = pe.cod_pedido)
       inner join pedidos_alimentos pa 
       on(pe.cod_pedido = pa.fk_pedidos_cod_pedido)
       inner join alimentos al 
       on(al.codigo = pa.fk_alimentos_codigo)

       select p.nome, e2.comissao +  e.salario as "Salario mensal", extract(month from p2.data_hora_entrega) as "Mês" from pessoa p  
       inner join empregado e 
       on(e.cod_empregado = p.codigo)
       inner join entregador e2
       on(e.cod_empregado = e2.cod_entregador)
       inner join pedidos p2 
       on(p2.fk_entregador_codigo = e2.cod_entregador)
       group by p.nome, e2.comissao +  e.salario, extract(month from p2.data_hora_entrega)

#### 9.8	CONSULTAS COM LEFT, RIGHT E FULL JOIN (Mínimo 4)<br>
     SELECT empregado.cod_empregado, pessoa.nome, pedidos.cod_pedido
     FROM pedidos
     RIGHT OUTER JOIN empregado
     ON (empregado.cod_empregado = pedidos.fk_entregador_codigo)
     INNER JOIN pessoa
     ON (empregado.cod_empregado = pessoa.codigo);

     SELECT alimentos.codigo, alimentos.valor, pedidos_alimentos.fk_alimentos_codigo
     FROM alimentos
     LEFT OUTER JOIN pedidos_alimentos
     ON (alimentos.codigo = pedidos_alimentos.fk_alimentos_codigo);

     SELECT pessoa.codigo, entregador.cod_entregador, empregado.salario
     FROM pessoa
     FULL JOIN entregador
     ON (pessoa.codigo = entregador.cod_entregador)
     INNER JOIN empregado
     ON (entregador.cod_entregador = empregado.cod_empregado);

#### 9.9	CONSULTAS COM SELF JOIN E VIEW (Mínimo 6)<br>
        a) Não foi possível devido à falta de auto relacionamento.
           
           create view nomes_dos_empregados as
           select pessoa.nome as empregados
           from pessoa inner join empregado
           on pessoa.codigo = empregado.cod_empregado;
           select * from nomes_dos_empregados;
 
        b) Outras junções com views que o grupo considere como sendo de relevante importância para o trabalho.
           
           create view salario_anual as
           (select cod_empregado, salario , salario*12 as salario_anual from empregado)
           select * from salario_anual;
 
           create view media_qntd as
           select fk_alimentos_codigo, avg(pedidos_alimentos.qtd) as quantidade_media from pedidos_alimentos
           group by fk_alimentos_codigo;
           select * from media_qntd;
 
           create view salario_max_mini 
           as select max(alimentos.valor) as maximo, 
           min(alimentos.valor) as minimo from alimentos;
           select * from salario_max_mini;

#### 9.10	SUBCONSULTAS (Mínimo 4)<br>
     a) Criar minimo 1 envolvendo GROUP BY
     
        select a.fk_pessoa_codigo, count(*) as "Qtd" from atendimento a   
        where a.fk_pessoa_codigo in (select p.codigo from pessoa p where uf = 'ES')  
        group by a.fk_pessoa_codigo
        order by 2 desc
        
     b) Criar minimo 1 envolvendo algum tipo de junção
  
        select p.nome as "Cliente que nunca pediram" from pessoa p 
        where p.nome not in (select p.nome from empregado e 
        inner join pessoa p
        on(e.cod_empregado = p.codigo)
        ) and p.nome not in (
        select p.nome from empregado e
        inner join atendimento a
        on(p.codigo = a.fk_pessoa_codigo))
        order by p.nome

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


