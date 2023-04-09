# Formatador de consultas SQL dinâmicas parametrizadas

Este é um projeto simples que tem como objetivo converter consultas SQL dinâmicas parametrizadas geradas por ORMs, como Dapper e Entity Framework, em consultas SQL mais legíveis.

Quando consultas dinâmicas parametrizadas são geradas por ORMs, elas podem aparecer no SQL Profiler como uma chamada para a procedure sp_executesql. 

Por exemplo, uma consulta gerada pelo Entity Framework pode aparecer da seguinte forma no SQL Profiler:

```sql
exec sp_executesql N'SELECT [Extent1].[Id] AS [Id], [Extent1].[Name] AS [Name] FROM [dbo].[Customers] AS [Extent1] WHERE [Extent1].[Id] = @p__linq__0',N'@p__linq__0 int',@p__linq__0=1

```


O objetivo é tornar a consulta mais legível, o que pode ser alcançado por meio da formatação da consulta para o seguinte formato:

```sql
DECLARE @p__linq__0 int;
SET @p__linq__0=1;

SELECT [Extent1].[Id] AS [Id], [Extent1].[Name] AS [Name] FROM [dbo].[Customers] AS [Extent1] WHERE [Extent1].[Id] = @p__linq__0
```

A codificação foi escrita em JavaScript puro, sem a utilização de frameworks, e pode ser facilmente modificado para atender às necessidades individuais.


## Referências
 - [mattwoberts/execsqlformat](https://github.com/mattwoberts/execsqlformat)
 - [PejmanNik/sqlops-spexecutesql-to-sql](https://github.com/igleite/sqlops-spexecutesql-to-sql)


## Licença

MIT
