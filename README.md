create Database faculdade;
use faculdade;

create table tbl_curso (
id_curso int primary key auto_increment,
nome varchar(100),
duração varchar(150),
grau varchar(200)
);

create table tbl_aluno (
id_aluno int primary key auto_increment,
nome varchar(100),
matricula varchar (100),
cpf varchar(15),
data_nascimento date,
email varchar(100),
telefone varchar(100),
endereço text(1000)
);

create table tbl_professor (
id_professor int primary key auto_increment,
nome varchar(100),
cpf varchar(15),
especilidade varchar (300),
data_contratação date,
email varchar(50),
telefone varchar(45),
departamento varchar (100)
);

create table tbl_sala (
id_sala int primary key auto_increment,
laboratorio varchar(100),
sala_projetor varchar (100),
sala_informatica varchar (300)
);

CREATE TABLE tbl_disciplina (
    id_disciplina INT AUTO_INCREMENT PRIMARY KEY,
    id_curso_fk INT,
    nome VARCHAR(100),
    carga_horaria INT,
    FOREIGN KEY (id_curso_fk) REFERENCES tbl_curso(id_curso)
);

CREATE TABLE tbl_turma (
    id_turma INT AUTO_INCREMENT PRIMARY KEY,
    id_professor_fk INT,
    id_disciplina_fk INT,
    id_sala_fk INT,
    ano INT NOT NULL,
    semestre ENUM('1', '2'),
    foreign key (id_professor_fk) references tbl_sala(id_sala),
    FOREIGN KEY (id_professor_fk) REFERENCES tbl_professor(id_professor),
    FOREIGN KEY (id_disciplina_fk) REFERENCES tbl_disciplina(id_disciplina)
);

CREATE TABLE tbl_matricula (
    id_matricula INT AUTO_INCREMENT PRIMARY KEY,
    id_aluno_fk INT NOT NULL,
    id_turma_fk INT NOT NULL,
    nota DECIMAL(4, 2),
    frequencia DECIMAL(5, 2),
    FOREIGN KEY (id_aluno_fk) REFERENCES tbl_aluno (id_aluno),
    FOREIGN KEY (id_turma_fk) REFERENCES tbl_turma (id_turma)
);

