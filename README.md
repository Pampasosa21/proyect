# [SQLQuery1.sql](https://github.com/user-attachments/files/34603599/SQLQuery1.sql)// 
Motor utilizado SQL Server Managemente Studio 22 //

CREATE DATABASE Ventas_Tech_DB

USE Ventas_Tech_DB

//** SECCION 1 - DROP TABLES **//

DROP TABLE IF EXISTS dbo.ventas;

DROP TABLE IF EXISTS dbo.productos;

DROP TABLE IF EXISTS dbo.clientes;

DROP TABLE IF EXISTS dbo.categorias;

//** SECCION DOS - CREATE TABLES **//

CREATE TABLE dbo.categorias(
	Categoria_id INT IDENTITY (1,1) NOT NULL PRIMARY KEY,
	Nombre_Categoria VARCHAR (50) NOT NULL,
	Descripcion VARCHAR (200)
	);
	
CREATE TABLE dbo.clientes(
	id_clientes INT IDENTITY (1,1) NOT NULL PRIMARY KEY,
	Nombre VARCHAR (100) NOT NULL,
	Email VARCHAR (100) UNIQUE,
	Ciudad VARCHAR (50),
	Fecha_Ingreso DATE NOT NULL
	);

CREATE TABLE dbo.productos(
	id_producto INT IDENTITY (1,1) PRIMARY KEY,
	Nombre_Producto VARCHAR(100) NOT NULL,
	id_categoria INT FOREIGN KEY REFERENCES dbo.categorias,
	Precio DECIMAL(10,2) NOT NULL,
	Stock INT DEFAULT 0,
	Activo BIT DEFAULT 1
	);

CREATE TABLE dbo.ventas(
	id_venta INT IDENTITY PRIMARY KEY,
	id_cliente INT FOREIGN KEY REFERENCES dbo.clientes,
	id_producto	INT FOREIGN KEY REFERENCES dbo.productos,
	Cantidad INT NOT NULL,
	Precio_Unitario DECIMAL(10,2) NOT NULL,
	Fecha_Venta DATE NOT NULL
	);

//** SECCION TRES - INSERT DATA **//

INSERT INTO ID_categorias (Nombre_Categoria, Descripcion) VALUES
	('Computacion', 'Laptops, PCs, monitores'),
	('Accesorios', 'Periferico', 'complementos'),
	('Audio', 'Auriculares', 'parlantes'),
	('Almacenamiento', 'Discos', 'memorias');

INSERT INTO clientes VALUES
	('Maria Lopez', 'maria@mail.com',  'Buenos Aires', '2024-01-05'),
	('Carlos Ruiz',  'carlos@mail.com', 'Córdoba',      '2024-01-10'),
	('Ana Gómez',    'ana@mail.com',    'Rosario',      '2024-02-01'),
	('Pedro Sanz',   'pedro@mail.com',  'Mendoza',      '2024-02-15'),
	('Laura Torres', 'laura@mail.com',  'Tucumán',      '2024-03-01');

INSERT INTO productos VALUES
	('Laptop Pro 15',    1, 1200.00, 15, 1),
	('Mouse Inalámbrico',  2,   28.00, 80, 1),
	('Monitor 4K 27',      1,  450.00, 12, 1),
	('Auriculares BT Pro', 3,  120.00, 35, 1),
	('SSD Externo 1TB',    4,  130.00, 18, 1),
	('Teclado Mecánico',   2,   95.00, 40, 1);

INSERT INTO ventas VALUES
	( 1, 1, 1, 2, 1200.00, '2024-03-05'),
	( 2, 2, 2, 5,   28.00, '2024-03-06'),
	( 3, 3, 3, 1,  450.00, '2024-03-07'),	
	( 4, 1, 4, 2,  120.00, '2024-03-08'),
	( 5, 4, 5, 3,  130.00, '2024-03-10'),
	( 6, 2, 6, 4,   95.00, '2024-03-11'),
	( 7, 5, 1, 1, 1200.00, '2024-03-12'),
	( 8, 3, 2, 8,   28.00, '2024-03-13'),
	( 9, 4, 4, 1,  120.00, '2024-03-14'),
	(10, 5, 3, 2,  450.00, '2024-03-15');

//** SECCION CUATRO - VALIDACION **//

SELECT * FROM dbo.categorias;

SELECT * FROM clientes;

SELECT * FROM productos;

SELECT * FROM ventas;
