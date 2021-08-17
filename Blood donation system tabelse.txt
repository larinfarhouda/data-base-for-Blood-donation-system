create database project;
use database project;



//done
CREATE TABLE bloodBank (
  bloodBank_id int,
  bloodBank_name varchar(20),
  bloodBank_phone int,
  bloodBank_address varchar(50),
  stock_id int,
  PRIMARY KEY (bloodBank_id),
  FOREIGN  KEY (stock_id) REFERENCES stock(stock_id)
);

insert into bloodBANK values (12048,"Samarpan",342172,"A-Kale ka Taal Dehli Gate");
insert into bloodBANK values (41093,"Agra City",561290,"71-A.M.G. Road Subhash Park");
insert into bloodBANK values (44813,"Life Line Charitable",382179,"Gulab Rai Marg Delhi Gate");
insert into bloodBANK values (92018,"Jan Suvidha",450117,"Shaheed Marg Sanjay M Road");
insert into bloodBANK values (77314,"jeevan Rekha Charitable Blood",256594,"Gandhi Stadium Rd,Pilibhit");
select * from bloodBANK;

//done
CREATE TABLE receptionist (
  receptionist_id int,
  receptionist_name varchar(30),
  receptionist_shift varchar(30),
  hos_id int,
  PRIMARY KEY (receptionist_id),
 FOREIGN  KEY (hos_id) REFERENCES hospital(hos_id)
);

insert into receptionist values (27875,"Steve",1536,332019);
insert into receptionist values (54125,"John",2314,547219);
insert into receptionist values (25481,"Josh",3029,653871);
insert into receptionist values (13507,"Adam",4152,984568);
insert into receptionist values (99841,"Mark",5673,000985);
select * from receptionist; 


//done
CREATE TABLE hos_req (
  req_id int,
  hos_id int,
  FOREIGN  KEY (req_id) REFERENCES request(req_id),
  FOREIGN  KEY (hos_id) REFERENCES hospital(hos_id)
);

insert into hos_req values (12526,332019);
insert into hos_req values (31784,547219);
insert into hos_req values (26372,653871);
insert into hos_req values (09328,984568);
insert into hos_req values (24516,000985);
select * from hos_req;


//done
CREATE TABLE hospital (
  hos_id int,
  hos_name varchar(40),
  hos_postcode varchar(20),
  hos_website varchar(30),
  hos_city varchar(20),
  hos_phone int,
  PRIMARY KEY (hos_id),
  FOREIGN  KEY (hos_postcode) REFERENCES hos_PostCode(hos_postcode)
);

insert into hospital values (332019, 'Union hospital', BK7 849, 'UNIONHOSPITAL.com', 'istanbul')
insert into hospital values (332019, 'Union hospital', BK7 849, 'UNIONHOSPITAL.com', 'istanbul')

insert into hospital values (547219, 'fren Hospital', ZXA 434, 'FrenHos.co.tr', 'Ankara')

insert into hospital values (653871, 'randon Hospital', PZZ 555 , 'THATrandomHospital.com', 'izmir')

insert into hospital values (984568, 'Energy hospital',LO8 321 , 'ENGHOSPITAL.com', 'istanbul')

insert into hospital values (000985, 'Power hospital',LU6 555 , 'POWHOSPITAL.com', 'istanbul')
select * from hospital;


//done
CREATE TABLE hos_PostCode (
  hos_postcode varchar(20),
  hos_addres varchar (30),
  PRIMARY KEY (hos_postcode)
);
insert into hos_PostCode values ('LU6 555', 'south street, bakirkoy');
insert into hos_PostCode values ('BK7 849', 'key road, fatih');
insert into hos_PostCode values ('LO8 321', 'laptop hospital, aksaray');
insert into hos_PostCode values ('PZZ 555', 'random hospital, down street');
insert into hos_PostCode values ('ZXA 434', 'fren hospital, uppertown road');
select * from hos_PostCode;


//done
CREATE TABLE patient (
  patient_id int,
  patient_name varchar(20),
  patient_gender varchar(10),
  patient_age int,
  patient_bloodType varchar(10),
  hos_id int,
  nurse_id int,
  PRIMARY KEY (patient_id),
  FOREIGN  KEY (hos_id) REFERENCES hospital(hos_id),
  FOREIGN  KEY (nurse_id) REFERENCES nurse(nurse_id)
);


