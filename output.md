   ::-moz-selection { color: #FFFCF0; background: #0F0C00; } ::selection { color: #FFFCF0; background: #0F0C00; } body { font: normal 12px Verdana, sans-serif; color: #0F0C00; background: #FFFCF0; } .ebnf a { text-decoration: none; } .ebnf a:hover { color: #050400; text-decoration: underline; } .signature { color: #806600; font-size: 11px; text-align: right; } a:link, a:visited { color: #0F0C00; } a:link.signature, a:visited.signature { color: #806600; } div.ebnf { padding: 10px; background: #FFF6D1; width: 992px; } .ebnf div { padding-left: 13ch; text-indent: -13ch; } .ebnf code { font:12px SFMono-Regular,Consolas,Liberation Mono,Menlo,Courier,monospace; }@namespace "http://www.w3.org/2000/svg"; .line {fill: none; stroke: #332900; stroke-width: 1;} .bold-line {stroke: #141000; shape-rendering: crispEdges; stroke-width: 2;} .thin-line {stroke: #1F1800; shape-rendering: crispEdges} .filled {fill: #332900; stroke: none;} text.terminal {font-family: Verdana, Sans-serif; font-size: 12px; fill: #141000; font-weight: bold; } text.nonterminal {font-family: Verdana, Sans-serif; font-size: 12px; fill: #1A1400; font-weight: normal; } text.regexp {font-family: Verdana, Sans-serif; font-size: 12px; fill: #1F1800; font-weight: normal; } rect, circle, polygon {fill: #332900; stroke: #332900;} rect.terminal {fill: #FFDB4D; stroke: #332900; stroke-width: 1;} rect.nonterminal {fill: #FFEC9E; stroke: #332900; stroke-width: 1;} rect.text {fill: none; stroke: none;} polygon.regexp {fill: #FFF4C7; stroke: #332900; stroke-width: 1;} 

create\_table\_statement:

CREATE EXTERNAL TEMPORARY TABLE IF NOT EXISTS database_prefix table_name ( column_definitions index_definitions ) engine KEY DESCRIPTOR comment partition_desc distribution_desc rollup_index order_by properties broker_properties

`

[create_table_statement](#create_table_statement "create_table_statement")

         ::= 'CREATE' 'EXTERNAL'? 'TEMPORARY'? 'TABLE' 'IF NOT EXISTS'? [database_prefix](#database_prefix "database_prefix")? [table_name](#table_name "table_name") '(' [column_definitions](#column_definitions "column_definitions") [index_definitions](#index_definitions "index_definitions")? ')' [engine](#engine "engine")? 'KEY DESCRIPTOR'? [comment](#comment "comment")? [partition_desc](#partition_desc "partition_desc")? [distribution_desc](#distribution_desc "distribution_desc")? [rollup_index](#rollup_index "rollup_index")? [order_by](#order_by "order_by")? [properties](#properties "properties")? [broker_properties](#broker_properties "broker_properties")?

`

no references

  

database_prefix:

database .

`

[database_prefix](#database_prefix "database_prefix")

         ::= [database](#database "database") '.'

`

referenced by:

* [create\_table\_statement](#create_table_statement "create_table_statement")

  

database:

identifier

`

[database](#database "database") ::= [identifier](#identifier "identifier")

`

referenced by:

* [database_prefix](#database_prefix "database_prefix")

  

table_name:

identifier

`

[table_name](#table_name "table_name")

         ::= [identifier](#identifier "identifier")

`

referenced by:

* [create\_table\_statement](#create_table_statement "create_table_statement")

  

column_definitions:

column_definition ,

`

[column_definitions](#column_definitions "column_definitions")

         ::= [column_definition](#column_definition "column_definition") ( ',' [column_definition](#column_definition "column_definition") )*

`

referenced by:

* [create\_table\_statement](#create_table_statement "create_table_statement")

  

column_definition:

identifier data_type column_constraint

`

[column_definition](#column_definition "column_definition")

         ::= [identifier](#identifier "identifier") [data_type](#data_type "data_type") [column_constraint](#column_constraint "column_constraint")*

`

referenced by:

* [column_definitions](#column_definitions "column_definitions")

  

index_definitions:

, index_definition

`

[index_definitions](#index_definitions "index_definitions")

         ::= ( ',' [index_definition](#index_definition "index_definition") )+

`

referenced by:

* [create\_table\_statement](#create_table_statement "create_table_statement")

  

index_definition:

index_type ( column_list )

`

[index_definition](#index_definition "index_definition")

         ::= [index_type](#index_type "index_type") '(' [column_list](#column_list "column_list") ')'

`

referenced by:

* [index_definitions](#index_definitions "index_definitions")

  

engine:

ENGINE = olap mysql elasticsearch hive hudi iceberg jdbc

`

[engine](#engine "engine")   ::= 'ENGINE' '=' ( 'olap' | 'mysql' | 'elasticsearch' | 'hive' | 'hudi' | 'iceberg' | 'jdbc' )

`

referenced by:

* [create\_table\_statement](#create_table_statement "create_table_statement")

  

comment:

COMMENT string_literal

`

[comment](#comment "comment")  ::= 'COMMENT' [string_literal](#string_literal "string_literal")

`

referenced by:

* [create\_table\_statement](#create_table_statement "create_table_statement")

  

partition_desc:

PARTITION BY partition_type ( column_list )

`

[partition_desc](#partition_desc "partition_desc")

         ::= 'PARTITION BY' [partition_type](#partition_type "partition_type") '(' [column_list](#column_list "column_list") ')'

`

referenced by:

* [create\_table\_statement](#create_table_statement "create_table_statement")

  

distribution_desc:

DISTRIBUTED BY HASH ( column_list )

`

[distribution_desc](#distribution_desc "distribution_desc")

         ::= 'DISTRIBUTED BY HASH' '(' [column_list](#column_list "column_list") ')'

`

referenced by:

* [create\_table\_statement](#create_table_statement "create_table_statement")

  

rollup_index:

ROLLUP ( column_list )

`

[rollup_index](#rollup_index "rollup_index")

         ::= 'ROLLUP' '(' [column_list](#column_list "column_list") ')'

`

referenced by:

* [create\_table\_statement](#create_table_statement "create_table_statement")

  

order_by:

ORDER BY ( column_list )

`

[order_by](#order_by "order_by") ::= 'ORDER BY' '(' [column_list](#column_list "column_list") ')'

`

referenced by:

* [create\_table\_statement](#create_table_statement "create_table_statement")

  

properties:

PROPERTIES ( property_list )

`

[properties](#properties "properties")

         ::= 'PROPERTIES' '(' [property_list](#property_list "property_list") ')'

`

referenced by:

* [create\_table\_statement](#create_table_statement "create_table_statement")

  

broker_properties:

BROKER PROPERTIES ( property_list )

`

[broker_properties](#broker_properties "broker_properties")

         ::= 'BROKER PROPERTIES' '(' [property_list](#property_list "property_list") ')'

`

referenced by:

* [create\_table\_statement](#create_table_statement "create_table_statement")

  

property_list:

property ,

`

[property_list](#property_list "property_list")

         ::= [property](#property "property") ( ',' [property](#property "property") )*

`

referenced by:

* [broker_properties](#broker_properties "broker_properties")
* [properties](#properties "properties")

  

property:

string_literal = string_literal

`

[property](#property "property") ::= [string_literal](#string_literal "string_literal") '=' [string_literal](#string_literal "string_literal")

`

referenced by:

* [property_list](#property_list "property_list")

  

column_list:

identifier ,

`

[column_list](#column_list "column_list")

         ::= [identifier](#identifier "identifier") ( ',' [identifier](#identifier "identifier") )*

`

referenced by:

* [distribution_desc](#distribution_desc "distribution_desc")
* [index_definition](#index_definition "index_definition")
* [order_by](#order_by "order_by")
* [partition_desc](#partition_desc "partition_desc")
* [rollup_index](#rollup_index "rollup_index")

  

identifier:

\[a-z\] \[A-Z\] _ \[a-z\] \[A-Z\] \[0-9\] _

`

[identifier](#identifier "identifier")

         ::= [a-zA-Z_] [a-zA-Z0-9_]*

`

referenced by:

* [column_definition](#column_definition "column_definition")
* [column_list](#column_list "column_list")
* [database](#database "database")
* [table_name](#table_name "table_name")

  

string_literal:

" \[^"\] "

`

[string_literal](#string_literal "string_literal")

         ::= '"' [^"]* '"'

`

referenced by:

* [comment](#comment "comment")
* [property](#property "property")

  

data_type:

INT VARCHAR DATETIME DECIMAL BOOLEAN

`

[data_type](#data_type "data_type")

         ::= 'INT'

           | 'VARCHAR'

           | 'DATETIME'

           | 'DECIMAL'

           | 'BOOLEAN'

`

referenced by:

* [column_definition](#column_definition "column_definition")

  

column_constraint:

NOT NULL PRIMARY KEY UNIQUE

`

[column_constraint](#column_constraint "column_constraint")

         ::= 'NOT NULL'

           | 'PRIMARY KEY'

           | 'UNIQUE'

`

referenced by:

* [column_definition](#column_definition "column_definition")

  

index_type:

INDEX UNIQUE INDEX

`

[index_type](#index_type "index_type")

         ::= 'INDEX'

           | 'UNIQUE INDEX'

`

referenced by:

* [index_definition](#index_definition "index_definition")

  

partition_type:

RANGE LIST HASH

`

[partition_type](#partition_type "partition_type")

         ::= 'RANGE'

           | 'LIST'

           | 'HASH'

`

referenced by:

* [partition_desc](#partition_desc "partition_desc")

  

* * *

|     |     |     |
| --- | --- | --- |
|     | ... generated by [RR - Railroad Diagram Generator](https://www.bottlecaps.de/rr/ui) | [R R](https://www.bottlecaps.de/rr/ui) |