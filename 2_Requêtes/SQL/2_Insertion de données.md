# Insertion de données dans les tables - INSERT INTO

INSERT INTO Customers VALUES

   (5, 'John Doe', 'jdoe@email.com', '123 Main St'),
   
   (6, 'Jane Smith', 'jsmith@email.com', '456 Elm St'),
   
   (7, 'Alex Johnson', 'ajohnson@email.com', '789 Oak St'),
   
   (8, 'Mary Brown', 'mbrown@email.com', '987 Boar St');


select floor(dbms_random.value(1, 300)) from dual;

insert into t values (
    'pc portble',
    floor(dbms_random.value(1, 300))
);

select * from t order by stock_global;
