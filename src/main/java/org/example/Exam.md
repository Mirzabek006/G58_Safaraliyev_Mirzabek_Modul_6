create table roles(
id serial primary key ,
role_name varchar  unique NOT NULL
);

create table users(
id  serial primary key ,
full_name varchar not null check ( length(full_name)>=5 ),
phone varchar not null  check ( length(phone)>=9 ) unique ,
role_id  int,
foreign key (role_id) references roles
on DELETE cascade
);

create table groups(
id serial primary key ,
grop_name varchar check ( length(grop_name)>=3 ),
mentor_id int,
foreign key (mentor_id) references users(id)
on DELETE cascade
);
create table students(
id serial primary key ,
active boolean not null default false,
createdAt date not null default now(),
foreign key (groups.id) references students(id)
on DELETE cascade ,
foreign key (user.id) references students(id)
on delete cascade
);
insert into roles(role_name) values ('STUDENT, MENTOR');
select*from roles;

insert into groups (grop_name, mentor_id) VALUES ('G59','Takhir Asadov'),
('P58','Ali Valiyev'),
('C59','Eshmat Toshmatov'),
('C58','Farruh Yoldoshev'),
('P59','John Johns'),
('D58','Cristian Ronoldo'),
('P59','Lioel Messi'),
('P58','Mirzabek Safaraliyev');
select *from groups;
insert into students(first_name,last_name,active,createdAt) values ('Safaraliyev','Mirzabek',name,true);
insert into students(first_name,last_name,active,createdAt) values ('Ali','Valiyev',name,true);
insert into students(first_name,last_name,active,createdAt) values ('Abbos ','Qoziboyev',name,false);
insert into students(first_name,last_name,active,createdAt) values ('Shohjahon','Ergashev',name,true);
insert into students(first_name,last_name,active,createdAt) values ('JOhn','ADMa',name,false);
insert into students(first_name,last_name,active,createdAt) values ('Sarsanul','Muzaffar',name,true);
insert into students(first_name,last_name,active,createdAt) values ('Aviram','Linkoln',name,true);
insert into students(first_name,last_name,active,createdAt) values ('Asadbek','Sayualliyev',name,true);
insert into students(first_name,last_name,active,createdAt) values ('Ergash','Joraboyev',name,false);
insert into students(first_name,last_name,active,createdAt) values ('Sadagul','Oyborchinov',name,true);
insert into students(first_name,last_name,active,createdAt) values ('Qozigul','Aliyeva',name,true);
insert into students(first_name,last_name,active,createdAt) values ('Laylo','Abilqosimova',name,true);
insert into students(first_name,last_name,active,createdAt) values ('Sabrina','Abdukaharova',name,false);
insert into students(first_name,last_name,active,createdAt) values ('Adam','Smid',name,true);
insert into students(first_name,last_name,active,createdAt) values ('Taysin','Mike',name,true);
insert into students(first_name,last_name,active,createdAt) values ('Safargul','Alijonva',name,false);
--create view standard;->Standard view
create table view(student_id,student_full_name,student_createdAt,groupName,mentor_FullName)
as select view.student_id,view.student_full_name,view.student_createdAt,view.groupName,view.mentor_FullName ;

create table   materialized_view as select * from students_id_seq;


create or replace function groupOfMentor(int )
language plpgsql $$


$$
language plpgsql;

create create event trigger  students  select * from students s1 ;



