# NTT DATA Bootcamp - Engenharia de Dados com Python, by Digital Innovation One

## Project Challenge - Azure and Power BI Integration

The challenge involved the creation of a SQL Database in Azure, population of the tables, then integration with Power BI, going through the transformation process of the data. The step-by-step of the process is detailed below, as was solicited in the challenge.

### Creation of an Azure based SQL Database

Following the steps of the challenge, the database was made and filled with data got from the instructor's GitHub Repo. As an addendum, some of the codes were broken and others required a bit of tinkering to work, specially the queries for adding the table elements. The integration with Power BI was done with no problems.

### Data transformation in Power Query

All of the headers in the source tables were verified and changed to more understandable names, the types were properly adapted as well, to ensure precise interpretation by Power BI. Null cells were minimal, the only instance of it happening was expected.

Some columns were too jumbled with information, so they were separated into individual values, that was done to the "Endereço" column, split into "Número", "Rua", "Cidade" and "Estado".

### Creating new tables by Merging

At this point, new tables needed to be created utilizing the data available, so that Power BI would have a better chance of understanding the elements and their relationships. **Why merge and not append?** To create these new tables, an column in common was needed between the source ones, Append can only glue them together with no relation required, while the functionality "merge" fuses tables only when there are identical columns present, using them as the relationship between these datasets. This is similar to using a SELECT query with JOIN, in SQL.

Nevertheless, the table **funcionarios_info_completa** was made merging **azure_company employee** with **azure_company department**, in that order, to avoid creating duplicates. This very table was made to show every employee in the organization, including all personal details, their managers and departments, the latter, in particular, was merged with its location, as requested in the challenge. The unwanted columns were removed and the headers were corrected.

Using the same method, the table **funcionarios_x_departamentos** was created merging the previous tables, but shaving every column except "Nome Completo", "ID Funcionário" and "Departamento". This table was made simply to show every employee without the overload of information from the previous table. The headers were also corrected.

The table **horas_trabalhadas_por_funcionario** was made using **azure_company employee**, **azure_company works_on** and **total_projetos**, the latter made by counting **azure_company works_on**, to show the total of hours worked by each employee. Same as everything else, unwanted columns were gone and headers corrected.

**dependentes_por_funcionarios** was created with **azure_company employee** merged with a counted **azure_company dependent**, to show the amount of dependents for employees, for those who have them. Same treatment process was done after.

For **gerentes_x_departamentos**, **azure_company employee** was merged with **azure_company project**, **azure_company works_on** and **azure_company departament** to achieve the desired merged department with their respective locations. This particular table showed the managers for each department. Same treatment after.

The last merged table was **colaboradores_por_gerentes**, made using a count of **funcionarios_info_completa** with **azure_company employee**, to know how many people are under each manager. The unwanted columns were removed and the headers were corrected, as usual.

### Conclusion

This challenge was pretty difficult, just not in the way I was expecting. I also did not make a Dashboard, there isn't enough data in this dataset to make any elaborated reports, few elements with low variable between them. Besides, the instructor said that a Dash using these methods were going to be tackled in a later module.