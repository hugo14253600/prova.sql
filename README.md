1 - Cenário
Estou responsável por uma organização esportiva que gerencia diversos times, jogadores e campeonatos. Para manter o controle de todas as informações relacionadas, desde os detalhes dos times e jogadores até as estatísticas das partidas e premiações, um sistema de banco de dados se torna essencial.

Necessidades do Sistema de Banco de Dados:

Gestão de Times e Jogadores:

Times: É necessário armazenar informações detalhadas sobre cada time, como nome, cidade, endereço e outras informações de contato. Isso permite manter um registro centralizado de todos os times participantes.
Jogadores: Para cada time, é importante registrar os jogadores, incluindo nome, posição e vínculo com o time. Isso possibilita o gerenciamento eficiente dos membros de cada equipe.
Registros de Partidas:

Partidas: O sistema deve registrar dados sobre cada partida realizada, incluindo a data, hora, local, times participantes e resultados. Isso permite acompanhar o desempenho de cada time ao longo do tempo e analisar estatísticas de jogos.
Gestão de Campeonatos:

Campeonatos: É crucial manter informações detalhadas sobre os campeonatos realizados, como nome, ano de realização, datas de início e término. Isso ajuda na organização e planejamento de eventos esportivos.
Premiações e Reconhecimentos:

Troféus e Premiações: O sistema deve incluir dados sobre troféus concedidos, como nome, descrição e categoria (por exemplo, artilharia, melhor jogador, melhor goleiro). Isso permite reconhecer e premiar os destaques de cada campeonato.
Inscrições em Campeonatos:

Inscrições: Registrar quais times estão inscritos em cada campeonato é fundamental para organizar as competições e garantir a participação adequada de cada equipe.