insert into patient values (10001,"Ryan","MALE,34,"A+",332019);
insert into patient values (10002,"Arthur","MALE",22,"B+",547219);
insert into patient values (10003,"Diana","FEMALE",26,"AB+",653871);
insert into patient values (10004,"Ramirez","FEMALE",20,"O+",984568);
insert into patient values (10005,"Majima","MALE",56,"AB-",000985);
select * from patient;


//done
CREATE TABLE stock (
  stock_id int,
  stock_amount int,
  bloodBag_group varchar(10),
  PRIMARY KEY (stock_id),
  FOREIGN  KEY (bloodBag_group) REFERENCES bloodDescription(bloodBag_group)
);

insert into stock values (354 , 6 , 'A+');
insert into stock values (355 , 3 , 'B+');
insert into stock values (356 , 7 , 'AB+');
select * from stock;
//done
CREATE TABLE donor (
  don_id int,
  don_name varchar(20),
  don_phone int,
  don_email varchar(225),
  PRIMARY KEY (don_id)
);

insert into donor values (123, 'wendy', 22935313, 'wendy@gmail.com');
insert into donor values (566, 'drake', 74392929, 'drake@gmail.com');
insert into donor values (333, 'ali',   55555044, 'ali@gmail.com');
insert into donor values (342, 'mohamed',44759428, 'MO@gmail.com');
insert into donor values (432, 'hafsa',6643824, 'hafsaaa@gmail.com');
insert into donor values (666, 'sofiane', 09097653, 'sofi@gmail.com');
select * from donor;

//done
CREATE TABLE nurse (
  nurse_id int,
  nurse_name varchar(20),
  nurse_shift varchar(30),
  hos_id int,
  PRIMARY KEY (nurse_id),
  FOREIGN  KEY (hos_id) REFERENCES hospital(hos_id)
);

insert into nurse values(34219,"Fatima",1,332019);
inseret into nurse values(71267,"Mokoto",3,547219);
insert into nurse values(35452,"Emma",5,653871);
inseret into nurse values(81873,"Sophia",6,984568);
insert into nurse values(13674,"Mia",9,000985);
select * from nurse;


//done
CREATE TABLE request (
  req_id int,
  req_date date,
  req_num int,
  lab_id int,
  PRIMARY KEY (req_id),
  FOREIGN  KEY (lab_id) REFERENCES lab(lab_id)
);

insert into request values(12526,"13/09/2015",3,100);
insert into request values(31784,"11/05/2015",2,2);
insert into request values(26372,"29/12/2015",5,10);
insert into request values(09328,"13/11/2015",4,2);
insert into request values(24516,"20/01/2015",1,43);
select * from request;

//done
CREATE TABLE bloodBags (
  bloodBag_id int,
  bloodBag_group varchar(10),
  bloodBag_Exp date,
  bloodBank_id int,
  lab_id int,
  PRIMARY KEY (bloodBag_id),
  FOREIGN  KEY (lab_id) REFERENCES lab(lab_id),
  FOREIGN  KEY (bloodBank_id) REFERENCES bloodBank(bloodBank_id),
  FOREIGN  KEY (bloodBag_group) REFERENCES bloodDescription(bloodBag_group)
);

insert into bloodbags values (5678,'A+','2019-09-11',12048,100);
insert into bloodbags values (5699,'AB+','2019-11-11',12048,2);
insert into bloodbags values (5654,'O+','2019-09-15',92018,43);
insert into bloodbags values (5675,'O+','2019-10-11',77314,100);
select * from bloodbags;

//done
CREATE TABLE lab (
  lab_id int ,
  lab_name varchar(20),
  lab_phone int ,
  lab_address varchar(30),
  PRIMARY KEY (lab_id)
);

insert into lab (lab_name, lab_phone, lab_address)values (100, 'south beach lab', 123432, '12 avenue, lu1');
insert into lab (lab_name, lab_phone, lab_address)values (2, 'north beach lab', 987654, 'coventry road, cv2');
insert into lab (lab_name, lab_phone, lab_address)values (43, 'east beach lab', 987654, 'endswood road, BR4');
select * from lab;

//done
CREATE TABLE bloodDescription (
  bloodBag_group varchar(10),
  bloodBag_description varchar(30),
  PRIMARY KEY (bloodBag_group)
);

insert into blooddescription values("A+",'doesnt give all');
insert into blooddescription values("B+",'doesnt give all');
insert into blooddescription values("O+",'gives all');
insert into blooddescription values("AB+",'doesnt give all');
select * from blooddescription;



//done
CREATE TABLE bloodBag_donor (
  bloodBag_id int,
  don_id int,
  FOREIGN  KEY (bloodBag_id) REFERENCES bloodBags(bloodBag_id),
  FOREIGN  KEY (don_id) REFERENCES donor(don_id)
); 
insert into bloodBag_donor values (5699,333);
insert into bloodBag_donor values(5654,666);
insert into bloodBag_donor values(5678,566);
insert into bloodBag_donor values(5675,123);
insert into bloodBag_donor values(5699,342);
select * from bloodBag_donor;
