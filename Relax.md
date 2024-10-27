


Considere la relación EMPLEADOS

| IDEmpleado | Nombre   | Apellido  | FechaIngreso | Salario | Cargo                    | IDDepartamento |
| ---------- | -------- | --------- | ------------ | ------- | ------------------------ | -------------- |
| 1          | Juan     | Pérez     | 2022-01-15   | 3000    | Gerente                  | 1              |
| 2          | María    | González  | 2021-06-10   | 2000    | Contadora                | 2              |
| 3          | Carlos   | Martínez  | 2020-09-01   | 1500    | Vendedor                 | 6              |
| 4          | Ana      | Rodríguez | 2021-12-05   | 1500    | Vendedora                | 6              |
| 5          | Luis     | López     | 2018-04-20   | 2500    | Analista de Sistemas     | 3              |
| 6          | Gabriela | Hernández | 2019-08-30   | 2200    | Recursos Humanos         | 5              |
| 7          | Fernando | García    | 2023-03-10   | 1800    | Soporte Técnico          | 3              |
| 8          | Elena    | Ramírez   | 2022-07-16   | 2100    | Diseñadora Gráfica       | 4              |
| 9          | Miguel   | Torres    | 2021-05-25   | 1900    | Analista de Datos        | 2              |
| 10         | Patricia | Vázquez   | 2020-11-12   | 1700    | Asistente Administrativa | 1              |
| 11         | Ricardo  | Ruiz      | 2018-02-09   | 2800    | Jefe de Ventas           | 6              |
| 12         | Sofía    | Moreno    | 2023-01-20   | 1600    | Community Manager        | 4              |



### Creación del esquema en Relax
group: bank example
				description[[ the data for this dataset was generated using {'<'}http://www.generatedata.com/>

				* the relation _Customers_ contains basic information about the customers of the bank.
				* the relation _Accounts_ contains the basic information of a single account. Note that a customer can
				have any number of accounts.
				* the relation _PremiumCustomers_ contains the customer-ids of all customers with a total balance over
				1000
				]]

				Customers = { cid firstname lastname
				1 Dexter Simpson
				2 Kaseem Gallagher
				3 Kuame Hamilton
				4 Robert Thompson
				5 Rhiannon Valentine
				6 Calvin Mays
				}

				Accounts = {
				aid, cid, balance:number
				1, 1, 66
				2, 1, -304
				3, 2, 272
				4, 3, 3472
				5, 4, 975.7
				6, 4, 93
				7, 5, 534
				8, 5, -75.5
				}