2- Modelagem Conceitual
![Diagrama em branco](https://github.com/hugo14253600/prova.sql/assets/162808170/ed599fc6-d5dd-4da7-a302-8998b72f625b)


3 - Modelagem Lógica

![Diagrama em branco (1)](https://github.com/hugo14253600/prova.sql/assets/162808170/a11bd346-ce91-4ff2-99fc-cd13b63f1cf5)


AMBAS MODELAGENS:
[Diagrama em branco (1).pdf](https://github.com/user-attachments/files/15781422/Diagrama.em.branco.1.pdf)



 4 Modelagem Física:
CREATE TABLE Time (
    ID_Time INTEGER PRIMARY KEY,
    Nome VARCHAR(100) NOT NULL,
    Cidade VARCHAR(100) NOT NULL,
    Rua VARCHAR(100),
    Numero INTEGER,
    Bairro VARCHAR(100),
    CEP VARCHAR(20)
);
CREATE TABLE Jogador (
    ID_Jogador INTEGER PRIMARY KEY,
    Nome TEXT,
    Posição TEXT,
    ID_Time INTEGER,
    FOREIGN KEY (ID_Time) REFERENCES Time(ID_Time)
);

);
CREATE TABLE Partida (
    ID_Partida INTEGER PRIMARY KEY,
    Data DATE NOT NULL,
    Hora TIME NOT NULL,
    Local VARCHAR(100) NOT NULL,
    ID_Time1 INTEGER,
    ID_Time2 INTEGER,
    Resultado_Time1 INTEGER,
    Resultado_Time2 INTEGER,
    Melhor_Jogador INTEGER,
    FOREIGN KEY (ID_Time1) REFERENCES Time(ID_Time),
    FOREIGN KEY (ID_Time2) REFERENCES Time(ID_Time),
    FOREIGN KEY (Melhor_Jogador) REFERENCES Jogador(ID_Jogador)
);
CREATE TABLE Campeonato (
    ID_Campeonato INTEGER PRIMARY KEY,
    Nome VARCHAR(100) NOT NULL,
    Ano INTEGER NOT NULL,
    Data_Inicio DATE,
    Data_Fim DATE
);
CREATE TABLE Inscrição (
    ID_Inscricao INTEGER PRIMARY KEY,
    ID_Time INTEGER,
    ID_Campeonato INTEGER,
    FOREIGN KEY (ID_Time) REFERENCES Time(ID_Time),
    FOREIGN KEY (ID_Campeonato) REFERENCES Campeonato(ID_Campeonato)
);
CREATE TABLE Trofeu (
    ID_Trofeu INTEGER PRIMARY KEY,
    Nome VARCHAR(100) NOT NULL,
    ID_Jogador INTEGER,
  	Descricao VARCHAR(255)
);
CREATE TABLE Premiacao (
    ID_Premiacao INTEGER PRIMARY KEY,
    ID_Trofeu INTEGER,
    ID_Jogador INTEGER,
    Ano INTEGER,
    ID_Campeonato INTEGER,
    FOREIGN KEY (ID_Trofeu) REFERENCES Trofeu(ID_Trofeu),
    FOREIGN KEY (ID_Jogador) REFERENCES Jogador(ID_Jogador),
    FOREIGN KEY (ID_Campeonato) REFERENCES Campeonato(ID_Campeonato)
);

5 - Inserção de Dados:
-- Insert data into Time table
INSERT INTO Time (ID_Time, Nome, Cidade, Rua, Numero, Bairro, CEP) VALUES
(1, 'Flamengo', 'Franca', 'Rua A', 101, 'Centro', '14400-000'),
(2, 'Corinthians', 'Franca', 'Rua B', 202, 'Centro', '14400-001'),
(3, 'Palmeiras', 'Franca', 'Rua C', 303, 'Centro', '14400-002'),
(4, 'São Paulo', 'Franca', 'Rua D', 404, 'Centro', '14400-003'),
(5, 'Santos', 'Franca', 'Rua E', 505, 'Centro', '14400-004'),
(6, 'Vasco da Gama', 'Franca', 'Rua F', 606, 'Centro', '14400-005'),
(7, 'Grêmio', 'Franca', 'Rua G', 707, 'Centro', '14400-006'),
(8, 'Internacional', 'Franca', 'Rua H', 808, 'Centro', '14400-007'),
(9, 'Cruzeiro', 'Franca', 'Rua I', 909, 'Centro', '14400-008'),
(10, 'Atlético Mineiro', 'Franca', 'Rua J', 1010, 'Centro', '14400-009'),
(11, 'Botafogo', 'Franca', 'Rua K', 1111, 'Centro', '14400-010'),
(12, 'Fluminense', 'Franca', 'Rua L', 1212, 'Centro', '14400-011'),
(13, 'Bahia', 'Franca', 'Rua M', 1313, 'Centro', '14400-012'),
(14, 'Sport Recife', 'Franca', 'Rua N', 1414, 'Centro', '14400-013'),
(15, 'Fortaleza', 'Franca', 'Rua O', 1515, 'Centro', '14400-014'),
(16, 'Ceará', 'Franca', 'Rua P', 1616, 'Centro', '14400-015'),
(17, 'Athletico Paranaense', 'Franca', 'Rua Q', 1717, 'Centro', '14400-016'),
(18, 'Coritiba', 'Franca', 'Rua R', 1818, 'Centro', '14400-017'),
(19, 'Goiás', 'Franca', 'Rua S', 1919, 'Centro', '14400-018'),
(20, 'Vitória', 'Franca', 'Rua T', 2020, 'Centro', '14400-019');

-- Insert data into Jogador table
INSERT INTO Jogador (ID_Jogador, Nome, Posição, ID_Time) VALUES
(1, 'Hugo',  'Atacante', 1),
(2, 'Tulio','Meio-Campo', 2),
(3, 'Arthur','Zagueiro', 3),
(4, 'João','Goleiro', 4),
(5, 'Pedro','Atacante', 5),
(6, 'Messi','Meio-Campo', 6),
(7, 'Ney','Zagueiro', 7),
(8, 'Cristiano','Goleiro', 8),
(9, 'Enzo','Atacante', 9),
(10, 'Vitor','Meio-Campo', 10),
(11, 'Luan', 'Zagueiro', 11),
(12, 'Jhon','Goleiro', 12),
(13, 'Pelé','Atacante', 13),
(14, 'Edu','Meio-Campo', 14),
(15, 'Cadu','Zagueiro', 15),
(16, 'Wesley','Goleiro', 16),
(17, 'Douglas','Atacante', 17),
(18, 'Edmundo','Meio-Campo', 18),
(19, 'José','Zagueiro', 19),
(20, 'Emerson','Goleiro', 20);

-- Insert data into Partida table
INSERT INTO Partida (ID_Partida, Data, Hora, Local, ID_Time1, ID_Time2, Resultado_Time1, Resultado_Time2, Melhor_Jogador) VALUES
(1, '2023-01-01', '10:00', 'Estádio A', 1, 2, 2, 1, 1),
(2, '2023-01-02', '11:00', 'Estádio B', 3, 4, 1, 3, 4),
(3, '2023-01-03', '12:00', 'Estádio C', 5, 6, 0, 0, 5),
(4, '2023-01-04', '13:00', 'Estádio D', 7, 8, 2, 2, 8),
(5, '2023-01-05', '14:00', 'Estádio E', 9, 10, 1, 2, 9),
(6, '2023-01-06', '15:00', 'Estádio F', 11, 12, 3, 1, 12),
(7, '2023-01-07', '16:00', 'Estádio G', 13, 14, 1, 1, 13),
(8, '2023-01-08', '17:00', 'Estádio H', 15, 16, 2, 3, 16),
(9, '2023-01-09', '18:00', 'Estádio I', 17, 18, 0, 2, 18),
(10, '2023-01-10', '19:00', 'Estádio J', 19, 20, 4, 1, 20),
(11, '2023-01-11', '10:00', 'Estádio A', 1, 3, 2, 2, 1),
(12, '2023-01-12', '11:00', 'Estádio B', 2, 4, 0, 3, 2),
(13, '2023-01-13', '12:00', 'Estádio C', 5, 7, 1, 1, 7),
(14, '2023-01-14', '13:00', 'Estádio D', 6, 8, 2, 0, 6),
(15, '2023-01-15', '14:00', 'Estádio E', 9, 11, 1, 3, 11),
(16, '2023-01-16', '15:00', 'Estádio F', 10, 12, 4, 2, 12),
(17, '2023-01-17', '16:00', 'Estádio G', 13, 15, 1, 0, 15),
(18, '2023-01-18', '17:00', 'Estádio H', 14, 16, 2, 3, 16),
(19, '2023-01-19', '18:00', 'Estádio I', 17, 19, 1, 2, 19),
(20, '2023-01-20', '19:00', 'Estádio J', 18, 20, 0, 1, 20);

-- Insert data into Campeonato table
INSERT INTO Campeonato (ID_Campeonato, Nome, Ano, Data_Inicio, Data_Fim) VALUES
(1, 'Campeonato A', 2023, '2023-01-01', '2023-06-30'),
(2, 'Campeonato B', 2023, '2023-02-01', '2023-07-30'),
(3, 'Campeonato C', 2023, '2023-03-01', '2023-08-30'),
(4, 'Campeonato D', 2023, '2023-04-01', '2023-09-30'),
(5, 'Campeonato E', 2023, '2023-05-01', '2023-10-30'),
(6, 'Campeonato F', 2023, '2023-06-01', '2023-11-30'),
(7, 'Campeonato G', 2023, '2023-07-01', '2023-12-30'),
(8, 'Campeonato H', 2023, '2023-08-01', '2024-01-30'),
(9, 'Campeonato I', 2023, '2023-09-01', '2024-02-28'),
(10, 'Campeonato J', 2023, '2023-10-01', '2024-03-31'),
(11, 'Campeonato K', 2023, '2023-11-01', '2024-04-30'),
(12, 'Campeonato L', 2023, '2023-12-01', '2024-05-31'),
(13, 'Campeonato M', 2023, '2024-01-01', '2024-06-30'),
(14, 'Campeonato N', 2023, '2024-02-01', '2024-07-31'),
(15, 'Campeonato O', 2023, '2024-03-01', '2024-08-31'),
(16, 'Campeonato P', 2023, '2024-04-01', '2024-09-30'),
(17, 'Campeonato Q', 2023, '2024-05-01', '2024-10-31'),
(18, 'Campeonato R', 2023, '2024-06-01', '2024-11-30'),
(19, 'Campeonato S', 2023, '2024-07-01', '2024-12-31'),
(20, 'Campeonato T', 2023, '2024-08-01', '2025-01-31');

-- Insert data into Inscrição table
INSERT INTO Inscrição (ID_Inscricao, ID_Campeonato, ID_Time) VALUES
(1, 1, 1),
(2, 1, 2),
(3, 1, 3),
(4, 1, 4),
(5, 1, 5),
(6, 2, 6),
(7, 2, 7),
(8, 2, 8),
(9, 2, 9),
(10, 2, 10),
(11, 3, 11),
(12, 3, 12),
(13, 3, 13),
(14, 3, 14),
(15, 3, 15),
(16, 4, 16),
(17, 4, 17),
(18, 4, 18),
(19, 4, 19),
(20, 4, 20);

-- Insert data into Troféu table
INSERT INTO Trofeu (id_trofeu, nome ) VALUES
(1, 'Artilharia'),
(2, 'Melhor Jogador'),
(3, 'Melhor Goleiro'),
(4, 'Artilharia'),
(5, 'Melhor Jogador'),
(6, 'Melhor Goleiro'),
(7, 'Artilharia'),
(8, 'Melhor Jogador'),
(9, 'Melhor Goleiro'),
(10, 'Artilharia'),
(11, 'Melhor Jogador'),
(12, 'Melhor Goleiro'),
(13, 'Artilharia'),
(14, 'Melhor Jogador'),
(15, 'Melhor Goleiro'),
(16, 'Artilharia'),
(17, 'Melhor Jogador'),
(18, 'Melhor Goleiro'),
(19, 'Artilharia'),
(20, 'Melhor Jogador');
INSERT INTO Premiacao (ID_Premiacao, ID_Trofeu, ID_Jogador, Ano, ID_Campeonato) VALUES
(1, 1, 1, 2023, 1),
(2, 2, 2, 2023, 2),
(3, 3, 3, 2023, 3),
(4, 4, 4, 2023, 4),
(5, 5, 5, 2023, 5),
(6, 6, 6, 2023, 6),
(7, 7, 7, 2023, 7),
(8, 8, 8, 2023, 8),
(9, 9, 9, 2023, 9),
(10, 10, 10, 2023, 10),
(11, 11, 11, 2023, 11),
(12, 12, 12, 2023, 12),
(13, 13, 13, 2023, 13),
(14, 14, 14, 2023, 14),
(15, 15, 15, 2023, 15),
(16, 16, 16, 2023, 16),
(17, 17, 17, 2023, 17),
(18, 18, 18, 2023, 18),
(19, 19, 19, 2023, 19),
(20, 20, 20, 2023, 20);

6 - CRUD e Relatórios.


Consulta: Listar todos os times e seus jogadores
![2342e98a-006a-4920-b0ca-ef5b418df524](https://github.com/hugo14253600/prova.sql/assets/162808170/9bf84016-8bc3-4995-be26-f9bc62d8132c)
![c9c37f57-dc47-4017-aa80-740040683f00](https://github.com/hugo14253600/prova.sql/assets/162808170/5bba3cd0-c693-4439-9d50-8310dc165fcd)

Consulta: Listar jogadores que ganharam troféu de Artilharia
![d5aead1b-017e-4577-b55d-5cce77c6396b](https://github.com/hugo14253600/prova.sql/assets/162808170/f8387419-5d8f-47cc-8799-f67d437a09d1)
![ae24fcdc-653e-42c8-9da4-fae48146a38e](https://github.com/hugo14253600/prova.sql/assets/162808170/32f3533c-6da6-4d07-93ab-248995a0d48c)

Consulta: Listar premiações de um campeonato específico
![c242fe1f-3649-4436-b9c2-031504e8fdda](https://github.com/hugo14253600/prova.sql/assets/162808170/b20270a5-d3a5-4dbd-abb9-826092c0b5dd)
![267255cc-f39d-4cf1-854a-075b5f9ad606](https://github.com/hugo14253600/prova.sql/assets/162808170/e3e9b73e-70ce-407b-be2f-9895851504b0)

Consulta: Listar troféus e suas descrições
![009f8d83-1775-4c60-9356-b44ca21ceeb8](https://github.com/hugo14253600/prova.sql/assets/162808170/e5f284dc-e76c-4ac9-bad0-fb4d8af1ef58)
![53ab5321-3d42-4185-8e1a-1b3c147f8ef3](https://github.com/hugo14253600/prova.sql/assets/162808170/94faf3e3-e71b-4949-bfac-260a5d257fc7)

Consulta: Listar partidas com resultado e melhor jogador
![e6025ec9-949c-4cc5-90c6-640ac0b412f5](https://github.com/hugo14253600/prova.sql/assets/162808170/db33aa46-82c3-4be6-90c3-ddf3eb18a03d)
![01e6033b-5f3b-4df2-8aad-3d35827db583](https://github.com/hugo14253600/prova.sql/assets/162808170/d2463dca-f73a-43f9-9274-266f0de22990)

Consulta: Listar jogadores e seus respectivos times
![4eb1a48e-4c72-40f8-b2f8-499b2a200695](https://github.com/hugo14253600/prova.sql/assets/162808170/e41e52c4-bb49-4489-bf71-80b56421db9c)
![1bf10766-d895-4e6e-8616-27be463c1e2f](https://github.com/hugo14253600/prova.sql/assets/162808170/c205f5ab-6a5f-40d4-a101-aec1a1339ee6)

Consulta: Listar campeonatos com número de inscrições
![5e28d5a3-17c3-4d73-a925-29d2416ef2db](https://github.com/hugo14253600/prova.sql/assets/162808170/6048bddc-c9ff-4291-ad73-2721c4ac97d1)
![3524b889-1b86-48fe-b70c-1a5d7a48487b](https://github.com/hugo14253600/prova.sql/assets/162808170/9cd192a6-13b7-41a1-a554-531ac3bcf174)

Consulta: Listar partidas com detalhes dos times
![620ec456-7209-4c70-be59-09c1eaf253ce](https://github.com/hugo14253600/prova.sql/assets/162808170/beb48b78-d687-4d3e-8dd0-924f955f735d)
![9f801302-1f81-47d6-bf7a-3714405271be](https://github.com/hugo14253600/prova.sql/assets/162808170/a8b2dccc-7145-4595-b24b-e23e8c0b133b)

Consulta: Listar jogadores de um time específico
![52866b7f-fdd7-4f98-9d99-b![ea5244f4-d9f6-466b-883e-0260d00ac4f7](https://github.com/hugo14253600/prova.sql/assets/162808170/875b721f-f171-4a32-a2fc-9b04f6dc9aba)
d0950e6b01f](https://github.com/hugo14253600/prova.sql/assets/162808170/b8803446-10b3-41af-a9b5-772bfa24d746)

Consulta: Listar todos os times
![ceb33363-3617-4b41-9765-67d5e32b4636](https://github.com/hugo14253600/prova.sql/assets/162808170/dd690079-76cc-47d2-91be-7430555be7c0)
![8fff6a2a-591e-4d38-8221-53ff3ee916fa](https://github.com/hugo14253600/prova.sql/assets/162808170/55276021-9a20-42bb-bce4-b8c06bed33f6)

















