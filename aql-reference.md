---

copyright:
  years: 2015, 2019
lastupdated: "2019-10-29"

subcollection: watson-knowledge-studio

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:note: .note}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Annotation Query Language reference 
{: #annotation-query-language-reference}

Annotation Query Language (AQL) is the primary language used to create {{site.data.keyword.knowledgestudiofull}} advanced rules extractors.

-   **Data model**  
The data model for AQL is similar to the standard relational model that is used by a SQL database such as DB2®. All data in AQL is stored in tuples, data records of one or more columns, or fields. A collection of tuples forms a view. All tuples in a view must have the same schema, that is the names and types of the fields across all tuples.
-   **Execution model**  
The runtime component has a document-at-a-time execution model. The runtime component receives a collection of documents and runs the extractor on each document to extract information from that document.
-   **AQL statements**  
By using AQL statements, you can create and then use modules, views, tables, dictionaries, and functions.
-   **Built-in functions**  
AQL has a collection of built-in functions for use in extraction rules.
-   **The create function statement**  
To perform operations on extracted values that are not supported by AQL, you can define custom functions to use in extraction rules called user-defined functions \(UDFs\).


## Annotation Query Language \(AQL\) syntax

Like many programming languages, AQL is based on common syntax and grammar.

The lexical structure of a programming language is the set of elementary rules that define the tokens or basic components of that language such as its reserved words, identifiers, constants, and more.

The syntax of AQL is similar to that of SQL, but there are several important differences:

-   AQL is case-sensitive.
-   AQL currently does not support advanced SQL features such as correlated subqueries and recursive queries.
-   AQL has a new statement type, `extract`, which is not present in SQL.
-   AQL does not allow keywords \(reserved words\) as view, column, or function names.
-   AQL allows, but does not require, regular expressions to be expressed in Perl syntax. Regular expressions begin with a slash \(`/`\) and end with a slash \(`/`\), as in Perl syntax. AQL also allows regular expressions that start with a single quotation mark \(`'`\) and end with a single quotation mark \(`'`\). For example, you can use `/regex/` instead of `'regex'` as the regular expression in AQL.

-   **Identifiers**  
Identifiers are used to define the names of AQL objects, including names of modules, views, tables, dictionaries, functions, attributes, and function parameters.
-   **Reserved words**  
Reserved words are words that have a fixed meaning within the context of the AQL structure, and cannot be redefined. Keywords are reserved words that have special meanings within the language syntax.
-   **Constants**  
Constants are fixed values that can be one of these data types: String, Integer, Float, or Boolean.
-   **Comments**  
Use comments to augment AQL code with basic descriptions to help others understand the code and to generate self-describing compiled modules.
-   **Expressions**  
An AQL expression is a combination of one or more scalar values and functions that evaluates to a single scalar value.

## Identifiers

Identifiers are used to define the names of AQL objects, including names of modules, views, tables, dictionaries, functions, attributes, and function parameters.

AQL identifiers are case-sensitive. There are two types of identifiers:

-   **Simple identifier**

    A simple identifier must start with a lowercase \(`a-z`\) or uppercase \(`A-Z`\) letter or the underscore character \(`_`\). Subsequent characters can be lowercase or uppercase letters, the underscore character, or digits \(`0-9`\). A simple identifier must be different from any AQL key word.

-   **Double-quoted identifier**

    A double-quoted identifier starts and ends with a double quotation mark character \(`"`\). You can use any character between the beginning and ending double quotation mark characters. Double-quoted identifiers cannot contain a period \(`.`\) character. If a double quotation mark character occurs within name, it must be escaped by prefixing it with the backslash character \(\\\), for example `\”`.

## Reserved words

Reserved words are words that have a fixed meaning within the context of the AQL structure, and cannot be redefined. Keywords are reserved words that have special meanings within the language syntax.

The following AQL-reserved keywords cannot be used as identifiers because each has a well-defined purpose within the language:

-   `all`
-   `allow`
-   `allow_empty`
-   `always`
-   `and`
-   `annotate`
-   `as`
-   `ascending`
-   `ascii`
-   `attribute`
-   `between`
-   `blocks`
-   `both`
-   `by`
-   `called`
-   `case`
-   `cast`
-   `ccsid`
-   `character`
-   `characters`
-   `columns`
-   `consolidate`
-   `content\_type`
-   `count`
-   `create`
-   `default`
-   `descending`
-   `detag`
-   `detect`
-   `deterministic`
-   `dictionary`
-   `dictionaries`
-   `document`
-   `element`
-   `else`
-   `empty\_fileset`
-   `entries`
-   `exact`
-   `export`
-   `external`
-   `external_name`
-   `extract`
-   `fetch`
-   `file`
-   `first`
-   `flags`
-   `folding`
-   `from`
-   `function`
-   `group`
-   `having`
-   `import`
-   `in`
-   `include`
-   `infinity`
-   `inline_match`
-   `input`
-   `into`
-   `insensitive`
-   `java`
-   `language`
-   `left`
-   `lemma_match`
-   `like`
-   `limit`
-   `mapping`
-   `matching_regex`
-   `minus`
-   `module`
-   `name`
-   `never`
-   `not`
-   `null`
-   `on`
-   `only`
-   `order`
-   `output`
-   `part_of_speech`
-   `parts_of_speech`
-   `parameter`
-   `pattern`
-   `point`
-   `points`
-   `priority`
-   `regex`
-   `regexes`
-   `retain`
-   `required`
-   `return`
-   `right`
-   `rows`
-   `select`
-   `separation`
-   `set`
-   `specific`
-   `split`
-   `table`
-   `tagger`
-   `then`
-   `token`
-   `Token`
-   `tokens`
-   `unicode`
-   `union`
-   `up`
-   `using`
-   `values`
-   `view`
-   `views`
-   `when`
-   `where`
-   `with`

The following reserved words are the names of built-in scalar types:

-   `Text`
-   `Span`
-   `Integer`
-   `Float`
-   `String`
-   `Boolean`
-   `ScalarList`

The following other reserved names cannot be used as identifiers:

-   `Dictionary`
-   `Regex`
-   `Consolidate`
-   `Block`
-   `BlockTok`
-   `Sentence`
-   `Tokenize`
-   `RegexTok`
-   `PosTag`



## Constants

Constants are fixed values that can be one of these data types: `String`, `Integer`, `Float`, or `Boolean`.

Constants are used in the select list of a `select` or `extract` clause, or as arguments in built-in or UDF functions and predicates. AQL supports the following types of constants:

-   **String constant**

    A string that is enclosed in single quotation marks \(‘\), for example ‘a string’.

-   **Integer constant**

    A 32-bit signed integer value that is not enclosed in quotation marks, for example 10 or -1.

-   **Float constant**

    A single-precision 32-bit floating point value, not enclosed in quotation marks, for example 3.14 or -1.2.

-   **Boolean constant**

    The value true or false not enclosed in quotation marks.

-   **Null constant**

    The value null that is not enclosed in quotation marks.



## Comments

Use comments to augment AQL code with basic descriptions to help others understand the code and to generate self-describing compiled modules.

Comments allow AQL developers to augment AQL code with basic descriptions, for ease of understanding of AQL source code, and they generate self-describing compiled AQL modules. There are three kinds of comments in AQL:

-   **Single-line comments**

    Single-line comments begin with double hyphens \(`--`\).

-   **Mulitple-line comments**

    Multiple-line comments begin with a slash and an asterisk \(`/*`\) and end with an asterisk and a slash \(`*/\). Multiple-line comments cannot be nested. For example, the following nested mulitple-line comment is not allowed:

    ```
    /*
    A comment with a /*nested comment*/
    */
    ```

-   **AQL Doc comments**

    AQL Doc comments provide a way to describe a module or an AQL object in plain language, and in an aspect-rich manner for contextual comprehension by other users. Unlike single-line comments and multiple line comments, which are ignored by the AQL Compiler, AQL Doc comments are serialized in the metadata of compiled modules \(.tam files\) and available for external consumption.

    All comments in AQL Doc for statements and modules have the following format:

    -   The comment is in plain text \(no HTML tags are supported\).
    -   The comment begins with a forward slash followed by two asterisks \(`/**`\) and ends with an asterisk forward slash \(`*/`\). Optionally, each line can start with an asterisk \(`*`\).
    -   Any number of white spaces can be used before the asterisk.
    -   Special tags that are prefixed by an at symbol \(`@`\) can be used at the beginning of each line or after the optional asterisk.
    -   AQL Doc comments cannot be nested.
    There are two levels of granularity within the AQL Doc system. The format for documenting each artifact is explained in detail in the topic that describes its statement and syntax.

    -   **Module-level comments**

        Module level comments are contained inside a special file named module.info that is located directly under the module folder. The comments are expected to describe the semantics of the module, and the schema of the view `Document` of the module.

    -   **Statement-level comments**

        Statement level comments are contained in the source AQL file, immediately preceding the statement that creates an AQL object. Single-line comments and multiple-line comments are allowed between the AQL Doc comment of a statement and the statement itself.

        The following top-level AQL statements can be documented by using AQL Doc comments:

        -   The **create external view** statement
        -   The **create external table** statement
        -   The **create external dictionary** statement
        -   The **create** function
        -   The **detag** statement
        -   The **select... into** statement
    AQL Doc comments are serialized inside the compiled representation of a module.


## Expressions

An AQL expression is a combination of one or more scalar values and functions that evaluates to a single scalar value.

Expressions can be one of four types:

-   a constant
-   a column reference
-   a scalar function call
-   an aggregate function call

### Constant

An expression can be a constant of type `Integer`, `Float`, or `String`, as in the following example:

```
select 'positive' as polarity 
```

The expression is the string constant `positive`. 

### Column reference

An expression can be a column reference, as in the following example:

```
create view Person as 
select F.name as firstname, L.name as lastname 
from FirstName F, LastName L
where FollowsTok(F.name, L.name, 0, 0);

```

This view identifies text that can be interpreted as a person’s full name \(for example, “Samuel Davis”, “Vicky Rosenberg”\). The expressions `F.name` and `L.name` are column-reference expressions that return the name column of the views `F` and `L`, respectively. The `from` statement defines views `F` and `L` as the local names for the views `FirstName` and `LastName` \(which define valid first and last names, and are not shown in this example\).

### Scalar function call

An expression can be composed of one or more scalar function calls, each of which may contain arguments that are also expressions of type constant, column reference, or scalar function call. A scalar function call can be one of the built-in scalar functions, or a scalar user-defined function. Consider the following example:

```
create view FamilyMembers as 
    select ToLowerCase(GetText(P.lastname)) as lastname, List( (GetText(P.firstname))) as firstnames 
    from Person P
    group by GetText(P.lastname); 

```

This view identifies potential family members by grouping people with the same last names together, printing all of the names, with the last names in lowercase characters \(for example, lastname keaton, firstnames \(Elyse, Alex, Diane\)\). The output of the `GetText` function calls are used as arguments to the `ToLowerCase` function call to display the names in lowercase. The `scalar` function call expressions in this example are: `ToLowerCase`, `(GetText(P.lastname)`, `ToLowerCase(GetText(P.firstname))`, and `GetText(P.lastname)`.

### Aggregate function call

An expression can be an aggregate function call. This expression type can have as arguments another expression of type column reference or type scalar function call. The following is an example of an aggregate function call with expression type column reference:

```
create view CountLastNames as
select Count(Person.lastname)
from Person;
```

The expression is simply `Count(Person.lastname)`. This expression will count the number of `Person.lastname` annotations in the document. An example of an aggregate function call with expression type scalar function call was seen in the previous example as `List(GetText(P.firstname))` with the `List` aggregate function taking a `GetText` scalar function as an argument to generate a list of first names. Aggregate function call expressions are only allowed as expressions in the `select` list of a `select` statement. Aggregate function call expressions are not allowed in the `select` list of an `extract` statement, or as arguments to a scalar or aggregate function call. 

## Data model

The data model for AQL is similar to the standard relational model that is used by a SQL database such as DB2®. All data in AQL is stored in tuples, data records of one or more columns, or fields. A collection of tuples forms a view. All tuples in a view must have the same schema, that is the names and types of the fields across all tuples.

The content of the input document is represented as a special view called Document.

The fields of a tuple must belong to one of the built-in data types of AQL:

-   **Boolean**

    A data type that has a true or false value.

-   **Float**

    A single-precision floating-point number.

-   **Integer**

    A 32-bit signed integer.

-   **ScalarList**

    A collection of values of the same scalar type \(Integer, Float, Text, or Span\). A value of data type ScalarList can be obtained as a result of the AQL built-in aggregate function `List\(\)`, or as the result of a UDF.

-   **Span**

    A Span is a contiguous region of a Text object, identified by its beginning and ending offsets in the Text object. Assume that your input text is:

    ```
    Amelia Earhart is a pilot.
    ```

    The text across Span \[0-6\] is `Amelia`.

    This Span can be visualized as:

    ```
    0A1m2e3l4i5a6
    ```

    Likewise, the text across Span \[20-25\] is `pilot`.

    **Note:** A Span of \[x-x\] represents the span between the end of a character and the beginning of the next character. In the previous example, \[0-0\] is an empty string before the character `A`. Likewise, a Span of \[3-3\] is an empty string between the characters `e` and `l`.

    A value of type Span can be obtained as a result of an `extract` statement, or a built-in scalar function, or a UDF.

-   **Text**

    The AQL data type to represent a character sequence. A text object contains a Unicode string, called its string value. In the case of a string formed as concatenation of disjoint substrings of another Text object, it also contains reference to the original Text object and relevant offset mapping information. Two Text objects are considered equal to each other if all their components are correspondingly equal to each other.


-   **Comparing values of type Span and Text**  
Prioritization factors affect comparisons between values of type Span and type Text.

## Comparing values of type Span and Text

Prioritization factors affect comparisons between values of type Span and type Text.

Values of type Span and type Text compare against each other in these ways:

-   A null span value is always sorted lower than other values.
-   A text value is always sorted higher than a span value.
-   Values of type Text are sorted first by the lexical order of their string values, then by their original Text orders and offset mapping information if applicable.
-   Values of type Span are sorted first by their underlying text objects, then by their begin offset, and then by their end offset. The span with a smaller begin offset is sorted lower. Between two spans that start on the same offset, the one with the smaller end offset sorts lower.



## Execution model

The runtime component has a document-at-a-time execution model. The runtime component receives a collection of documents and runs the extractor on each document to extract information from that document.

An extractor consists of one or more AQL modules to create a collection of views that each defines a relation. Some of these views are designated as output views, while others are non-output views. Non-output views can include some views that are imported into or exported from a module. It is important to note that output views and exported views are orthogonal. For example, a view that is exported does not qualify as a view that is output. In addition to these views, the unique `Document` view represents the input document that is annotated by this extractor.

### `Document` view

At the AQL module level, `Document` view is a special view that represents the current document that is being annotated by that module. When two or more modules are combined to form an extractor, the duplicate-free union of Document schemas of all modules is the required `Document` view. Use the `require document with columns` statement to specify the schema of the `Document` view. If this statement is absent from a module, the default schema that is assumed for the `Document` view is \(text Text, label Text\):

-   **text**

    The textual content of the current document.

-   **label**

    The label of the current document that is being annotated.


The keyword Document is reserved as an identifier for the `Document` view, which is automatically populated during execution. Therefore, you cannot define another view or table with the same name. However, you can use the word Document as an identifier for attribute names and aliases.


## AQL statements

By using AQL statements, you can create and then use modules, views, tables, dictionaries, and functions.

The following statements are supported in AQL:

-   **Statements for creating modules and declaring the interaction between them**

    The module statement

    The export statement

    The import statement

-   **Statements for creating AQL objects: views, dictionaries, tables, or functions**

    The create dictionary and create external dictionary statements

    The create table statement

    The create view statement

    The create external view statement

    The detag statement

    The extract statement

    The select statement

    The require document with columns statement

    The set default dictionary language statement

    The create function statement


**Note:** The syntax specifications in the AQL statements contain \[ \]. These specifications indicate that the square brackets, and the constructs that they hold, are optional when the corresponding syntax is used in writing a statement. In addition, they stand as place holders to define how to specify additional instances of a construct or argument.

## The `module` statement

Use the `module` statement to create a module that has self-contained required resources. You can export and import these resources as AQL objects to and from other modules.

### Syntax

```
module <module-name\>;
```

### Description

-   `<module-name\>`

    Declares that the current file is part of the module that is named `<module-name\>`. The module name must be a simple identifier. Double-quoted identifiers are not allowed as module names.

    Each AQL file inside the module must have exactly one module declaration, and this declaration must be the first statement in each file. This declaration establishes a namespace identical to the module-name. All views \(and other objects such as dictionaries, tables, and functions\) declared in AQL files inside this module are located inside this single namespace. They are accessible to all AQL files in this namespace.

    All of the files that are declared as part of the module `<module-name\>` must be inside a folder that is called `<module-name\>` to enforce this namespace. There is no ordering of the AQL files within this module folder. The AQL compiler examines all AQL files of the module and determines the right order to compile all views, dictionaries, tables, and functions declared in the module.


### Usage notes

-   When the underlying AQL file is not located as part of a module \(modular AQL\) and is compiled in compatibility mode, this statement is not supported.
-   Circular dependencies between views are not allowed.
-   AQL modules do not support submodules.
-   AQL files within subfolders of the top-level module folder are ignored.

### Examples

**Example 1: Sample module**

In the following example, the view TheMentions belongs to the module that is named sample.

```
module sample;

create dictionary GetTheDict as ('The', 'the');

create view TheMentions as
  extract dictionary 'GetTheDict' on D.text as theMention
  from Document D;
```


## The `export` statement

The `export` statement in AQL is used to export an AQL object from the current module so that it can be imported and used in other modules.

### Syntax

```
export view|dictionary|table|function <object-name\>;
```

### Description

-   `view\|dictionary\|table\|function`

    Defines the type of object to export. The object type can be a view, dictionary, table, or function.

-   `<object-name\>`

    Defines the name of the object to export. The `<object-name\>` can be a simple identifier or a double-quoted identifier.


### Usage notes

-   You cannot export any of the imported AQL objects. You can create the effect of re-exporting the view or table in the current module by creating a new view:

    ```
    select * from <imported_view_name_or_table_name>;
    ```

-   The `export view` and `output view` statements that are shown in the examples are orthogonal to each other. That is, an output view is not automatically an exported view, but it must be explicitly exported by using an `export` statement. An exported view is not automatically an output view, but it must be explicitly output by using the `output view` statement. In the examples, the `export` statement attempts to export the view PersonName.FirstName, which is an imported view. This attempt causes an error, which means that the developer must copy the imported view into a new view and then export that instead.

### Examples

**Example 1: Creating views and dictionaries and then exporting them for use in other modules**

This example creates the views FirstName and NotFirstName. The view FirstName collects information about the first names that are represented in the FirstNamesDictionary dictionary. The other view collects the names that remain when you exclude the first names. Two dictionaries are necessary to make the text extraction easier. One dictionary contains all of the first names that you want to search for. The second dictionary, LastNamesDictionary, contains the last names to search for. The FirstNamesDictionary dictionary is exported so that it can be used in other modules. The FirstName and the NotFirstName views are also exported so that they can be imported and used in other modules, such as module person in Example 2.

```
module personName;

create dictionary FirstNamesDictionary as
('Smith', 'John', 'Mary', 'Sam', 'George');

-- export dictionary statement

export dictionary FirstNamesDictionary;


create view FirstName as
  extract dictionary 'FirstNamesDictionary' 
  on D.text as firstName
from Document D;

-- export view statement

export view FirstName;

create dictionary LastNamesDictionary as
('Stewart', 'Johnson', 'Smith', 'Hopkins', 'George');

create view NotFirstName as
  select F.firstName as notFirstName from FirstName F
  where ContainsDict('LastNamesDictionary', F.firstName);

-- export view statement

export view NotFirstName;
```

**Example 2: Importing views to use, but exporting inappropriately, causing an error**

This example shows the importing of two views. These views were exported from module personName in Example 1. Module person can now import and reference those views. However, this module attempts to export the same view that it imported, FirstName, which causes an error.

```
module person;

-- Form 1

import view FirstName from module personName as PersonFirstName;

-- Form 2

import view NotFirstName from module personName;


-- ERROR
-- Reason: A view that is imported from one module 
-- cannot be exported in the current module.
export view personName.FirstName;


output view PersonFirstName;
```

The reason for the error in this code is that a view that is imported from one module cannot be exported in the current module. In addition, exported views are not automatically output views unless you defined an output view with the `output view` statement.


## The `import` statement

You can use the `import` statement to reference objects that are exported from other modules in the context of the current module.

### Syntax

```
import view|dictionary|table|function <object-name\> 
     from module <module-name\> [as <alias\>];
```

### Description

-   `view\|dictionary\|table\|function`

    Identifies the type of AQL object to be imported. The type of the object is mandatory.

-   `<object-name\>`

    The `<object-name\>` can be a simple identifier or a double-quoted identifier.

-   `<module-name\>`

    The `<module-name\>` must be a simple identifier.

-   `<alias\>`

    This form of the import statement, also known as `alias import`, imports the specified AQL object under the `<alias\>` name \(not the original name\) into the namespace of the current module. You can reference the imported element by using either an unqualified alias or an alias that is qualified with the current module name \(the module where the AQL object was imported\). You cannot use originalModule.elementName because the `alias import` statement imports the element under the alias name only and not under the qualified original name.


### Usage notes

-   An import statement without an alias specification imports the specified AQL object into the current module. It makes the AQL object accessible to AQL statements defined in the current module under its qualified name `<original\_module\_name\>.<object-name\>.`
-   The import statement is only used to import AQL objects from modules other than the current module. An object that is declared in an AQL file of the module is visible to any other AQL file in that same module. An import statement puts objects in the context of the current module, and not in the context of the current file. Therefore, a view that is imported by 1.aql inside module A is made visible to 2.aql inside the same module without the need for any additional import statements.

-   All import statements must follow immediately after the module declaration, and must precede all other types of statements. Only those AQL objects that are explicitly exported from any module can be imported in another module. If this requirement is not observed, a compilation error results.

-   A compilation error is introduced when an `import view` statement introduces a naming conflict with any `create view` statement or other import statements within the same module \(not just within the current file\). This restriction applies to the `import` of other objects in addition to views.
-   The AQL compiler adheres to the naming conventions that are used in previous versions of AQL:
    -   A module cannot contain a view and a table with the same name.
    -   A dictionary with the same name as a table or view is allowed.
    -   A function with the same name as a table, view, or dictionary is allowed.
-   A compilation error is introduced when different import statements within one or multiple AQL files in the module give the same name to different AQL objects.
-   A compilation error is introduced when an AQL file inside a module tries to reference another exported view of a module without using the `import view` statement. The same applies to dictionaries, tables, or functions.
-   When two AQL files inside a module import the same view X from another module under two different aliases, for example, A and B, then the two aliases are treated synonymously. This rule applies also to tables, dictionaries, and functions.

### Examples

**Example 1: Create views that you export to be imported into other modules.**

This example creates two views, `FirstName`, and `NotFirstName`. The view `FirstName` collects information about the first names that are represented in the `FirstNamesDictionary` dictionary. The second view collects the names that are left when you exclude the first names. Two dictionaries are necessary to make the text extraction easier. One dictionary contains all of the first names that you want to search for. The second dictionary, `LastNamesDictionary`, contains the last names to search for. The `FirstName` and the `NotFirstName` views are exported so that they can be imported and used in other modules, such as module `person` in Examples 2 and 3.

```
module personName;

create dictionary FirstNamesDictionary as
('Smith', 'John', 'Mary', 'Sam', 'George');

create view FirstName as
extract dictionary 'FirstNamesDictionary' 
on D.text as firstName
from Document D;

export view FirstName;

create dictionary LastNamesDictionary as
('Stewart', 'Johnson', 'Smith', 'Hopkins', 'George');

create view NotFirstName as
select F.firstName as notFirstName from FirstName F
where ContainsDict('LastNamesDictionary', F.firstName);

export view NotFirstName;
```

**Example 2: Importing the view FirstName by using alias import**

This example imports one of the views that were created and exported in Example 1. Then, the `PersonFirstName` view is output so that its results can be viewed.

The sample import statement is known as an alias import. It imports the view `FirstName`, with no module qualifier, to the namespace of the current module, `person`. The imported view can be accessed only through the alias name `PersonFirstName` and not through any other form. For example, you cannot refer to the imported view as `personName.FirstName` because it is imported only through the alias name.

```
module person;

`import view FirstName from module personName as PersonFirstName;`

output view PersonFirstName;
```

**Example 3: Importing the view NotFirstname without using alias import**

This sample import statement imports the qualified name personName.NotFirstName \(not the unqualified name of the view\) to the namespace of the current module, `person`. Always refer to the imported view by using only the qualified name. Any other mode of reference is flagged as compiler error.

```
module person;

`import view NotFirstName from module personName;`


output view personName.NotFirstName;
```


## The `import module` statement

You can use the `import module` statement to import and reuse existing AQL modules.

### Syntax

```
 import module <module-name\>;
```

### Description

-   `<module-name\>`

    Specifies the module to import. The `<module-name\>` must be a simple identifier.


### Usage notes

-   The import statement is only used to import AQL objects from other modules, not from the current module.

-   All import statements must follow immediately after the module declaration and must precede all other types of statements. Only those AQL objects that are explicitly exported from any module can be imported in another module. If this requirement is not observed, a compilation error results.

-   A compilation error is introduced when an `import view` statement introduces a naming conflict with any `create view` or other import statement within the same module \(not just within the current file\). This restriction applies to the `import` of other AQL objects in addition to views.
-   A compilation error is introduced when an AQL file inside a module tries to reference another exported view of a module without using the `import view` statement. The same applies to dictionaries, tables, or functions.
-   If two AQL files inside a module import the same view X from another module under two different aliases, for example, A and B, then the two aliases are treated synonymously. This rule applies also to tables, dictionaries, and functions.

### Examples

In this example, the `import` statement imports the qualified name of both the exported views, `personName.FirstName` and `personName.NotFirstName`. Any view that is not exported by the module `personName` is not imported as a part of the import statement

-   **Example 1: Import both FirstName and NotFirstName views**

    This example shows all of the exported views from module personName. The views `FirstName` and `NotFirstName` were created in the example section of the export statement.

    ```
    module personOther;
    
    -- The following statement would import both views FirstName and NotFirstName.
    import module personName;
    ```




## The `set default dictionary language` statement

The `set default dictionary language` statement allows an extractor developer to customize the default set of dictionary-matching languages for the containing module.

### Syntax

```
 set default dictionary language as '<language codes\>';
```

### Description

-   `<language codes\>`

    Specifies the language for compilation and matching for dictionaries of the module that are declared without an explicit `with language as` specification. The `<language codes\>` set must be a comma-separated list, with no white spaces around each language code. Failure to observe this requirement can result in a compilation error.

    This statement affects the following dictionaries:

    -   Dictionaries that are explicitly declared in the current module by using the `create dictionary` or `create external dictionary` statement, and that statement does not have a `with language as` clause.
    -   Dictionaries from external files.
    -   In a pattern specification of an `extract pattern` statement, atoms of type `'string'` and atoms of type `<'string' [match parameters]>` without an explicit `with language as` specification.
    When this statement is absent from inside a module, the runtime component defaults to a language set of German, Spanish, English, French, Italian, and the unspecified language x. It is defined as a set: `[de,es,en,fr,it,x_unspecified]`. Within a module, there can be only one instance of this statement.


### Usage notes

-   The `set default dictionary language` statement can be updated to improve the extent of languages that are covered by the extractor. This ability to add languages promotes ease of customization and the reuse of existing extractors.

### Examples

**Example 1: Specifying languages to be used to match dictionary entries**

```
module Dictionaries;

-- Set the default dictionary matching language 
--  for this module to English and French 

set default dictionary language as 'en,fr';


/**
* Dictionary of English and French names. Since there is no language 
* clause in dictionary definition, module level dictionary matching 
* setting will be applied.
*/

create dictionary EnglishFrenchNames
from file 'en_fr_names.dict';

/**
* Dictionary of Italian names. Language clause in the dictionary 
* definition will override the module level dictionary matching setting.
*/

create dictionary ItalianNames 
with language as 'it'
as
(
'firstEntry','secondEntry'
);
    
    
/**
* View to extract pattern: Phone, followed by one to three tokens, 
* followed by Email. Language clause at the atom level will override 
* the module level dictionary setting.
*/

create view PhoneEmailPattern as
extract pattern <'Phone'[ with language as 'en']> 
  <Token> {1,3} 'Email'  
as match 
from Document D;  

output view PhoneEmailPattern;
```


## The `require document with columns` statement

By using the `require document with columns` statement, you can define the schema of the special view `Document` at compile time. This schema definition specifies the list of required fields and their types to be found in each tuple of the view `Document`.

### Syntax

```
require document with columns  <columnName\> <columnType\>  
     [and <columnName\> <columnType\>]*;
```

### Description

-   `<columnName\>`

    Specifies the name of the column to be used in the schema. The `<columnName\>` is an attribute identifier, which is a simple identifier or a double-quoted identifier.



-   `<columnType\>`

    Specifies the type of column to be used in the schema of the `Document` view. The `<columnType\>` can be one of the following data types: Integer, Float, Boolean, or Text.

-   `[ and <columnName\> <columnType\> ]*`

    Specifies additional column names and types to the schema of the `Document` view. They follow the same rules as `<columnName\>` and `<columnType\>`.


In earlier versions of AQL, the schema of the special view `Document` was predefined to consist of either a single field \(text Text\) or two fields \(text text, label Text\). The choice between these schemas was decided at run time. By using the `require document with columns` statement, you can override the default input document schema at compile time.

### Usage notes

-   For modular AQL code, the scope of any `require document with columns` statement is the module in which it is defined.
-   Only one `require document with columns` statement is allowed per AQL file. Within a single module, or a generic module, there can be zero, one, or multiple AQL files that have a `require document with columns` statement. All AQL files within a module merge their `require document with columns` statements at the level of the entire module to form a module-wide `require document with columns`. This statement defines the schema of the `Document` view for that module. If none of the AQL files of a module or a generic module contain a require statement, the module has a default schema for the view `Document`. This schema consists of two columns: \(text Text, label Text\). No default columns are established for the special view `Document` if at least one AQL file in the module has one `require document with columns` statement.
-   When multiple modules are combined to form an extractor, the schema of the `Document` view of the entire extractor is defined by the duplicate-free union of Document schemas for each module. An exception is raised when any column found across the multiple `require document with columns` statements is found to be conflicting in its type requirements across modules. For example, a module requires a column X with type Y when another module that is being loaded with it requires a column X with type Z.
-   An exception is raised when you run an extractor if the provided input document tuple does not contain all of the required columns. An exception is also raised if a column does not conform to its corresponding required type.
-   When the `require document with columns` statement is present inside a module, every column of the special view `Document` that is referenced must be declared in at least one of the `require document with columns` statements. The statement can be found in different AQL files within the same module. However, all such `require document with columns` statements would be merged at the level of the module to form a module-wide `require document with columns` statement.

### Examples

**Example 1: Require document statement with similar column types**

The following example defines a document schema that contains four fields of the same type. This AQL sample expects each document tuple of the data collection to contain four columns as defined in the document schema.

Refer to JSON document formats for details on how to create a document that conforms to a schema.

```
module person;

-- Require document statement with similar field types

require document with columns
  inputDocumentText Text
  and inputDocumentLabel Text
  and documentAuthor Text
  and documentCreationDate Text;
```

**Example 2: Require document statement with varying column types**

The following sample defines a document schema that contains columns of varying field types.

```
module sample;

-- Require document statement with varying field types

require document with columns
  bookText Text
  and purchaseCount Integer
  and bookPrice Float
  and isBookPopular Boolean;
```

**Example 3: Merging document schemas**

  The example describes how to merge document schemas that use the files first.aql, last.aql, and socialsecurity.aql.

```
first.aql:
    module person;  
    require document with columns firstName Text;


last.aql: 
    module person;  
    require document with columns lastName Text;


socialsecurity.aql 
    module person;  
    require document with columns lastName Text 
        and socialSecurityNo Integer;
```

The merged schema is \(firstName Text, lastName Text, socialSecurityNo Integer\).


## The `create view` statement

The top-level components of an AQL extractor are its views. Views are logical statements that define, but do not necessarily compute, a set of tuples.

### Syntax

The `create view` statement can take one of three forms. The simplest form defines a logical view that is composed of the tuples of a single `select` or `extract` statement. The second is a a multijoin form that defines a view that comprises the tuples that arise from the multiset union of several`select` or `extract` statements. The third form defines a new view that contains the set difference between tuples from two `select` or `extract` statements.

```
create view <viewname\> as  <select or extract statement\>;
```

```
create view <viewname\> as  (<select or extract statement\>) union all (<select or extract statement\>)...;
```

```
create view <viewname\> as  (<select or extract statement\>) minus (<select or extract statement\>);
```

### Description

-   `<viewname\>`

    The `<viewname\>` can be a simple identifier or a double-quoted identifier. It cannot contain the period character.


-   `<select or extract statement\>`

    The `select` or `extract` statement creates output that is used to compute the tuples of the containing view.


### Usage notes

-   View names are case-sensitive. For example, Person, PERSON and person are different view names
-   Two views within the same AQL module cannot share a name, which would make them duplicates. However, two views with same name can exist in two different modules, since their fully qualified names are unique.
-   By default, a view that is defined by the `create view` statement is a non-output view until it is specified as an output view.
-   The `select` or `extract` statements of the `union all` and the `minus` forms, must have a compatible output schema. Two schemas are considered compatible for a `union` or `minus` operation if they have the same number of columns, the column names are in the same order, and they have compatible data types:
    -   Fields of the same data type are `union` or `minus` compatible.
    -   The Span and Text data types are `union` or `minus` compatible. In the case of a union between a Span and a Text type, the output type is a Span. However, objects of Text type are not automatically converted into a Span type – the automatic conversion happens only when required by function calls.
    -   Two `ScalarLists` are `union` or `minus` compatible regardless of the underlying scalar type.

### Examples

**Example 1: Creating a view with a select or extract statement**

In the example below, the view `Phone` uses an `extract` statement to prepare its tuples. The view `PhoneNumber` uses a `select` statement to pick specific fields from the view `Phone`.

```
create view Phone as extract 
  regexes /\+?\([1-9]\d{2}\)\d{3}-\d{4}/ 
  and /\+?[Xx]\.?\d{4,5}/
  on D.text as num
from Document D;

create view PhoneNumber as
select P.num as num, LeftContextTok(P.num, 3) as lc
from Phone P;
```

**Example 2: Creating a view with Union All statement**

The view `AllPhoneNums` prepares a unionized set out of the tuples of `Phone` and `Extension` views. The two views that are being unionized have the same schema.

```
create view Phone as 
extract 
    regex /\+?\([1-9]\d{2}\)\d{3}-\d{4}/
    on D.text as match
from Document D;

create view Extension as
  extract
    regex /\+?[Xx]\.?\d{4,5}/
    on D.text as match
from Document D;

create view AllPhoneNums as
  (select P.match from Phone P)
union all
  (select E.match from Extension E);
```

**Example 3: Creating a view with Minus statement**

The following example shows how you can use `minus` to filter out unwanted tuples from a set of tuples.

```
create view Organization as
  (select * from OrganizationCandidates)
minus
  (select * from InvalidOrganizations);
```

**Example 4: Schema compatibility for minus**

It is important to note that spans over different target text are not of the same type. Consider the following AQL example that explains this difference by using a String literal.

```
create view OneString as 
  select 'a string' as match 
  from Document D;

create view TheSameString as 
  select 'a string' as match 
  from Document D;

create view Subtraction as
  (select R.match from OneString R)
minus
  (select R.match from TheSameString R);
```

Instead of the expected output of an empty tuple list, the output is a set of records that have 'a string' as a field value.

Although the contents of the `OneString` and `TheSameString` views seem identical, the actual text values have different underlying AQL objects. The type of `OneString.match` is 'Span over OneString.match'. The type of `TheSameString.match` is 'Span over TheSameString.match'. Since the field types are different, they are not compatible for comparison purposes.

To obtain the wanted output of the empty tuple list, you must compare values of same type. In the following example, the GetString\(\) function converts span objects to string objects to pass compatible types to the `minus` operation.

```
create view Subtraction as
(select GetString(R.match) from OneString R)
minus
(select GetString(R.match) from TheSameString R);
```


### Documenting the `create view` statement with AQL Doc

The AQL Doc comment for a `create view` statement contains the following information:

-   General description about the view.
-   @field for every column name in the view.

**Example**

```
/**
* Extracts all spans that match a phone number pattern from 
* the input documents. It uses a regular expression to match 
* phone number patterns.
* @field num phone number
* @field lc 3 tokens to the left of phone number*/

create view PhoneNumber as
select P.num as num, LeftContextTok(P.num, 3) as lc
from
(
extract 
    regexes /\+?\([1-9]\d{2}\)\d{3}-\d{4}/ and /\+?[Xx]\.?\d{4,5}/
    on D.text as num
from Document D
) P;
```

## The `output view` statement

The `output view` statement defines a view to be an output view. The runtime component outputs only the tuples of views that are marked as output views. The AQL compiler compiles only views that are marked as output or export, or reachable from views that are marked as output or export.

### Syntax

```
output view <view-name\> [as '<alias\>'];
```

### Description

-   `<view-name\>`

    The name of the view that should be output, as known in the name space of the current module. The `<view-name\>` is a simple identifier or a double-quoted identifier. The built-in view `Document` cannot be output.

-   `[as '<alias\>']*`

    Defines an `<alias\>` name for the output view. When the optional alias is not specified, the view is output under the following names:

    -   In modular AQL, the view is output under the name `<module-name\>.<view-name\>` where `<module-name\>` is the name of the module where the view is originally defined \(which can be different from the module where the view is output\).
    -   In AQL 1.4 or earlier, the view is output under the name `<view-name\>`
    The `output ... as <alias\>` statement is useful when you customize an extractor for different domains. The use of the `<alias\>` name when you define an output view ensures that output names are identical across different implementations of the customization.

    The `<alias\>` name cannot be used in another `select` or `export` statement. You must enclose the `<alias\>` with single quotation marks, and the `<alias\>` name can contain periods.


### Usage notes

-   When an AQL extractor is run, it computes resultant tuples for each view that is defined as an output view. The tuples of any non-output view are also computed, but only when they are necessary to compute the resultant tuples of an output view.
-   In modular AQL, the `output view` statement outputs the tuples of the view under the fully qualified view name that is qualified by its module name. Consider the following example where the statement `output view Person;` results in the output of the `personModule.Person` view:

```
module personModule;

create view Person as
  extract dictionary 'FamousPeopleDict' on D.text as match 
  from Document D;

output view Person; 
```

This behavior applies for any view output without an alias, regardless of whether the view is output in the module where it has been defined, or a module where it has been imported, even when it has been imported using an alias import. For example, in the output view `MyPerson`, this example results in the view being output under its original qualified name `personModule.Person` and not under its local alias `MyPerson`.

```
module employeeModule;
  
import view Person from module personModule as MyPerson;

output view MyPerson;
```

-   The output alias statement is useful when you build libraries of extractors where the same type of entity can have many different implementations, depending on the application domain or the language of the input documents. The main benefit of using an alias when you define an output view is to ensure a consistent nomenclature across output views. Consistent nomenclature is expected by the program logic of a user when you process multiple modules that each output a semantically similar view. In modular AQL, when an alias name is used in an `output view` statement, the tuples of a view are output under the specified alias name. For example, the following code would output the results under the alias name PersonAlias, and the alias name is not qualified with the module prefix.

```
module personModule;

create view Person as
  extract dictionary 'FamousPeopleDict' on D.text as match 
  from Document D;

output view Person as 'PersonAlias';
```


### Examples

The following examples contain two modules, personModuleFrench and personModuleEnglish. Each module outputs a view, named PersonNameFrench and PersonNameEnglish. Suppose that there are similar modules, each of which outputs views that are semantic variants of an extractor for person names. These modules are customized for different languages with the variance in the customization of this view for a specified input language. Eventually, a user might want a program to use modules where the sought output view is name PersonName, irrespective of the modules that are processed. This expectation is normal, since each module that is customized for a language, domain, or another purpose is expected to produce various results. The consumer of these modules does not need to alter the algorithm of their program to accommodate for varying output view names when the underlying semantics are similar.

In the example, because the alias PersonName is used, the consumer does not need to alter the view name that is sought. However, the results might vary depending on the modules that are processed. In the example, for instance, the resulting matches are French-based \(Example 1\) and English-based \(Example 2\).

**Example 1: Resulting matches are French-based**

The following example defines a view `PersonNameFrench` and outputs it under an implementation-neutral alias name, `'PersonName'`.

```
module personModuleFrench;

create dictionary FrenchNames as
  ('Jean', 'Pierre', 'Voltaire', 'Francois', 'Marie', 'Juliette');

create view PersonNameFrench as
  extract dictionary 'FrenchNames' 
  on D.text as name
  from Document D;

output view PersonNameFrench as 'PersonName'; 
```

**Example 2: Resulting matches are English-based**

The following example defines a view `PersonNameEnglish` and outputs it under an implementation-neutral alias name, `'PersonName'`.

```
module personModuleEnglish;

create dictionary EnglishNames as
  ('John', 'Peter', 'Andrew', 'Francis', 'Mary', 'Juliet');

create view PersonNameEnglish as
  extract dictionary 'EnglishNames' 
  on D.text as name
  from Document D;

output view PersonNameEnglish as 'PersonName'; 
```


The consumer of the example modules can access the output tuples through the alias name `'PersonName'`. The consumer would not need to know the actual module from which the results are fetched.



## The `extract` statement

The `extract` statement is used to extract basic features directly from text.

### Syntax

```
extract <select list>,
  <extraction specification>
from <from list>
[having <having clause>]
[consolidate on <column> [using '<policy>']]
[limit <maximum number of output tuples for each document>];
```

### Description

-   `<select list\>`

    A comma-delimited list of output expressions. The result of these output expressions are returned as the output of the `extract` statement, along with the tuples that are generated by the evaluation of the extraction specification. The format for the `<select list\>` is the same as the `<select list\>` of a `select` statement.

-   `<extraction specification\>`

    Applies the extraction specification over all tuples from the views that are defined in the `<from list\>`. It renames the columns of tuples according to their corresponding aliases that are specified in the `extract` statement. You can use one of the following extraction specifications:

    -   Regular expressions
    -   Dictionaries
    -   Splits
    -   Blocks
    -   Part of speech
    -   Sequence patterns
-   `<from list\>`

    A comma-delimited list that is the source of the tuples from which features are to be selected. The format of the `<from list\>` is similar to the format of the `<from list\>` of the `select` statement. However, if the `extract` statement does not have a pattern specification, then the `<from list\>` can contain a single item.

-   `[having <having clause\>]`

    Specifies a filtering predicate \(in the `<having clause\>`\) that is applied to each extracted output tuple. Note that the field names that are specified in the `<having clause\>` refer to any aliases that are specified in the `<select list\>`. This clause is optional.

-   `[consolidate on <column\>[using '<policy\>' ]]`

    Defines how to handle overlapping spans as defined in the consolidation `<policy\>`. In this specification, `<column\>` must be the name of an output field, which is part of the `extract` statement. This clause is optional.

-   `[limit<maximum number of output tuples for each document\>]`

    Limits the number of output tuples from each document to the specified maximum. This clause is optional.


### Usage notes

The semantics of the `extract` statement are as follows:

-   Evaluate the extraction specification over each tuple of the input relation. For each result that the extraction produces, an output tuple that contains the extracted values, along with any columns of the original tuple that were specified in the `<select list\>`, is produced.
-   Rename the columns of the output tuple according to the aliases specified as part of the `<select list\>` and the `<extraction specification\>`.
-   Apply any predicates in the optional `having` clause to the resulting output tuple.
-   Consolidate tuples that pass the predicates according to the optional `consolidation` clause, and add the resulting tuples to the output.
-   If the optional `limit` clause is present, limit the output to the specified number of tuples for each document.

The semantics of the `from` clause of an `extract pattern` statement are different from other forms of `extract` statements that do not have a pattern specification. If at least one of the views in the `<from list\>` does not contain any tuples on a particular document, then the output of the `extract` statement is empty. This output is empty because the set of all combinations of tuples in the input views is empty.

In the special case of `extract pattern` statements, the `from` clause is a placeholder that declares the names of relations that are involved in the pattern specification. The semantics of the statement are driven only by the pattern specification. In particular, the output of the statement can be non-empty even when some of the input views are empty.

### Examples

**Example 1: Extracting phone numbers from a pre-defined view**

This sample extract statement evaluates a regular expression for United States phone numbers across input text that is represented by the pre-defined view `Document`. The output is then restricted to the first three phone numbers that are identified per each document. Field names in the having clause refer to the aliases at the beginning of the `extract` statement.

```
create view PhoneNumbers as
  extract 
    D.text as documentText,
    regex /\d{3}-\d{3}-\d{4}/ on D.text as phoneNumber 
from Document D
having MatchesRegex(/\d{3}.*/, phoneNumber)
limit 3;
```

**Example 2: Extracting blocks of capitalized words**

In this example, the `extract` statement identifies blocks of two to three capitalized words. In AQL, a block refers to a contiguous span of tokens, in this case two to three tokens. This example also uses a consolidation policy to exclude blocks that are contained within larger blocks from the output set of tuples.

```
create view CapitalizedWord as
  extract
    regex /[A-Z][a-z]*/
            with flags 'CANON_EQ'
        on 1 token in D.text
        as word
from Document D;

create view TwoToThreeCapitalizedWords as
  extract blocks
  with count between 2 and 3
  and separation 0 tokens
  on CW.word as capswords
from CapitalizedWord CW
consolidate on capswords using 'ContainedWithin';
```

The `consolidate` clause is applied to the `capswords` field by the extract blocks specification. The difference is that the target field referred to by the `consolidation` clause is an output field of the `extract` statement. The target field of the `select` statement is an input field. This behavior is similar to that of the `having` clause.

**Example 3: A nested `extract` or `select` statement as a view name**

The input view for an `extract` statement can be either a view name, as in Example 2, or a nested `extract` or `select` statement, as in this example:

```
create view SampleExtract as
  extract
  regex /foo/ on E.foobar as foo
  from 
    (extract regex /foobar/ on D.text as foobar
  from Document D) E;
```

**Example 4: Extract a statement with a select list**

In this example, we extract matches for a pattern, and at the same time, select multiple attributes from the input views.

```
create view Person as
  extract.F.first as first, M.initial as middle, L.last as last
          pattern ('Mr.'|'Ms.'|'Miss')? (<F.first> <M.initial>? <L.last>)
                    return group 0 as reference
                    and group 1 as salutation
                    and group 2 as name
  from FirstName F, MiddleInitial M, LastName L;
```


-   **Regular expressions**  
Use a regular expression extraction specification to identify matching patterns that are contained by the regular expression across the input text.
-   **Dictionaries**  
Use the dictionary extraction specification to extract strings from input text that are contained in a dictionary of strings.
-   **Splits**  
Use the split extraction specification to split a large span into several smaller spans.
-   **Blocks**  
Use the blocks extraction specification to identify blocks of contiguous spans across input text.
-   **Part of speech**  
Use the part-of-speech extraction specification to identify locations of different parts of speech across the input text.
-   **Sequence patterns**  
Use the pattern extraction specification to perform pattern matching across an input document and other spans extracted from the input document.

## Regular expressions

Use a regular expression extraction specification to identify matching patterns that are contained by the regular expression across the input text.

### Syntax

```
regex[es] /<regex1>/ 
         [and /<regex2>/ and ... and /<regex n>/]
       [with flags '<flags string>']
on <token spec>] <name>.<column>
<grouping spec>
```

### Description

-   `regex[es] /<regex1\>/`

    Specifies the regular expressions to be used in the extraction. By default, AQL uses Perl syntax for regular expressions, which means that regular expression literals are enclosed in two forward slash \(//\) characters. Regular expression escape sequences take precedence over other escape characters. AQL allows regular expressions in SQL string syntax, so a regular expression for United States phone numbers can be expressed as either of the examples:

    ```
    /\d{3}-\d{5}/
    ```

    ```
    '\\d{3}-\\d{5}'
    ```

-   `[and /<regex2\>/ and ... and /<regex n\>/ ]`

    Lists more regular expressions to be used in the extraction.

-   `[with flags '<flags string\>']`

    Specifies a combination of flags to control regular expression matching. This parameter is optional. These flags correspond to a subset of the flags that are defined in the Java™ implementation. If the flags string is not provided, AQL uses only the `DOTALL` flag by default.

    To specify multiple flags, separate them with the `|` character. For example, to specify multiline matching, matching that is not case-sensitive, and Unicode case folding, use the flags string `'MULTILINE|CASE_INSENSITIVE|UNICODE'`.


-   `[<token spec\>]`

    Indicates whether to match the regular expression only on token boundaries.

    ```
    ... [[between <number> and] <number> token[s] in] ...
    ```

    Token constraints are an optional part of the specification. If token constraints are omitted, AQL returns the longest non-overlapping match at each character position in the input text. If token constraints are present, the `extract` statement returns the longest match at every token boundary that is within the specified range of tokens in length. Each returned match must start at the beginning of a token and end at the end of a token. If there are multiple overlapping matches, the `extract` statement returns all of them.

    The locations of token boundaries depend on what tokenizer the runtime component is using to tokenize the document. If the engine is using the Standard tokenizer, then a token is defined as a sequence of word characters or a single punctuation character.

    For example, consider the string:

    ```
    "The fish are pretty," said the boy.
    ```

    The token boundaries are identified at these locations:

    ```
    ["][The] [fish] [are] [pretty][,]["] [said] [the] [boy][.]
    ```

-   `<name\>.<column\>`

    The view name and column name on which the regular expression is applied.

-   `<grouping spec\>`

    Determines how to handle the capturing of groups in the regular expression. Capturing groups are regions of the regular expression match that are identified by parentheses in the original expression. For example, the expression `(fish)(cakes)` has three capturing groups:

    -   Group 0 is the entire match `fishcakes`.
    -   Group 1 is `fish`.
    -   Group 2 is `cakes`.
    When you specify group IDs in the return clause of the syntax, each group ID must correspond to a valid group within each regular expression specified as part of the extract regex clause in the syntax.

    This is the format of the grouping specification:

    ```
    return 
        group <number> as <name>
        [and group <number> as <name>]*
    ```

    To return only Group 0 \(the entire match\), you can use a shorter, alternative format as in Example 1. This format is equivalent to `return group 0 as <name>`. `<name>` can be a simple identifier or a double-quoted identifier.


### Usage notes

-   In general, AQL supports the same features as the Java 5 regular expression implementation, as described in [Class Pattern: java.util.regex. The runtime component contains several regular expression engine implementations, including the built-in implementation of Java. During compilation, the Optimizer examines each regular expression and chooses the fastest engine that can run the expression.
-   The alternative execution engines might have slightly different semantics for certain corner cases. In particular, AQL does not guarantee the order in which alternatives are evaluated.

    For example, suppose that an extract statement matches the regular expression `/fish|fisherman/`, over the text 'fisherman'. The statement might match either 'fish' or 'fisherman', depending on which regular expression engine is used internally.

|AQL flag string|Java flag|Description|
|---------------|---------|-----------|
|CANON\_EQ|CANON\_EQ|Canonical equivalence: Different Unicode encodings of the same character are considered equivalent.|
|CASE\_INSENSITIVE|CASE\_INSENSITIVE|Perform matching that is not case-sensitive.By default, case-insensitive matching assumes that only characters in the US-ASCII character set are matched. Unicode-aware case-insensitive matching can be enabled by specifying the UNICODE flag with this flag.|
|UNICODE|UNICODE\_CASE|If case-insensitive matching is specified, use Unicode case folding to determine whether two characters are equivalent in a case-insensitive comparison in a manner that is consistent with the Unicode Standard. By default, case-insensitive matching assumes that only characters in the US-ASCII character set are matched.**Note:** The behavior of this flag is not defined when it is used without the CASE\_INSENSITIVE flag.|
|DOTALL|DOTALL|Make the dot character `.` match all characters, including newlines.|
|LITERAL|LITERAL|Treat the expression as a sequence of literal characters, ignoring the normal regular expression escape sequences.|
|MULTILINE|MULTILINE|Make the characters `^` and `$` match the beginning and end of any line, as opposed to the beginning and end of the entire input text.|
|UNIX\_LINES|UNIX\_LINES|Treat only the UNIX™ newline character `\n` as a line break, ignoring the carriage return character `\r`.|

-   Follow these guidelines to make your extractors run faster and be easier to maintain:
    -   Avoid long, complex regular expressions and use simpler, smaller regular expressions that are combined with AQL statements.
    -   Avoid unnecessary use of lookahead and lookbehind in regular expressions. You can usually achieve the same effect by adding predicates to the having clause of your extract statement.
    -   Use token constraints in your regular expression extraction specifications when possible.

### Examples

**Example 1: Using canonical Unicode equivalence to determine matches**

This example shows you how to find capitalized words that are not given names. Canonical Unicode character equivalence is used to determine matches. Notice the usage of the flag `‘CANON_EQ’` and that regex is performed on tokens:

```
create dictionary FirstNamesDict as
  (
  'Aaron', 'Matthew', 'Peter'
  );
create view NotFirstName as
  extract 
    regex /[A-Z][a-z]*/ 
    with flags 'CANON_EQ'
    on 1 token in D.text 
    as word 
from Document D
  having Not(ContainsDict('FirstNamesDict', word));
```

**Example 2: Usage of capturing groups**

The following example demonstrates the usage of capturing groups in an `extract regex` statement. The code extracts the fields of a United States phone number by using capturing groups:

```
create view Phone as
  extract regex /(\d{3})-(\d{3}-\d{4})/ 
    on between 4 and 5 tokens in D.text 
    return 
      group 1 as areaCode 
      and group 2 as restOfNumber
      and group 0 as fullNumber
from Document D;
```

**Example 3: Applying multiple regex over input text**

You can specify multiple regular expressions in the same `extract regex` statement by using the `regexes` syntax.

```
create view PhoneNum as
  extract regexes 
    /(\d{3})-(\d{3}-\d{4})/ and /[Xx]\d{3,5}/
        on between 1 and 5 tokens in D.text as num
from Document D;
```

**Example 4: Misuse of grouping specification**

The regular expression in this code sample contains neither `group -1` nor `group 3000`. This will result in a compilation error.

```
create view ErrorExample as
    extract regex /(\d+)/ 
    on D.text    
    return group -1 as wrongGroup and
          group 3000 as nonExistentGroup
from Document D;
```

## Dictionaries

Use the dictionary extraction specification to extract strings from input text that are contained in a dictionary of strings.

### Syntax

```
    dictionar[y|ies]
        '<dictionary>'
        [and '<dictionary>' and ... and '<dictionary>']
        [with flags '<flags string>']
```

### Description

-   `'<dictionary\>'`

    References a dictionary that is created by using either the `create dictionary` statement, `create external dictionary` statement, or a dictionary file on the file system.

-   `[and '<dictionary\>' and ... and '<dictionary\>']`

    References additional dictionaries to be used for extraction.

-   `[with flags'<flags string\>']`

    Controls dictionary matching. Currently there are two options:

    -   **Exact**

        Provides exact, case-sensitive matching.

    -   **IgnoreCase**

        Provides matching that is not case-sensitive.


If no flag is specified, the dictionary will match based on any flag that was specified when it was created. If no flag was specified during creation, it will match by using the `IgnoreCase` flag.

### Usage notes

-   Dictionaries are always evaluated on token boundaries. Specifically, a dictionary entry matches a region of text if the first token of the entry matches the first token of the text region, the second token of the entry matches the second token of the text region, and so on. Characters between two consecutive tokens are ignored.

    For example, assume that you are using a simple white space based tokenization model that is appropriate for a language such as English. Also, assume that the input text is “Let’s go fishing!”. If a dictionary consists of the term `go fish`, there is no match in the text for `Let's go fishing!`. However, if the dictionary consists of the entry `go fishing` \(notice there are two white spaces between go and fishing\), there is one match in the text `Let's go fishing!`. White space specifies that `go` and `fishing` are two distinct tokens. If there are one or more white space characters between the two tokens `go` and `fishing` in the input text, there is a match.

    For each match of a dictionary entry with input text, the `extract dictionary` statement generates an output tuple.


### Examples

**Example 1: Extracting terms from dictionary files**

Find person names by using dictionary files of common given and surnames and case-sensitive matching.

```
create view Name as
  extract
    dictionaries
        'first.dict' 
        and 'last.dict'
    with flags 'Exact'
        on D.text   
        as name
from Document D;
```

The following is sample content of `last.dict`:

```
#Dictionary for last names
Anthony
Aparicio
Cate
Lehmann
Radcliff
```

The following is sample content of `first.dict`:

```
#Dictionary for first names
Aaron
Candra
Freeman
Mathew
Matthew
Zoraida
```

**Note:**

-   A dictionary file system that is directly referenced in an `extract dictionary` statement cannot be explicitly configured with a set of languages so that the dictionaries are compiled and applied at run time. Instead, the set of languages is specified with the `set default dictionary language` statement if the module contains this statement.

    Therefore, direct referencing of dictionary files in an `extract dictionary` statement is not recommended and might be discontinued in the future. The preferred practice is to explicitly define a dictionary object by using the statement `create dictionary from file`, and then use that dictionary in the extract statement.

-   The compiler and runtime component attempt to locate dictionary files that are referenced in AQLs under the configured search path.


**Example 2: Extracting terms from an inline dictionary**

Find conjunctions by using an inline dictionary and the default matching that is not case-sensitive.

```
create dictionary ConjunctionDict as
  (
    'and', 'or', 'but', 'yet'
  );

create view Conjunction as
  extract
    dictionary 'ConjunctionDict'
        on D.text   
        as name
from Document D;
```


## Splits

Use the split extraction specification to split a large span into several smaller spans.

### Syntax

```
split using <name>.<split point column>
    [retain [right|left|both] split point[s]]
    on <name>.<column to split>
    as <output name>
```

### Description

The split extraction specification takes two arguments:

-   A column that contains longer target spans of text.
-   A column that contains split points.

The splitting algorithm works in two passes over the input view. The first pass groups all of the input tuples by the target column. The second pass goes through the tuples in each group, splitting the target column with each value of the splitting column.

-   `<name\>.<split point column\>`

    Specifies the split points for the extraction.

-   `[retain [right|left|both] split point[s]]`

    Specifies how to treat the left and right end points of each result. This argument is optional.

    -   If `retain left split point` is specified, then each output span also contains the split point to its left, if such a split point exists.
    -   If `retain right split point` is specified, then the system makes each output span contain the split point to its right.
    -   The split extraction also accepts null values as split points. For each such value, the extraction returns a tuple that contains the entire input span.
-   `<name\>.<column to split\>`

    Specifies the target column for the extraction.

-   `<output name\>`

    Defines the name of the output of the extraction.


### Examples

**Example 1: Split points and the `retain` clause**

If the split points are all the instances of the word fish in the phrase fish are swimming in the fish pond, then the various versions of the `retain` clause have the following effects:

-   **retain clause omitted**

    " are swimming in the " and " pond"

-   **retain right split point**

    " are swimming in the fish" and " pond"

-   **retain left split point**

    "fish are swimming in the " and "fish pond"

-   **retain both split points**

    "fish are swimming in the fish" and "fish pond"

**Example 2: Split extraction**

This example splits the document into sentences. It first uses a regular expression to identify sentence boundaries, then uses the split extraction specification to split the document text on the sentence boundaries.

```
create dictionary AbbreviationsDict as
  (
  'Cmdr.',
  'Col.',
  'DR.',
  'Mr.',
  'Miss.');

create view Sentences as
  extract 
    split using B.boundary 
        retain right split point
        on B.text
        as sentence
  from (
    extract 
        D.text as text,
        regex /(([\.\?!]+\s)|(\n\s*\n))/ 
        on D.text as boundary
        from Document D
    -- Filter the candidate boundaries.
      having Not(ContainsDict('AbbreviationsDict', 
            CombineSpans(LeftContextTok(boundary, 1), boundary)))
      ) B;
```


## Blocks

Use the blocks extraction specification to identify blocks of contiguous spans across input text.

### Syntax

```
blocks
    with count [between <min\> and] <max\>
    and separation [between 0 and] <max\> (tokens| characters)
    on <name\>.<column containing spans\>
    as <output name\>
```

### Description

-   `with count [between<min\> and] <max\>`

    Specifies how many spans can make up a block. The `<min\>` and `<max\>` values specify the minimum and maximum number of spans that can make up a block.

-   `[between 0 and] <max\>`

    Specifies the separation distance that is allowed between spans before they are no longer considered to be contiguous.

-   `(tokens| characters)`

    Specifies whether the separation distance of the span represents the number of tokens or the number of characters.

-   `<name\>.<column containing spans\>`

    The view name and column name on which the block operator is to be applied.

-   `<output name\>`

    Specifies a name for the output from the block operator.


### Usage notes

-   If there are multiple overlapping blocks in the input spans, a block extraction statement returns all possible blocks. Use consolidation to filter out redundant blocks.
-   An `extract` statement with block extraction specification yields blocks that each consist of an aggregation of values of a certain field from across multiple input tuples. Therefore, its select list cannot include fields from its input view.

### Examples

**Example 1: Extract blocks of words within a character range**

In the following code, the view `TwoToThreeCapitalizedWords` identifies blocks of two to three capitalized words within 100 characters of each other.

```
create view CapitalizedWords as
  extract
    regex /[A-Z][a-z]*/
        with flags 'CANON_EQ'
        on 1 token in D.text
        as word
from Document D;

create view TwoToThreeCapitalizedWords as
  extract blocks
    with count between 2 and 3
    and separation between 0 and 100 characters
    on CW.word as capswords
from CapitalizedWords CW;
```

**Example 2: Extract blocks of words within a token range**

The following code identifies blocks of exactly two capitalized words within five tokens of each other.

```
create view TwoCapitalizedWords as
extract blocks
    with count 2
    and separation between 0 and 5 tokens
    on CW.word as capswords
from CapitalizedWords CW;
```


## Part of speech

Use the part-of-speech extraction specification to identify locations of different parts of speech across the input text.

### Syntax

```
part_of_speech 
 '<part of speech spec>' 
 [and '<part of speech spec>']*
 [with language '<language code>']
 [and mapping from <mapping table name>]
 on <input column> as <output column\>
 from <input view>
```

### Description

-   `'<part of speech spec\>'`

    Identifies the parts of speech to extract from the input text. The `'<part of speech spec\>'` is one of the following strings:

    -   A string that contains a comma-delimited list of part-of-speech tags that are generated by the Multilingual tokenizer
    -   A combination of an internal part-of-speech name and flags, as defined by a mapping table
-   `[and '<part of speech spec\>']*`

    Identifies the additional parts of speech tags for extraction.

-   `[with language '<language code\>']`

    Specifies the language to be used in the extraction. The `<language code\>` is a two-letter, lowercase language code, such as 'en' or 'ja'. If this argument is omitted, the language for part-of-speech extraction is assumed to be English

-   `[and mapping from <mapping table name\>]`

    Specifies the name of an AQL table that maps raw part-of-speech tags such as "NN" to combinations of high-level parts of speech and flags. While the optional mapping table can have variable names, a part-of-speech mapping table is required to have these column names:

    -   **tag**

        The column that holds a Multilingual tokenizer part-of-speech tag.

    -   **basetag**

        The column that holds the corresponding internal tag.

    -   **flagstr**

        The column that holds a comma-delimited list of flags that are associated with the indicated part of speech.

    The mapping table must be defined by using the `create table` statement in the same module as the extract `part_of_speech` statement that uses it. It cannot be an imported table, and it cannot be an external table.

    ```
    create table POSMapping_EN(tag Text, basetag Text, flagstr Text)
    as values
     ('NN','Noun','singular'),
     ('NNP','Noun','singular,proper'),
     ( 'VBG','Verb','presentParticiple');
    ```

-   `<input column\>`

    Specifies the column of the input view from which to extract part-of-speech information.

-   `<output column\>`

    Specifies the name of the column where the spans of the tokens with the indicated parts of speech are sent.

-   `<input view\>`

    Specifies the input view from which to extract part-of-speech information.


### Usage notes

-   Part of speech extraction works only when is using the Multilingual tokenizer. If the system uses the Standard tokenizer, a `part_of_speech` extraction generates an error.


### Parts of speech tags for languages

For English, the Multilingual tokenizer uses the part-of-speech tags that are listed in the following table.

|Tag|Description|
|---|-----------|
|`UNKNOWN`|Unknown word|
|`DT`|Determiner|
|`QT`|Quantifier|
|`CD`|Cardinal number|
|`NN`|Noun, singular or mass|
|`NNS`|Noun, plural|
|`NNP`|Proper noun, singular|
|`NNPS`|Proper noun, plural|
|`EX`|Existential there|
|`PRP`|Personal pronoun \(PP\)|
|`PRP$`|Possessive pronoun \(PP$\)|
|`POS`|Possessive ending|
|`RBS`|Adverb, superlative|
|`RBR`|Adverb, comparative|
|`RB`|Adverb|
|`JJS`|Adjective, superlative|
|`JJR`|Adjective, comparative|
|`JJ`|Adjective|
|`MD`|Modal|
|`VB`|Verb, base form|
|`VBP`|Verb, present tense, other than third person singular|
|`VBZ`|Verb, present tense, third person singular|
|`VBD`|Verb, past tense|
|`VBN`|Verb, past participle|
|`VBG`|Verb, gerund, or present participle|
|`WDT`|Wh-determiner|
|`WP`|Wh-pronoun|
|`WP$`|Possessive wh-pronoun|
|`WRB`|Wh-adverb|
|`TO`|to|
|`IN`|Preposition or subordinating conjunction|
|`CC`|Coordinating conjunction|
|`UH`|Interjection|
|`RP`|Particle|
|`SYM`|Symbol|
|`$`|Currency sign|
|`'' ''`|\(double or single\) quotation mark|
|`\(`|Left parenthesis \(round, square, curly, or angle bracket\)|
|`\)`|Right parenthesis \(round, square, curly, or angle bracket\)|
|`,`|Comma|
|`:`|Mid-sentence punctuation \(: ; -- -\)|
|`.`|Sentence-final punctuation \(. ! ? ...\)|

For Indo-European Languages other than English, the Multilingual tokenizer uses the part-of-speech tags that are listed in the following table.

|Tag|Description|
|---|-----------|
|`UKW`|Unknown word|
|`CC`|Coordinating Conjunction|
|`CD`|Cardinal Number|
|`DT`|Determiner|
|`IN`|Preposition or subordinating conjunction|
|`JJ`|Adjective|
|`MD`|Modal|
|`NN`|Noun, singular or mass|
|`NNP`|Proper noun|
|`PRP`|Pronoun|
|`QT`|Quantifier|
|`RB`|Adverb|
|`SYM`|Symbol|
|`UH`|Interjection|
|`VB`|Verb, base form|
|`WH`|Wh-pronoun|

For Chinese, the Multilingual tokenizer uses the part-of-speech tags that are listed in the following table.

|Tag|Description|
|---|-----------|
|`ac`|Complementary adjective|
|`ag`|General adjective|
|`b`|Distinction word|
|`cbc`|Postposition \(after a clause\)|
|`cbs`|Postposition \(after a sentence\)|
|`cbw`|Postposition \(after a word\)|
|`cf`|Preposed conjunction|
|`cmc`|Conjunction between clauses|
|`cms`|Conjunction between sentences|
|`cmw`|Conjunction between words|
|`db`|The adverb bing4|
|`dd`|Existential adverb|
|`dr`|General adverb|
|`e`|Exclamation|
|`f`|Position and direction|
|`h`|Noun prefix|
|`i`|Phrasal idiom|
|`j`|Abbreviated words|
|`kn`|Noun suffix|
|`kv`|Verb suffix|
|`l`|Idiom|
|`mab`|Postposed auxiliary numerals|
|`maf`|Preposed auxiliary numerals|
|`mam`|Auxiliary numerals|
|`mg`|Approximation numerals|
|`mh`|The numeral ban4|
|`mm`|Numeral followed by measures|
|`mo`|The numeral ling2|
|`mw`|Position numerals|
|`mx`|Ordinal numerals|
|`nf`|Family names|
|`ng`|General nouns|
|`npf`|Person names|
|`npr`|Other proper names|
|`npu`|Organization names|
|`o`|Onomatopoeia word|
|`pba`|The preposition ba3/jiang1|
|`pbei`|The preposition bei4|
|`pg`|General preposition|
|`pzai`|The preposition zai4|
|`qnc`|Collection measure|
|`qnf`|Forming measure|
|`qng`|Nominal measure ge4|
|`qni`|Individual measure|
|`qnk`|Category measure|
|`qnm`|Existential measure|
|`qns`|Infinitive measure|
|`qnv`|Volume measure|
|`qnz`|Quasi-measure|
|`qt`|Temporal measure|
|`qv`|Verbal measure|
|`rd`|Adverbial pronoun|
|`rm`|The pronoun mei3|
|`rn`|Nominal pronoun|
|`rp`|Predicative pronoun|
|`s`|Place|
|`t`|Time|
|`ur`|Other auxiliary particles|
|`usde`|Auxiliary particle de0|
|`usdf`|Auxiliary particle de2|
|`usdi`|Auxiliary particle di0|
|`ussb`|Auxiliary particle bu4|
|`ussi`|Auxiliary particle shi4-de0|
|`ussu`|Auxiliary particle suo3|
|`uszh`|Auxiliary particle zhi1|
|`utg`|Auxiliary particle guo4|
|`ut1`|Auxiliary particle le0|
|`utz`|Auxiliary particle zhe0|
|`va`|Auxiliary verb|
|`vc`|Complementary verb|
|`vf`|Complementary verb|
|`vg`|General verb|
|`vga`|Verb with adjective object|
|`vgd`|Verb with direct and indirect objects|
|`vgj`|Verb with concurrent object|
|`vgn`|Verb with nominal object|
|`vgo`|Verb without object|
|`vgs`|Verb with clause object|
|`vgv`|Verb with verbal object|
|`vh`|The verb you3|
|`vi`|Linking verb|
|`vv`|Successive verb|
|`vy`|The verb shi4|
|`x`|Other|
|`y`|Tone word|
|`z`|State word|
|`ADJ`|Adjective \(non-predicate\)|
|`ADV`|Adverb|
|`ASP`|Aspect Marker|
|`AUX`|Verb \(Auxiliary\)|
|`CJ`|Conjunction|
|`CL`|Classifier|
|`CTM`|Modifier Clitic|
|`CTN`|Noun Clitic|
|`CTS`|Sentential Clitic|
|`D`|Determiner|
|`INT`|Interjection|
|`LIM`|Limiter|
|`LOC`|Locative|
|`NC`|Noun|
|`NF`|Family Name|
|`NP`|Proper Name|
|`NR`|Pronoun|
|`PREP`|Preposition|
|`PREF`|Prefix|
|`Q`|Quantifier|
|`SEN`|Sentence|
|`SUF`|Suffix|
|`V`|Verb|

For Japanese, the Multilingual tokenizer uses the part-of-speech tags that are listed in the following table.

|Tag|Description|
|---|-----------|
|`Michigo`|Unknown|
|`Doushi`|Verb|
|`AddV`|Formal Verb \(subsidiary verb\)|
|`AddV2`|Formal Verb \(verbify\)|
|`Meishi`|Noun|
|`FukushitekiMeishi`|Adverbial Noun|
|`Josuushi`|Numeral Classifier|
|`KeishikiMeishi`|Formal Noun|
|`KoyuuKoyuuMeishi`|Unknown Proper Noun \(can be a start of phrase\)|
|`KoyuuMeishi`|Unknown Proper Noun|
|`KoyuuMeishiSei`|Proper Noun - LastName|
|`KoyuuMeishiMei`|Proper Noun - FirstName|
|`KoyuuMeishiSoshiki`|Proper Noun - Organization|
|`KoyuuMeishiKuni`|Proper Noun - Country|
|`KoyuuMeishiChimei`|Proper Noun - Place name|
|`KoyuuMeishiSonota`|Proper Noun - Other|
|`KoyuuMeishiSeimei`|Proper Noun - PersonName \(Lastname + Firstname\)|
|`KeiyouDoushi`|Adjective Verb|
|`AddAn`|Adjective Verb \(derivation\)|
|`AddAn2`|Adjective Verb \(yet another derivation\)|
|`Daimeishi`|Pronoun|
|`AddA`|Formal adjective|
|`Keiyoushi`|Adjective|
|`Fukushi`|Adverb|
|`Rentaishi`|Pre-noun Adjectival|
|`Setsuzokushi`|Conjunction|
|`Setsubiji`|Suffix - Common|
|`Settouji`|Prefix - Common|
|`SuushiSetsubi`|Suffix - Numeral|
|`SuushiSettou`|Prefix - Numeral|
|`Jodoushi`|Auxiliary Verb|
|`AuxA1`|Auxiliary Verb \(adjective\)|
|`AuxV`|Auxiliary Verb \(verbal\)|
|`AuxV1`|Auxiliary Verb \(derivation\)|
|`JodoushiDesu`|Auxiliary Verb \("desu"\)|
|`PartAux`|Auxiliary Verb \(part of collocation\)|
|`InyouJoshi`|Particles - case markers \(extract\)|
|`JoshiNo`|Particles - case markers \("no"\)|
|`KakuJoshi`|Particles - case markers|
|`KakuJoshi1`|Particles - case markers \(connect with non-indeclinable words\)|
|`ParticleAdnominal`|Particles - case markers \(collocation\)|
|`ParticleV`|Particles - case markers \(collocation between verb and particles\)|
|`SetsuzokuJoshi`|Particles - conjunctive particles|
|`FukuJoshi`|Particles - adverbial particles|
|`FukuJoshi1`|Particles - adverbial particles \(anomalistic\)|
|`ShuuJoshi`|Particles - sentence ending particles|
|`FuteiJoshi`|Particles - indefinite particles|
|`HeiretsuJoshi`|Particles - parallel markers|
|`RentaiHeiretsuJoshi`|Particles - parallel markers \(parallel nouns\)|
|`KeiJoshi`|Particles - binding particles|
|`PartParticle`|Particles \(part of collocation\)|
|`ParticleIdiomRy`|Particles - collocation particles \(not case markers\)|
|`RentaiJoshi`|Particles - adnominal particle|
|`JoukyouKa`|Particles - continuative particle|
|`JoukyoukaFunc`|Particles - continuative particle \(collocation\)|
|`JunTaigen`|Particles - phrasal particles|
|`Cushion`|Interjection|
|`VInfl`|Inflection Suffix - verb|
|`AddVInfl`|Inflection Suffix - adverb|
|`PartVInfl`|Inflection Suffix - verb \(collocation\)|
|`AInfl`|Inflection Suffix - adjective|
|`AnInfl`|Inflection Suffix - adjective verb|
|`AuxInfl`|Inflection Suffix - auxiliary verb|
|`PartAuxInfl`|Inflection Suffix - auxiliary verb \(collocation\)|
|`PartVSuf`|Part of verb suffix|
|`Kigou`|Symbol mark|
|`HirakiKakko`|Punctuation - opened parenthesis|
|`TojiKakko`|Punctuation - closed parenthesis|
|`Kuten`|Punctuation - Japanese period \(full stop\)|
|`Touten`|Punctuation - Japanese comma \(pause mark\)|
|`Delimiter`|Punctuation - Alphabet delimiter|
|`SuujiComma`|Punctuation - Numeric delimiter|

For Korean, the Multilingual tokenizer uses the part-of-speech tags that are listed in the following table.

|Tag|Description|
|---|-----------|
|`NNG`|General Noun|
|`NNP0`|Proper Noun - LastName|
|`NNP1`|Proper Noun - FirstName|
|`NNP2`|Proper Noun - Organization|
|`NNP3`|Proper Noun - Country/Region|
|`NNP4`|Proper Noun - Place Name|
|`NNP5`|Proper Noun - Others|
|`NNP6`|Proper Noun - PersonName|
|`NNB`|Bound Noun|
|`NNM`|Numerical Unit|
|`NP`|Pronoun|
|`NP\_JKS`|Combination of NP+JKS|
|`NR`|Number - Korean Characters|
|`VV`|Verb|
|`VVJ`|Exist Verb|
|`VA`|Adjective|
|`VCP`|Positive Copula|
|`VCN`|Negative Copula|
|`VXV`|Auxiliary Verb|
|`VXJ`|Auxiliary Exist Verb|
|`VXA`|Auxiliary Adjective|
|`VVX`|Derived Verb Using Suffix|
|`VAX`|Derived Adjective Using Suffix|
|`MM`|Modifier - Adnominal|
|`MMN`|Modifier - Adnominal for Number|
|`MAG`|Modifier - Adverb \(General\)|
|`MAJ`|Modifier - Adverb \(Conjunction\)|
|`IC`|Interjection|
|`JKS`|Postpositional \(Subjective\)|
|`JKG`|Postpositional \(Adnominal\)|
|`JKO`|Postpositional \(Objective\)|
|`JKB`|Postpositional \(Adverbial\)|
|`JKV`|Postpositional \(Vocative\)|
|`JKQ`|Postpositional \(Quotation\)|
|`JX`|Auxiliary Postposition|
|`JC`|Conjunctive Postposition|
|`XPN`|Nominal Prefix|
|`XSN`|Nominal Suffix|
|`XSV`|Verbal Suffix|
|`XSA`|Adjective Suffix|
|`SF`|Symbol - Sentence Final|
|`SP`|Symbol - Pause, Comma|
|`SS`|Symbol - Citation|
|`SE`|Symbol - Ellipsis|
|`SO`|Symbol - Pattern|
|`SW`|Symbol - Won, Dollar|
|`SL`|Foreign Language|
|`SH`|Korean, Chinese Characters|
|`SN`|Number - Only Composed with Digit|
|`UNK`|Unknown Word|

For Turkish, the Multilingual tokenizer uses the part-of-speech tags that are listed in the following table.

|Tag|Description|
|---|-----------|
|`NN`|Noun|
|`NNP`|Proper noun|
|`PRP`|Pronoun|
|`JJ`|Adjective|
|`JJR`|Adjective, comparative|
|`VB`|Verb|
|`RB`|Adverb|
|`RBN`|Adverb, negative suffix|
|`IN`|Adposition|
|`CC`|Conjunction|
|`WP`|Interrogative pronoun|
|`WRP`|Interrogative particle|
|`RP`|Particle, suffix|
|`UH`|Interjection|
|`CD`|Cardinal number|
|`SYM`|Symbol|
|`UKW`|Unknown|

### Examples

**Example 1: Using a part of speech tag directly in an extract statement**

The view `EnglishNoun` extracts English nouns \(singular or mass\) or proper nouns \(singular\).

```
create view EnglishNoun
as extract parts_of_speech 'NN' and 'NNP'
with language 'en' on D.text
as noun from Document D;
```

**Example 2: Using a mapping table for parts of speech specification**

The view `EnglishNoun` uses the mapping table `POSMapping_EN` to specify part of speech tag.

```
-- Create a mapping table to translate low-level part-of-speech tags
-- into combinations of part-of-speech names and flags.
create table POSMapping_EN(tag Text, basetag Text, flagstr Text)
as values
('NN','Noun','singular'),
('NNP','Noun','singular,proper');

-- Use the mapping table to find singular nouns.
-- This view is equivalent to the "EnglishNoun" view defined above
create view EnglishNoun2
as extract part_of_speech 'Noun' with flags 'singular'
      with language 'en' and mapping from POSMapping_EN
      on D.text
as noun from Document D;
```

**Example 3: Identifying some common parts of speech in Japanese documents**

The following example shows a sample part of speech extraction for the Japanese language:

```
create view Surname as
extract part_of_speech 'KoyuuMeishiSei'
  with language 'ja' on D.text as name
from Document D;

create view GivenName as
extract part_of_speech 'KoyuuMeishiMei'
  with language 'ja' on D.text as name
from Document D;

create view Place as
extract parts_of_speech 'KoyuuMeishiChimei' and 'KoyuuMeishiKuni'
  with language 'ja' on D.text as pname
from Document D;

create view Organization as
extract part_of_speech 'KoyuuMeishiSoshiki'
  with language 'ja' on D.text as oname
from Document D;
```


## Sequence patterns

Use the pattern extraction specification to perform pattern matching across an input document and other spans extracted from the input document.

### Syntax

The general syntax of a sequence pattern is to first specify the pattern to be matched in the text, and then to specify what is to be returned by the extractor. The final part of the sequence pattern specifies what is the input to the pattern; it might be a column from a previously-defined view, or it might be the entire document text.

```
pattern <pattern specification> [return clause] [with inline_match on <viewname.colname>]  
```

### Description

-   `<pattern specification\>`

    A `<pattern specification\>` is composed of multiple Atoms. An individual Atom can be a column from an already-defined view, a fixed string, or a regular expression. You can specify your Atoms to be optional and repeating, and specify token gaps between Atoms.

    Remember that the pattern specification is part of a larger AQL statement, which includes an extract clause.

    Here is a simple example of how to create a view that contains three adjacent matches from earlier defined views. In this example, the entire combination is returned, which is what `group 0` refers to:

    ```
    create view Money as 
    extract pattern <C.match> <N.match> <Q.match> 
    return group 0 as  match
    from Currency C, Number N, Quantifier Q;
    ```

    If your Atoms do not need to be exactly adjacent to each other, then you can use token gaps between the Atoms to allow for more matches. This example finds mentions of persons that follow within 0 to 2 tokens by a phone number. Notice the `<Token>{0,2}` construct, which indicates that a gap of 0 to 2 tokens between the person and phone annotations is allowed.

    ```
    create view Phone as
    extract regex /(\d{3})-(\d{3}-\d{4})/
      on between 4 and 5 tokens in D.text
      return
       group 1 as areaCode
       and group 2 as restOfNumber
       and group 0 as fullNumber
    from Document D;
    create view PersonPhone as
    extract 
      pattern (<P.name>) <Token>{0,2} (<Ph.fullNumber>)
      return group 0 as match
       and group 1 as person
       and group 2 as phone
    from Person P, Phone Ph;
    ```

    Token gap constructs are restricted to occur within sequence expressions. Also, each token gap in a sequence must be preceded and followed by a "non-token gap" expression. As a result, `extract pattern` statements produce exceptions:

    ```
    -> pattern consisting only of a token gap is an error
    extract pattern <Token> as match from ...
    -> pattern beginning with a token gap is an error
    extract pattern <Token> {0,2} <Ph.phone> as match from ...
    -> pattern ending with a token gap is an error
    extract pattern <P.name> <Token> ?  as match from ...
    -> group consisting only of a token gap is an error
    extract pattern <P.name> (<Token>)  <Ph.phone> as match from ... 
    ```

    Use the \(min,max\) syntax to indicate the number of times each Atom repeats. You can also use the ? syntax to indicate that an Atom or repeating Atom is optional. Atoms, along with their indications for repeating and optional, are combined to create sequences.

    Here is a more complex example that shows how to repeat elements. Find candidate hotel names by identifying occurrences of one to three capitalized words, followed by a 'Hotel' or 'hotel' token.

    ```
    create view CapsWord as
    
    extract
        regex /[A-Z][a-z]*/        
           on 1 token in D.text
           as word
    from Document D;
    
    create view HotelCandidate as
    extract 
      pattern <CW.word>{1,3} /[Hh]otel/ as hotelname
    from CapsWord CW;
    ```

    You can also use the `|` operator to indicate a choice between Atoms, as in `extract pattern <A.match>| <B.match> <C.match> as match from Apple A, Bacon B, Chocolate C;`. This pattern can be explained as “match either one `A.match` OR a sequence of a `B.match` followed by a `C.match`. You can see a complete example that uses the `|` operator in Example 1.

    After you created your pattern, each match to your `<pattern specification>` constructs an output result according to the return clause of the pattern specification, as well as the optional `<select list>` at the beginning of the `extract` statement. The results are filtered and consolidated according to the `having`, `consolidate`, and `limit` clauses of the `extract` statement. For example, if there are multiple overlapping matches for the pattern specification, all of the possible matches will be returned, and you can use a `consolidation` clause to filter out redundant outputs.

    Consider the previous example, but now the goal is to remove matches that contain the word 'Sheraton', and to consolidate resulting matches by removing the ones that are contained within a larger match. For example, we do not want to find “Best Garden Hotel” and also “Garden Hotel” across the same span of text.

    ```
    create view HotelCandidate as
    extract 
      pattern <CW.word>{1,3} /[Hh]otel/ as hotelname
    from CapsWord CW
    having Not(ContainsRegex(/.*Sheraton.*/,hotelname))
    consolidate on hotelname using 'ContainedWithin';
    ```


Now that you are familiar with the syntax and some examples, this diagram outlines the full syntax for the pattern specification. Refer to this full syntax when you start building patterns to see how to structure the pattern that you want to build.

If you are familiar with POSIX character-based regular expressions, then you will recognize that the syntax is similar. In this case, the syntax allows for white space between elements, and what an element can be in order to suit the AQL purposes is also defined.Note that the term `Alternation` in this case means choice. Using a vertical bar between elements indicates that there is a choice, which can be grouped by using `( )` .

```
Pattern   -> Alternation
Alternation  -> Sequence | Sequence | ... | Sequence
Sequence   -> Optional Optional ... Optional
Optional   -> Repeat | Repeat ? Repeat     -> Atom | Atom { min, max }
Atom     -> <view_name.column_name>
     'string'
   <'string' [match parameters]>
     /regex/
     <Token>
     Group
Group -> ( Pattern )
```

Specifically, an Atom can have six formats:

-   `<view_name.column_name\>`

    Specifies a column from one of the views, table, or table function references that are named in the from list of the `extract pattern` statement.

-   **'string'**

    Specifies a match to the specified string by using the AQL default dictionary match semantics.

-   `<'string' [match parameters]\>`

    Specifies a match to the specified string by using the dictionary matching semantics that are specified by the `[match parameters]`. The format of `[match parameters]` is case `(exact | insensitive)`. This specifies the type of case-folding that is used to determine the string matches. To specify an exact case-sensitive match select exact. To specify a match that is not case-sensitive match, select the default value insensitive.

-   `/regex/`

    Specifies a character-based regular expression match with matching constrained to a single token in the document text. In addition, the syntax allows a special token gap construct to be specified in a sequence expression to indicate a match between `min` and `max` number of tokens.

-   `<token\>`

    A match for any token.


-   `[return clause]`

    Generates extracted values for each match of the pattern expression according to the return clause. The `return` clause has the same semantics as the `return` clause in an `extract regex` statement.

-   `[with inline_match on <viewname.colname\>]`

    For the Atoms such as string and regex Atoms, the `with inline_match` clause determines which text object the system uses for string or regex extraction. For example, if the clause is `with inline_match on Email.subject`, then all dictionaries and regular expressions defined inline in the pattern specification are applied to the subject field of the `Email` view. If the `with inline_match` is absent, string and regular expression extraction are run by default on the entire Document.text. In this case, viewname must be the name of a view or table that is defined in the current module, or imported from another module; references to table functions are not allowed in the with inline\_match clause.

-   `[with language as <language code(s)\>]`

    Specifies a comma-delimited list of two-letter language codes, such as en \(English\) or zh \(Chinese\) for the languages on which to evaluate the string. There will be no match on documents whose language code is not contained in this string. If the language parameter is omitted, the evaluation language defaults to one of the following language sets:

    -   If it is declared, the language sets that are specified through the set default language statement in the containing module.
    -   The language sets that contain German \(de\), Spanish \(es\), English \(en\), French \(fr\), Italian \(it\), and the unspecified language \(x\_unspecified\)

### Usage notes

-   The semantics of an `extract pattern` statement is driven by the pattern specification. Each match constructs an output result according to the return clause of the pattern specification and the select list at the top of the `extract` statement. The results are filtered and consolidated according to the `having`, `consolidate`, and `limit` clauses of the extract statement. If there are multiple overlapping matches for the pattern specification, a pattern extraction outputs all possible matches. Use consolidation to filter redundant outputs.
-   The semantics of the `from` clause of an `extract pattern` statement are different from other forms of `extract` statements that do not have a pattern specification. The general semantics of an `extract` statement require that the extraction specification is evaluated over each combination of the views that are defined in the `<from list\>`. If at least one of the views in the `<from list\>` does not contain any results on a particular document, then the output of the extract statement is empty because the set of all combinations of results in the input views is empty. In the special case of extract pattern statements, the from clause is a placeholder that declares the names of relations that are involved in the pattern specification. The semantics of the statement are driven only by the pattern specification. In particular, the output of the statement can be non-empty even when some of the input views are empty.
-   An `extract` statement that uses sequence pattern extraction can carry forward the columns of any view in the `from` list, but only if the view name does not appear in a repeat element of the pattern specification. For example, the statement `CapsWordOneToThree` results in a compilation error. The error occurs because the carried forward column `CW.type` at the top of the `extract` statement belongs to the view name `CW`, which is in the repeat element `<CW.word>{1,3}` of the pattern specification.

    ```
    create view CapsWord as
    extract 'UpperCase' as type,
        regex /[A-Z].*/ on 1 token in D.text as word
    from Document D;
    
    ---> This results in and error due to the repeating element CW.word
    create view CapsWordOneToThree as
    extract CW.type as type,
        pattern <CW.word>{1,3} as match 
    from CapsWord CW;  
    
    output view CapsWordOneToThree;
    ```

    **Note:** For columns that are carried forward from view names that appear in alternation or optional elements of the pattern specification, the value of the output column is `null` when the corresponding alternative or the optional element is not present in the text. An example that illustrates this point is in the `Person` view of Example 1.

-   Groups that occur under a repeat element cannot be output in the `return` clause of the statement. For example, the following statement causes an exception:

    ```
    create view CapsWordOneToThree as
      extract 
             pattern (<CW.word>){1,3}   
            return group 0 as fullmatch      
                   and group 1 as word   -- not allowed due to repeat
      from CapsWord CW;
    ```


### Examples

**Example 1: Sequence pattern with capturing groups**

The goal of this example is to find person names by identifying occurrences of given name, optionally followed by middle initial, followed by a surname, and the entire match that is optionally preceded by a common salutation. In addition, the extractor should return the entire match as reference, the first group as salutation, and the second group as name and carry forward the values of the given name, middle initial, and surname from the respective input views.

```
create view MiddleInitial as
extract regex /\b([\p{Lu}\p{M}*]\.\s*){1,5}\b/
            on between 1 and 10 tokens in D.text as initial
from Document D;

create view Person as
extract F.first as first,
        M.initial as middle,
        L.last as last,
        pattern ('Mr.'|'Ms.'|'Miss')? (<F.first> <M.initial>? <L.last>)
return group 0 as reference
  and group 1 as salutation
  and group 2 as name
from FirstName F, MiddleInitial M, LastName L;
```

Since the subpattern expression `('Mr.'|'Ms.'|'Miss')?` is optional, the value of the salutation output column is `null` when a salutation is not present in the text. Similarly, since the pattern subexpression `<M.initial>?` is optional, the value of the output column middle is `null` when a middle initial is not present.

**Example 2: Sequence pattern with string match and match parameters**

The goal of this example is to find occurrences of meeting notes for known projects by examining the title annotations of the document. Notice the `with inline_match` clause, which specifies that string matching is done over the match field of the view `Title`, as opposed to the entire document text.

```
create view Project as
extract 
regex /[Pp]roject\s?\w*/ on D.text as name
from Document D;


create view Title as
extract regex /[A-z][a-z]+.*/ 
on between 1 and 20 tokens in D.text as match
from Document D;


create view MeetingNote as
extract 
pattern <'Meeting Notes:'[with case exact]> (<P.name>)
return group 0 as match
  and group 1 as projectname
with inline_match on Title.match
from Project P;
```

**Example 3: Sequence pattern that returns non-empty results even when an input view is empty**

The following statement generates results even when the input view LastName is empty. The second part of the pattern specification, `<L.name\>?` contains an optional element. The semantics of the pattern specification is designed to output all spans that are composed of either a `FirstName.name` span or a `FirstName.name` span that is immediately followed by a `LastName.name` span. Therefore, on documents for which the view LastName is empty, the result of the statement consists of all spans that comprise a single `FirstName.name` span that is identified from that document.

```
create dictionary FirstNamesDict as
(
  'Aaron', 'Matthew', 'Peter'
);
create dictionary LastNamesDict as
(
  'Anthony', 'Lehman', 'Radcliff'
);

create view LastName as
  extract dictionary 'LastNamesDict'
  on D.text as last 
from Document D
having MatchesRegex(/((\p{L}\p{M}*)+\s+)?\p{Lu}\p{M}*.{1,20}/, last);

create view FirstName as
  extract dictionary 'FirstNamesDict'
  on D.text as first
from Document D
having MatchesRegex(/\p{Lu}\p{M}*.{1,20}/, first);

create view PersonName as
extract pattern <F.first> <L.last>? as fullName
from FirstName F, LastName L;
```


## The `select` statement

The `select` statement in AQL provides a powerful mechanism for using various specifications to construct and combine sets of tuples.

### Syntax

The `select` statement is similar in structure to a SQL `SELECT` statement:

```
select `<select list>`
  from `<from list>`
  [where `<where clause>`]
  [consolidate on `<column>` 
     [using '`<policy>`' [with priority 
         from `<column> ` [priority order]]]]
  [group by `<group by list>`]
  [order by `<order by list>`]
  [limit `<maximum number of output tuples for each document>`];
```

### Description

-   `<select list\>`

    A comma-delimited list of output expressions.

-   `<from list\>`

    A comma-delimited list that is the source of the tuples to be selected.

-   `[where <where clause\>]`

    Defines a predicate to be applied on each tuple that is generated from the Cartesian product of all of the tuples in the relations in the `from` clause. This clause is optional.

-   `[consolidate on<column\>[using '<policy\>' [with priority from <column\> priority order]]]]`

    Defines a consolidation policy to manage overlapping spans. This clause is optional.

-   `[group by<group by list\>]`

    Groups the tuples that are produced from the same document by common values of a specified field. This clause is optional.

-   `[order by<order by list\>]`

    Orders the output tuples that are produced by the `select` statement from each document. The order is based on the values of the order-by list, a comma-delimited list of expressions. This clause is optional.

-   `[limit <maximum number of output tuples for each document\>]`

    Limits the number of output tuples for each document to the specified maximum. This clause is optional.


### Usage Notes

The semantics of the `select` statement are as follows:

-   Determine the input data \(in tuples\) by taking the Cartesian product of relations in the from list.
-   For each input tuple that is generated, filter it by applying the predicates in the \(optional\) `where` clause.
-   If the optional `group by` clause is present, group tuples produced from the same document by the values specified in the group-by list and compute the result of the `aggregate` functions within the select list.
-   Consolidate any overlapping tuples, according to the policy defined in the \(optional\) `consolidation` clause. If the optional `order by` clause is present, order these tuples by the values of the order-by list.
-   Compute all expressions within the `select` list on each tuple, and rename the columns as specified by the `as` clauses.
-   If the optional `limit` clause is present, limit the number of output tuples to the specified number of tuples for each document.

### Examples

An example of how to use the `select` statement is to extract phone numbers that match a pattern. Assume that the `PhoneNumbers` view that extracts phone numbers of the pattern XXX-XXX-XXXX for United States is already defined. This `select` statement evaluates the regular expression for the pattern 444-888-XXXX across the input text. The view has the output columns `documentText` and `phoneNumber`. In addition, the output is limited to the first occurrence of this phone number pattern that is identified per document.

```
create view PhoneNumbersPattern1 as
select D.documentText, D.phoneNumber
from PhoneNumbers D
where MatchesRegex(/444-888-\d{4}/,D.phoneNumber)
limit 1;
```

Another example of how you can use the `select` statement is to find approximate mappings of people and their corresponding phone numbers. Assume that the view `Person` is already defined, and that it has the columns `person` and the view `PhoneNumbers`. This `select` statement evaluates the `where` clause to find text spans that contain a person mention followed by a phone number within 1 to 3 words or tokens. The input to this statement is represented by a join of the `Person` and `PhoneNumbers` views in the from list.

```
create view PersonPhone as
select P1.documentText, P1.person, P2.phoneNumber, CombineSpans(P1.person,P2.phoneNumber) as personPhoneSpan
from Person P1, PhoneNumbers P2
where FollowsTok(P1.person,P2.phoneNumber,1,3);
```

The `personPhoneSpan` column will contain the matching spans that give the approximate person-phone mapping.

```
personPhoneSpan
John : 433-999-1000
Martha Mob 433-999-1001
```

-   **The select list**  
The select list in an AQL `select` or `extract` statement consists of a comma-delimited list of output expressions.
-   **The from list**  
 The second part of a `select` or an `extract` statement in AQL is the from list. The from list is a comma-separated list that is the source of the tuples to be selected or extracted.
-   **The where clause**  
The optional `where` clause defines a predicate to be applied on each tuple generated from the Cartesian product of all tuples in the relations in the `from` clause.
-   **The consolidate on clause**  
 The optional `consolidate on` clause specifies how overlapping spans are resolved across tuples that are output by a `select` or `extract` statement. Tuples with non-overlapping spans are not affected when this clause is used.
-   **The group by clause**  
The optional `group by` clause of a `select` statement directs the runtime component to group tuples that are produced from the same document by common values of a specified field.
-   **The order by clause**  
The optional `order by` clause directs the runtime component to order the output tuples that are produced by the select statement from each document based on the values of the order by list, which is a comma-delimited set of expressions
-   **The limit clause**  
The optional `limit` clause specifies a limit on the number of output tuples that are produced by the select statement for a document.
-   **The select... into statement**  
 The `select ... into` statement is useful for defining a view and specifying that it is an output view in a single statement.



## The select list

The select list in an AQL `select` or `extract` statement consists of a comma-delimited list of output expressions.

### Syntax

Each select expression must be in one of the following forms:

```
select 
   <viewname>.<colname> as <alias> |
   <viewname>.* |
   <expr> as <alias> |
     case 
     when <predfunction1()> then <expr1>
      when <predfunction2()> then <expr2>...
     when <predfunctionn()> 
      then <exprn>
     [else <expr\_default>]
      as <name>
```

### Description

-   `<viewname\>.<colname\> as <alias\>`

    -   `<viewname\>`

        Specifies the view from which to select columns.

    -   `<colname\>`

        Specifies the column in that view.

    -   `<alias\>`

        Specifies the name by which the selected field is known. This field is an optional field. It is selected to be a part of each output tuple. If `<alias\>` is not specified, the name of the column is by default the `<colname\>`. Can be a simple identifier or a double-quoted identifier.

-   `<viewname\>.*`

    Specifies the name of a view. This syntax indicates that all columns of the specified view must be carried forward to the enclosing `select` or `extract` statement.

    Like SQL, AQL allows the shorthand `select *` statement. The effect of this statement is to select all columns from all inputs that are specified in the `from` clause of the `select` statement. However, the shorthand extract \* statement is not supported.

-   `<expr\> as <alias\>`

    This represents the assignment of an expression to an attribute of the encompassing view.

    -   `<expr\>`

        Specifies an expression that is composed of scalar function calls, aggregate function calls, or a constant.

    -   `<name\>`

        Represents the name of the column that holds the result of the expression that is specified by `<expr\>` as `<alias\>`. If `<alias\>` is not specified, the name of the column is by default the `<name\>`. Can be a simple identifier or a double-quoted identifier.

-   `when<function1()\> then <expr1\> when <function2()\> then <expr2\> ... when <functionN()\> then <exprn\> [else ] <expr_default\> as <name\>`

    -   `<function1()\>, <function2()\>, <functionN()\>`

        Specify scalar functions that return type Boolean.

    -   `<expr1\>, <expr2\>, <exprn\>, <expr_default\>`

        Specify expressions that are composed of scalar function calls and must return the same type.

    If the result of `<function1()\>` is true, then the result of the `case` expression is the result of `<expr1\>`, and none of the subsequent `when` clauses are evaluated. Otherwise, subsequent `when` clauses \(if any\) are evaluated in the same manner.

    When none of the conditions of the `when` clauses are satisfied, the result of this case expression is the result of the default expression `<expr\_default\>`. This expression is specified in the optional `else` clause. If the `[else]` clause is absent, the result of this `case` expression is `null`.


### Usage notes

-   The following statement is not supported:

    ```
    select * from Document;
    ```

    The contents of the `Document` view might not be fully known in the current context or scope of the .aql file where this `select` statement is issued. The lack of information about the contents is because multiple `require document with columns` statements provided outside of the current .aql file might alter the eventual schema definition of this special `Document` view when it is used at the level of a module. The shorthand Document.\* statement is not a valid AQL construct.

-   You can explicitly select fields from the `Document` view. The following example shows a valid explicit selection of fields from a `Document` view:

    ```
    select D.label as label, 
      D.text as text 
    from Document D;
    ```


### Examples

The following examples illustrate various forms of the select list.

**Example 1: Explicit value assignment using a constant**

This example shows the assignment of a constant value to a view attribute within the select list. The field that is called polarity indicates if the polarity of `PS.match` is positive or negative \(Notice the explicit assignment of a constant value to this attribute\).

```
create view PositiveSentimentsWithPolarity as
select 
  'positive' as polarity, 
  PS.match as sentiment
from 
  PositiveSentiments PS;
```

```
create view NegativeSentimentsWithPolarity as
select 
  'negative' as polarity, 
  NS.match as sentiment
from 
  NegativeSentiments NS;
```

**Example 2: Explicit value assignment using function call**

The following example illustrates how the result of a function call is explicitly assigned to a view attribute within the select list.

```
create view Citizenship as
select 
  P.Name as name, 
  MatchesDict('USCities.dict', P.birthPlace) as isUSCitizen
from 
  Person P;
```

**Example 3: Select list expression from a dictionary extraction**

The following example illustrates how the select list expression can pick values of type Span from a result of dictionary extraction.

```
create view PersonNames as
select N.match as name
from
  (extract
  dictionary 'firstNames.dict' 
  on D.text   
  as match
  from Document D
)N;
```

**Example 4: Examples of case expressions**

This first example shows you how to specify null handling on specific fields:

```
create view School as
select
case
when Not(NotNull(P.education)) then 'Unknown'
else GetString(P.education)
as name
from Person P;
```

This example explains how to classify data:

```
create view Company as
select
PM.name as productname,
case
when ContainsRegex (/IBM/,PM.name) then 'IBM'
when ContainsDict ('OpenSourceDict',PM.name) then 'OSS'
else 'Unknown'
as name
from ProductMatches PM;
```




## The from list

The second part of a `select` or an `extract` statement in AQL is the from list. The from list is a comma-separated list that is the source of the tuples to be selected or extracted.

### Syntax

```
from <from list item> <name>  [, <from list item> <name>]
```

### Description

-   `<from list item\>`

    A view, table, table function reference or nested AQL statement. All nested statements in AQL must be surrounded by parentheses.

-   `<name\>`

    Local name of the `<from list item\>`, that is scoped within the `select` statement or the `extract` statement. A local name can be a simple identifier or a double-quoted identifier. Local names that contain spaces, punctuation characters, or AQL keywords must be enclosed in double quotation marks.


### Examples

**Example 1: A from list with a view and a nested statement**

This example shows a from list that references a view and a nested `extract` statement. The example assigns the result of the statement to the local name `FN`. The example also assigns the outputs of the `LastName` view to the local name `Last Name`.

```
create dictionary LastNamesDict as
  (
    'Anthony', 'Lehman', 'Radcliff'
  );

create view LastName as
  extract dictionary 'LastNamesDict'
  on D.text as lastname 
from Document D;

create view FromList as 
  select * 
    from 
    (extract dictionary 'first.dict' on D.text 
      as firstname from Document D) FN, 
      LastName "Last Name" 
    where Follows(FN.firstname, 
      "Last Name".lastname, 0, 1);
```

The following names are contained in the external dictionary first.dict:

```
#Dictionary for first names
Aaron
Candra
Freeman
Mathew
Matthew
Zoraida
```




## The `where` clause

The optional `where` clause defines a predicate to be applied on each tuple generated from the Cartesian product of all tuples in the relations in the `from` clause.

### Syntax

```
select <select list>
  from <from list>
[where <where clause>]
```

### Description

-   `<where clause\>`

    Specifies one or more predicates. A join occurs when any predicate in a `where` clause involves fields from more than one view that belongs to the `from` list. This predicate must be a conjunction of a set of built-in predicate functions or other user-defined functions that return the data type Boolean:

    ```
    function1() and function2() 
    and ... and functionn()
    ```

    The `where` clause is optional and can be omitted from a `select` statement if there are no predicates to apply.


### Examples

**Example 1: Filter out joined tuples by using a predicate in the WHERE clause**

This example shows a `where` clause that finds only phrases that consist of valid first names that are followed within 0-1 characters by valid last names.

```
-- a view containing words that are valid first names
create view FirstName as
  extract dictionary 'first.dict'
  on D.text as firstname 
from Document D;

-- a view containing words that are valid last names
create view LastName as
  extract dictionary 'last.dict'
  on D.text as lastname 
from Document D;

-- a view containing phrases consisting of valid first names 
-- followed within 0-1 characters by valid last names.
create view FullName as 
  select *
  from
  FirstName FN,
  LastName LN
  where
  Follows (FN.firstname, LN.lastname, 0, 1);
```

The following names are contained in the external dictionary first.dict:

```
#Dictionary for first names
Aaron
Candra
Freeman
Mathew
Matthew
Zoraida
```

The following names are contained in the external dictionary last.dict:

```
#Dictionary for last names
Anthony
Lehman
Radcliff
```




## The `consolidate on` clause

The optional `consolidate on` clause specifies how overlapping spans are resolved across tuples that are output by a `select` or `extract` statement. Tuples with non-overlapping spans are not affected when this clause is used.

### Syntax

The following code is an example of the general structure of this clause:

```
consolidate on <target> 
  [using '<policy>'[ with priority from <priority_column> 
    [ <priority_order> ]]]
```

### Description

-   `<target\>`

    Specifies a column in a view in the `from` clause, or an expression that is composed of scalar function calls involving columns of views that are specified in the `from` clause as arguments.

-   `'<policy\>'`

    Specifies one of the following consolidation policies that is supported by Text Analytics:

    -   **ContainedWithin**

        This policy is the default. If spans A and B overlap, and A completely contains B, this policy then removes the tuple that contains span B from the output. If A and B are the same, then it removes one of them. The choice of which tuple to remove is arbitrary.

    -   **NotContainedWithin**

        If spans A and B overlap, and A completely contains B, this policy then removes the span A from the output. If A and B are the same, then it removes one of them. The choice of which tuple to remove is arbitrary.

    -   **ContainsButNotEqual**

        This policy is the same as ContainedWithin, except that the spans that are exactly equal are retained.

    -   **ExactMatch**

        If a set of spans covers the same region of text, this policy returns exactly one of them. All other spans are left untouched.

    -   **LeftToRight**

        This policy processes the spans in order from left to right. When overlap occurs, it retains the leftmost, longest, non-overlapping span. This policy emulates the overlap-handling policy of most regular expression engines.

-   `<priority\_column\>`

    Specifies a column of type Text, String, Integer, or Float. Can be specified only with the `LeftToRight` consolidation policy.

-   `<priority\_order\>`

    Specifies either ascending or descending order. Can be specified only with the `LeftToRight` consolidation policy. The ascending order ensures that if a tuple T1 has priority 1 and a tuple T2 has priority 2, T1 has a higher priority than T2. By contrast, if the priority order is descending, T2 has a higher priority. The default value of the priority order is ascending.


### Usage notes

-   When the priority clause is present, the semantics of consolidation follow this order:
    -   Process spans from left to right, and when spans overlap, retain the leftmost spans.
    -   If you have multiple overlapping spans that start at the same offset, retain the ones with the highest priority according to the priority order.
    -   Break remaining ties by retaining the longest spans among those spans with the same priority.
-   Consolidate treats nulls as identical. All inputs with a null `<consolidate target\>` result in a single output tuple, which is chosen randomly among those inputs. This behavior is similar to how tuples are consolidated with an identical span in the target column. The exception to resulting in a single output tuple is if the policy is ContainsButNotEqual. In that case, the null `<consolidate target\>` outputs all inputs with null consolidate target.

### Examples

**Example 1: Consolidate on single column**

This example directs the system to examine the field `Person.name` of all output tuples and to use the `ContainedWithin` consolidation policy to resolve overlap.

```
consolidate on Person.name 
  using 'ContainedWithin'
```

**Example 2: Consolidate on expression, involving multiple columns**

This example directs the system to examine the result of applying the `CombineSpans` scalar function to fields `Person.firstname` and `Person.lastname` in each output tuple. It resolves overlap by using the`ContainedWithin` consolidation policy.

```
consolidate on 
  CombineSpans(Person.firstname, Person.lastname) 
  using 'ContainedWithin'
```

**Example 3: Consolidate by using `LeftToRight` policy and priority order**

Suppose that the following Term tuples are extracted from the input text John Doe:

```
match: `John`,
priority: `1`
```

and

```
match: `John Doe`, 
priority: `2`
```

Both spans have the same begin offset. When you consolidate by using the `LeftToRight` policy for ascending priority order, the tuple \(`match: John, priority: 1`\) is retained because it has the higher priority. When you consolidate by using the descending priority order, the tuple \(`match: John Doe, priority: 2`\) is retained. For example:

```
create view ConsolidatePeopleWithPrioritiesAscending as
  select P.match as match, P.weight as weight
  from People P
  consolidate on P.match
  using 'LeftToRight'
  with priority from P.weight
  ascending;
```




## The `group by` clause

The optional `group by` clause of a `select` statement directs the runtime component to group tuples that are produced from the same document by common values of a specified field.

### Syntax

```
select <select list>
from <from list>
[where <where clause>]
...
[group by <group by list>] 
```

### Description

-   `<group by list\>`

    Specifies a comma-delimited list of expressions that involves columns of the views in the `from` clause and scalar function calls. When you apply the `group by` clause, each group of tuples that shares common values for all `group by` expressions produces a single output tuple that is representative for the entire group.

    A field or expression that does not appear in the `group by` clause cannot appear in the select list, unless it is used in an aggregate function call. The order of expressions in the list does not matter.

    The `group by` clause treats all nulls as identical. `Group by` on a column with null values results in a single group.


### Examples

**Example 1: Computing aggregate values**

Use the `group by` clause to compute aggregate values. This example counts the number of occurrences of each first name in the document. In this example, `Count` is an aggregate function.

```
create view SampleView as 
  select 
    GetText(P.firstname) as name, 
    Count(GetText(P.firstname)) as occurrences 
  from 
    (extract 
    dictionary 'first.dict'
    on D.text as firstname
    from Document D
    ) P
  group by GetText(P.firstname);
```

In this case, `first.dict` is an external dictionary that contains the following entries:

```
#Dictionary for first names
Aaron
Candra
Freeman
Matthew
Zoraida
```

The following steps describe semantics of this statement:

1.  Group tuples that are produced by the subquery in the `from` clause by the text content of their `firstname` field.
2.  For each group, count the number of tuples with a non-null `firstname` value. Produce a single output tuple for each such group, with two values, the name and the number of tuples in that group.

**Example 2: Issues with grouping dissimilar fields**

This example illustrates a statement that is not valid.

```
select GetText(P.firstname) as first, 
  GetText(P.lastname) as last, 
  Count(P.firstname) as occurrences
from Person P
group by GetText(P.firstname);
```

The inclusion of `GetText(P.lastname)` in the select list is not accepted, since tuples with the same `firstname` values might have different `lastname` values, which leads to ambiguity.




## The `order by` clause

The optional `order by` clause directs the runtime component to order the output tuples that are produced by the select statement from each document based on the values of the order by list, which is a comma-delimited set of expressions

### Syntax

```
select ... 
  [order by <order by list>]
```

### Description

-   `<order by list\>`

    Specifies a comma-delimited list of expressions.

    The order is based on the values of a comma-delimited list of expressions. The order by clause supports expressions that return numeric \(Integer or Float\), Text, or Span data types. If an expression in the `order by` clause returns a type Span, the result tuples are compared by comparing the relevant span values. In the following example, the span values of the `person` field are compared.

    ```
    order by P.person
    
    ```

    The `order by` clause treats nulls as unordered \(amongst themselves\). Nulls are ordered lower than other objects.


### Examples

**Example 1: Order by multiple expressions**

Assume that person is a field of type Span. The following `order by` clause specifies that the statement returns tuples within each document. They are ordered lexicographically by the text of the person field and then by the beginning of the person field.

```
order by GetText(P.person), GetBegin(P.person)
```

## The `limit` clause

The optional `limit` clause specifies a limit on the number of output tuples that are produced by the select statement for a document.

### Syntax

```
select <select list>
  from <from list>
  ...
  [limit <maximum number of output tuples for each document>];
```

### Description

-   `<maximum number of output tuples for each document\>`

    Specifies the maximum number of output tuples for each document. If the limit value is greater than or equal to the total number of tuples that could be returned, all of the tuples are returned.


### Examples

**Example 1: Limiting the number of returns**

This example returns the first three person names in each document:

```
create view SampleView as 
  select * 
  from Person P
  order by GetBegin(P.name)
  limit 3;
```




## The `select... into` statement

The `select ... into` statement is useful for defining a view and specifying that it is an output view in a single statement.

### Syntax

```
select <select list>
into <output view name>
from <from list>
[where <where clause>]
[consolidate on <column> [using '<policy>' [with priority from <column> [priority order]]]]
[group by <group by list>]
[order by <order by list>]
[limit <maximum number of output tuples for each document>];
```

### Description

-   `<output view name\>`

    Specifies the name of the output view that is defined by the statement. The `select ... into` statement is identical to the `select` statement, except for the additional `into <output view name\>` clause.


### Examples

**Example 1: Defining a view**

This example defines a view that is called `PersonPhone` and also specifies this view as an output view.

```
select P.name as name, 
  Ph.number as phoneNumber 
into PersonPhone 
from Person P, Phone Ph;
```

This example is equivalent to the following two statements:

```
create view PersonPhone as
  select P.name as name, 
    Ph.number as phoneNumber 
  from Person P, Phone Ph;

output view PersonPhone;
```


## The `detag` statement

The `detag` statement in AQL provides the function to detag or remove all the markup from HTML or XML documents before you run AQL extractors.

The `detag` statement can also retain the original locations of and any values that are stored in these tags. When a `detag` statement removes tags from a document, the runtime component remembers the mapping between offsets from the detagged text and the original markup source. The `Remap` function, a special built-in function that maps spans from the detagged text back to their equivalent spans from the original source.

### Syntax

```
detag <input view name>.<text column>
 as <output view name>
[detect content_type (always|never)]
[annotate
 element '<element name>' as <auxiliary view name>
 [with attribute '<attribute name>' as <column name>]
 [and attribute '<attribute name>' as <column name>]
 [, element ...]];
```

### Description

-   `<input view name\>.<text column\>`

    -   `<input view name\>`

        Specifies the name of the input view on which to do the detag process. The `<input view name\>` can be a simple identifier or a double-quoted identifier.

    -   `<text column\>`

        Specifies the text field of the input view on which to do the detag process. The `<text column\>` can be a simple identifier or a double-quoted identifier.

-   `<output view name\>`

    Specifies the name of the output view that contains the detagged text. The output view contains a single column that is called **text**, which holds the detagged text. The `<output view name\>` can be a simple identifier or a double-quoted identifier.

-   `always|never`

    Specifies whether to verify that the contents are HTML or XML before the `detag` statement is processed. When you run non-HTML and non-XML text through a detagger, problems can occur if the text contains XML special characters such as `<`, `>`, or `&`. If the `detect content_type` clause is missing, the default value is always and the system always detects content.

    -   `always`

        Specifies that verification always occurs before the operation is attempted to avoid problems with parsing documents that are not HTML or XML. If the value of the `<text column\>` does not appear to contain a markup, the system skips detagging for the current document.

    -   `never`

        Specifies that verification never occurs before the detag operation is attempted. The system attempts to detag the target text, even if the text does not contain any HTML or XML content.

-   `<element name\>`

    Specifies the name of the HTML or XML element to be annotated. The optional `annotate` clause can direct the runtime component to remember information about the removed tags by creating one or more views.

-   `<auxiliary view name\>`

    Specifies the name of the view that is created to hold the original tags and their attributes. Can be a simple identifier or a double-quoted identifier.

-   `<attribute name\>`

    Name of an attribute of the HTML or XML element.

-   `<column name\>`

    The name of the column in the `<auxiliary view name\>` that is used to store the values of `<attribute name\>`. Can be a simple identifier or a double-quoted identifier.


### Examples

**Example 1: Specifying the detag output view and an auxiliary view**

In this example, the `DetaggedDoc` view is created to hold the detagged version of the original text in the `text` attribute of the view `Document`. In addition to creating a `DetaggedDoc` view, the annotate clause creates an auxiliary view called `Anchor`. This auxiliary view has two columns. One column, called **match**, contains the anchor text. The other column, called **linkTarget**, contains the actual target of the link as text. The spans in the match column are over the text value of the `DetaggedDoc` view.

```
detag Document.text as DetaggedDoc 
annotate 
  'a' as Anchor 
  with attribute 'href' as linkTarget;
```

**Example 2: Using the `Remap` function**

The following example illustrates how the `Remap` function is used to map spans from the detagged text back to their equivalents in the original source.

```
-- Strip out tags from each document, provided that the document
-- is in HTML or XML format.
-- Remember the locations and content of all <A> and <META> tags
-- in the original source document.
detag Document.text as DetaggedDoc
detect content_type always
annotate 
  element 'a' as Anchor
    with attribute 'href' as target,
  element 'meta' as Meta
    with attribute 'name' as name
    and attribute 'content' as content;

output view DetaggedDoc;

-- Create a view containing all lists of keywords in the 
-- document's META tags.
create view MetaKeywordsLists as
select M.content as list 
from Meta M
where MatchesRegex(/keywords/, 'CASE_INSENSITIVE', M.name)
  and NotNull(M.content);

-- Create a dictionary of "interesting" web sites
create dictionary InterestingSitesDict as
(
  'ibm.com', 'slashdot.org'
);

-- Create a view containing all anchor tags whose targets contain 
-- a match of the "interesting sites" dictionary.
create view InterestingLinks as
select A.match as anchortext, A.target as href
from Anchor A
where ContainsDict('InterestingSitesDict', A.target);

-- Find all capitalized words in the anchor text of links to
-- "interesting" web sites.
create view InterestingWords as
extract I.href as href,
  regex /[A-Z][a-z]+/ on 1 token in I.anchortext as word
from InterestingLinks I;

-- Map spans in the InterestingWords view back to the original
-- HTML or XML source of the document.
create view InterestingWordsHTML as
select I.href as href, Remap(I.word) as word
from InterestingWords I;
```


### Documenting the `detag` statement with AQL Doc

The AQL Doc comment for a `detag` statement contains the following information:

-   General description about the function of the statement.
-   @field for each text field of the input view on which to do the detag process.
-   @auxView specifies the view name.
-   @auxViewField specifies the fully qualified column name of the view.

```
/**
* Detags the input document
* @field text the detagged text of the document
* @auxView Anchor stores the anchor points from tagged doc
* @auxViewField Anchor.linkTarget stores the href attribute of anchor tag
*/

detag Document.text as DetaggedDoc
  annotate element 'a' as Anchor
  with attribute 'href' as linkTarget;
```

## The `create dictionary` and `create external dictionary` statements

The `create dictionary` and `create external dictionary` statements are used to define dictionaries of words or phrases to identify matching terms across input text through extract statements or predicate functions. The `create dictionary` statement allows the specification of dictionary content in source AQL code, and the dictionary content is serialized inside the compiled representation of the module \(the .tam file\). The `create external dictionary` statement allows you to specify the dictionary content when the extractor is instantiated, instead of in source AQL code, and you do not have to recompile the module. Therefore, external dictionaries are powerful constructs that allow the AQL developer to expose customization points in a compiled module.

Dictionaries can be created from three sources:

-   Dictionary files
-   Inline dictionary declarations
-   Tables that are created with the `create table` statement and the `create external table` statement.

### Syntax

The internal create dictionary statement has three syntactical forms, `from file`, `from table`, and an inline format.

-   **Internal dictionary**

    From file:

    ```
    create dictionary <dictionary name> 
      
     from file '<file name>' 
     [with language as '<language code(s)>']
     [and case (exact | insensitive)]
     [and lemma_match];
    ```

    From table:

    ```
    create dictionary <dictionary name> 
      
      from table <table name> 
      with entries from <column name>
      [and language as '<language code(s)>']
      [and case (exact | insensitive)]
      [and lemma_match];
    ```

    Inline format

    ```
    create dictionary <dictionary name>
    [with language as '<language code(s)>']
    [and case (exact | insensitive)]
    [and lemma_match]
     as
        (
        '<entry 1>', '<entry 2>', ... , '<entry n>'
        ) 
    ;  
    ```

-   **External dictionary**

    ```
    create external dictionary <dictionary-name>
    required [true|false] 
    [with language as '<language codes\>'] 
    [and case (exact | insensitive )]
    [and lemma_match]; 
    ```


### Description

-   `<dictionary name\>`

    Specifies a name for the new internal or external dictionary. Can be a simple identifier or double-quoted identifier.

-   `'<file name\>'`

    Specifies the name of the file that contains dictionary entries. Dictionary files are carriage-return-delimited text files with one dictionary entry per line. Entries in a dictionary file can consist of multiple tokens.

-   `<table name\>`

    Specifies the name of the table from which to add dictionary entries. Dictionaries cannot be created from a table that is imported from another module.

-   `<column name\>`

    Specifies the name of the column in the table from which to add dictionary entries.

-   `required [true|false]`

    Specifies whether external content for the external dictionary is required to run the module.

    -   `true`

        If the clause is `required true`, you must supply a URI to the location of the file that contains the external content. The specified file must contain content. If the URI is not supplied, or if the file does not contain content, the runtime component throws an exception.

    -   `false`

        If the clause is `required false`, the module can be run successfully even if a URI to the external content is not supplied for this dictionary. If a URI is not supplied, the runtime component treats it as an empty dictionary.

    **Note:** The use of `create external dictionary <dictionary-name\> allow_empty` is now deprecated and results in a compiler warning.

-   `'<language code(s)\>'`

    Specifies a comma-delimited list of two-letter language codes, such as en \(English\) or zh \(Chinese\) for the languages, or for the document languages for external dictionaries, on which to evaluate the dictionary. The dictionary produces no results on documents whose language code is not contained in this string.

    If the language parameter is omitted, the dictionary language defaults to one of the following language sets:

    -   The language sets that are specified through the `set default language` statement, if it is declared, in the containing module.
    -   The language sets that contain German \(de\), Spanish \(es\), English \(en\), French \(fr\), Italian \(it\), and the unspecified language \(x\_unspecified\).
    
-   `lemma_match`

    Use lemmatization to find matches for similar words to a dictionary term in your documents.

    Lemmatization is the process of determining the lemma for a given word. A lemma is a word that can be used as a match for a single given term. For example, the term “go” can be matched to the terms “goes”, “going”, “gone”, or “went”. This process involves complex tasks such as understanding context and determining the part of speech of a word in a sentence. Lemmatization is available for all languages for which IBM Multilingual tokenizer provides part-of-speech support.

    Lemma match is performed only for dictionaries declared with the `lemma match` clause.

    The semantics for dictionary extraction with the `lemma_match` clause are as follows:

    -   The lemmatized form for each token of the input document is computed.
    -   The dictionary is evaluated against the lemmatized document.
    **Restriction:** You cannot use the `lemma_match` option with the `case exact` option. If both are used, a compiler error is returned.

-   `case (exact | insensitive)`

    Specifies the type of case-folding that the dictionary performs when it determines whether a specific region of the document matches.

    -   `exact`

        Specifies an exact case-sensitive match.

    -   `insensitive`

        Specifies a match that is not case-sensitive match. This option is the default value.

-   `'<entry 1\>', '<entry 2\>', ... , '<entry n\>'`

    Specifies the strings that you want to include in the inline dictionary. Entries in an inline dictionary can consist of one or more tokens.


### Usage notes

-   The `from file` and `from table` formats are recommended, especially when you anticipate modifying the entries, or when you have many entries. By using these formats, you can modify the contents of the dictionary without modifying the code.
-   When the `create dictionary` statement is processed by the modular AQL compiler, references to dictionary file locations specified in the `create dictionary ... from file` syntax must be relative to the root of the module in which this `create dictionary` statement is issued.
-   You can specify comments in a dictionary file by preceding the comment with the character `#`. Comments can start anywhere in a line.
-   If you want to specify comments that span multiple lines, you must precede each line with the comment character. If the comment character is part of a dictionary entry, you must escape it using the backslash character \(\\\), as in `\#`. If the backslash character is part of the dictionary entry, it must be escaped with itself, as in `\\`.
-   For external dictionaries, when modules are being loaded, you must specify a list of URIs to external dictionaries, as required by the modules that are being loaded.

-   **Lemmatization of dictionaries**: The primary difference between the existing dictionary matching semantics and the lemmatized semantics is that the match is performed against the lemmatized form of the document, instead of the original form of the document.

    There are additional prerequisites on the format of dictionary entries that belong to dictionary that has lemma match enabled.

    -   A dictionary entry can contain one or more tokens, where each entry token is a lemma. To create a dictionary of lemmas, you can use the [GetLemma scalar function.
    -   The tokens of a dictionary entry should be separated by a white space. If the token consists of white spaces, then the white spaces should be escaped by using the backslash \( \\\) character.

-   The following table shows the differences between the `create external dictionary` statement and the `create dictionary` statement:

|`create external dictionary`|`create dictionary`|
|----------------------------|-------------------|
|<ul><li>Defines a placeholder for a dictionary whose content is supplied at initialization time.</li></ul>|<ul><li>Requires that the content of the dictionary is available at compile time.</li><li>Serialized in the compiled representation \(.tam\) of a module.</li></ul>|


### Examples

**Example 1: Creating an external dictionary**

The external dictionary, PersonPositiveClues, expects to be populated with values from an external file at load-time. It also expects to be matched against some Western languages as specified by its flags.

```
module PersonModuleEnglish;

create external dictionary PersonPositiveClues
  allow_empty false
  with case exact;

export dictionary PersonPositiveClues;
```

**Example 2: Lemmatization**

Consider a dictionary that has lemma match enabled and contains two entries: go shop and went shopping. The document contains the text `Anna went shopping`. The lemmatized form of the input document is `Anna go shop`. Lemma match will return went shopping as a match for the entry go shop. The original document text is not compared to the dictionary entries, only the lemmatized document text. Therefore, there are no matches in the document for the entry `went shopping`.


### Documenting the `create dictionary` and `create external dictionary` statements with AQL Doc

The AQL Doc comment for a `create dictionary` statement contains the following information:

General description about the dictionary.

```
/**
* A dictionary of terms used to greet people.
* 
*/

create dictionary GreetingDict as
(
  'regards', 'regds', 'hello', 'hi', 'thanks', 'best', 'subj', 'to', 'from'
);
```

The AQL Doc comment for a `create external dictionary` statement contains the general description about the dictionary that is created. The following string illustrates the format:

```
/**
 * Customizable dictionary of first names.
 * Evaluated on English, French, Italian, German, Portuguese, Spanish text.  
 */
create external dictionary CustomFirstNames_WesternEurope
  allow_empty true;
```

## The `create table` statement

The `create table` statement creates an AQL table.

The `create table` statement in AQL is used to define static lookup tables to augment annotations with more information.

### Syntax

```
create table <table name> (
    <colname> <type> [,  <colname> <type>]* )
 as values 
    ( <value> [, <value>]*),
    ...
    ( <value> [, <value>]*);
```

### Description

-   `<table name\>`

    Specifies the name of the table to create. The `<table name\>` can be a simple identifier or a double-quoted identifier.

-   `<colname\>`

    Specifies the name of the column to create.

-   `<type\>`

    Specifies the AQL data type for the associated column. All columns must be of type Text , Integer, Float or Boolean.

-   `<value\>`

    Specifies the tuples to be populated in the created table.


### Examples

**Example 1: Creating a table of company names**

In this example, the `create table` statement adds more location metadata to company name annotations:

```
-- Create a dictionary of company names
create dictionary CompanyNames as
  ('IBM', 'BigCorp', 'Initech');

-- Find all matches of the company names dictionary.
create view Company as
  extract
    dictionary 'CompanyNames' on D.text as company
  from Document D;


-- Create a table that maps company names to locations of 
-- corporate headquarters.
create table NameToLocation 
  (name Text, location Text) as
  values 
  ('IBM', 'USA'), 
  ('BigCorp', 'Apex'), 
  ('Initech', 'Dallas'),
  ('Acme Fake Company Names', 'Somewhere');

-- Use the table to augment the Company view with location
-- information.
create view CompanyLoc as
  select N2C.location as loc, 
          C.company as company
  from Company C, NameToLocation N2C
  where Equals(GetText(C.company), GetText(N2C.name));

output view CompanyLoc;
```


### Documenting the `create table` statement with AQL Doc

The AQL Doc comment for a `create table` statement contains the following information:

-   General description about the table.
-   @field for every column name in the schema of this table.

```
/** Create a table that maps company names to locations 
/** of corporate headquarters.
* @field name name of the company
* @field location location of corporate headquarters
*/

create table NameToLocation 
  (name Text, location Text) as
 values 
  ('IBM', 'USA'), 
  ('Enron', 'UK'), 
  ('Initech', 'Dallas'),
  ('Acme Fake Company Names', 'Somewhere');
```

## The `create external table` statement

You can use the `create external table` statement to specify a table with established content when a compiled module is run across all input documents. You supply the table content during load time instead of in the source AQL code, and you do not have to recompile the module.

External tables are powerful constructs that allow the AQL developer to expose customization points in a compiled module.

### Syntax

```
create external table <table-name\>
  (<colname\> <type\> 
   [,  <colname\> <type\>]* )  
   allow_empty <true|false>;
```

### Description

-   `<table-name\>`

    Specifies name of the external table to create. The `<table-name\>` can be a simple identifier or a double-quoted identifier.

-   `<colname\>`

    Specifies the name of the column to create.

-   `<type\>`

    Specifies the AQL data type for the associated column. All columns must be of type Text , Integer, Float or Boolean.

-   `[, <colname\> <type\>]*`

    Specifies additional columns and AQL objects to be used in the external table.

-   `allow_empty [true|false]`

    Specifies the value for the `allow_empty` clause.

    -   `true`

        If the clause is `allow_empty true`, the module can be run successfully even if a URI to the external content is not supplied for this table. If the URI is not supplied, the runtime component treats it as an empty table.

    -   `false`

        If the clause is `allow_empty false`, then you must supply a URI to the location of the file that contains the external content. The specified file must contain content. If the URI is not supplied, or if the file does not contain content, the runtime component throws an exception.


### Usage notes

-   The compiled representation of the module contains metadata about the external objects \(views, dictionaries, and tables\) that the module defines.
-   When modules are being loaded, you must specify a list of URIs to external tables, as required by the modules that are being loaded.
-   The supported format for the content of an external table is one CSV \( .csv\) file with header.

The following table shows the differences between the `create external table` statement and the `create table` statement:

|`create external table`|`create table`|
|-----------------------|--------------|
|<ul><li>Defines a placeholder for a table whose content is supplied at initialization time.</li></ul>|<ul><li>Requires that the content of the table is available at compile time.</li><li>Serialized in the compiled representation \(.tam\) of a module.</li></ul>|

### Examples

**Example 1: Creating an external table that is populated at load time**

The external table, PersonNegativeClues, expects to be populated at load-time because of the flag, `allow_empty false`.

```
module PersonModuleFrench;

create external table PersonNegativeClues (name Text)
  allow_empty false;

export table PersonNegativeClues;

```

**Example 2: Creating a dictionary with an external table**

Dictionaries can also be created from external tables, similar to being created from inline tables that are declared with the `create table` statement.

```
create external table Product (nickName Text, formalName Text)
allow_empty false;

/**
  * Dictionary of product nicknames, from the nickName field 
  * of the customizable external table Product.
  */
create dictionary ProductDict 
from table Product 
with entries from nickName;
```


### Documenting the `create external table` statement with AQL Doc

The AQL Doc comment for a `create external table` statement contains the following information:

-   General description about the table.
-   @field for every column name in the schema of this table.

```
/** Create a table that maps company names to locations of corporate headquarters.
* @field name name of the company
* @field location location of corporate headquarters
*/
create external table Company2Location
  (name Text, location Text)
   allow_empty false;
```

## The `create external view` statement

The `create external view` statement in AQL allows specification of more metadata about a document as a new view, in addition to the predefined `Document` view that holds the textual and label content.

### Syntax

```
create external view <view_name> (
        <colname> <type> [, <colname> <type>]*
        )
external_name '<view_external_name>';
```

### Description

-   `<view_name\>`

    Specifies the internal name of the external view. The external view is referred by this name in the AQL rules. A `<view_name\>` can be a simple identifier or a double-quoted identifier. A `<view_name\>` cannot contain the period character.

-   `<colname\>`

    Specifies the name of the column to define in the external view.

-   `<type\>`

    Specifies the data type for the associated column. The data types that are supported for external view columns are Text, Span, Integer, and Float.

-   `'<view_external_name\>'`

    Specifies the external name of the external view. External systems that populate tuples into the external view refer to the external view by the external name. The `'<view_external_name\>'` must be a String constant encased in single quotation marks \('ExternalName'\).


### Examples

To illustrate external views, consider an example application that requires that you identify the names of persons in email messages.

**Example 1: Identifying the names of persons in email messages**

Assume that the text of an email message is "Ena, please send me the document ASAP". While a human might be able to understand that Ena is a name of a person based on the text of the email, AQL rules that are written to identify names of persons with high-precision from general text might be too conservative and not able to draw the same conclusion with high confidence, based on the fact that Ena is a capitalized word.

One way to boost the coverage of the rules is to use words from the **From**, **To**, and **CC** fields of the email as more evidence.

If the email is addressed to "Ena Smith," and the application makes this information available to the extractor, then the extractor developer can write more AQL rules to boost the coverage of the extractor that is based on the domain knowledge that emails are usually addressed to people.

For example, you can write AQL rules to identify person tokens from the email metadata fields. You then use that information as strong clues when you decide whether a capitalized token in the email text is a person name. In general, the email metadata is not part of the actual email message, but the application can make this metadata available to the extractor by using an external view.

This means that at run time, for each email that must be processed, the application can pass the email text as document text \(to populate the view `Document`\). It can also pass the extra metadata by using an appropriately defined external view.

The following statement defines an external view that is named `EmailMetadata`. The external view has a schema that contains three fields of type Text. At run time, the view `EmailMetadata` is automatically populated from an external type named `EmailMetadataSrc`. You can then reference the `EmailMetadata` view in your AQL rules, similarly to how you would reference any other view.

```
create external view EmailMetadata 
  (fromAddress Text, toAddress Text, ccAddress Text)   
external_name 'EmailMetadataSrc';
```


### Documenting the `create external view` statement with AQL Doc

The AQL Doc comment for a `create external view` statement contains the following information:

-   General description about the view.
-   @field for every column name in the view.

```
/**
* The external view named EmailMetadata, containing three fields 
* of type Text. At run time, the view EmailMetadata is 
* automatically populated from an external type named 
* EmailMetadataSrc. 
*
* @field from the fromAddress field of the email
* @field to the toAddress field of the email
* @field cc the ccAddress field of the email
*/

create external view EmailMetadata(fromAddress Text, toAddress Text, ccAddress Text)
external_name 'EmailMetadataSrc';
```

## File formats for external artifacts

Three types of external artifacts are supported: external views, external dictionaries, and external tables.

### External dictionary 

The format for the file that contains entries for an external dictionary is defined here:

-   Carriage-return-delimited text file.
-   One dictionary entry per line.
-   Recommended file extension is .dict, but other file extensions can be supported.
-   Entries in the dictionary can consist of multiple tokens.
-   Comments can be specified by preceding the content of the comment with the character, `#`.
-   Comments can start anywhere in a line.
-   Multi-line comments must contain the `#` character at the start of each line.
-   Dictionary entries can contain comment characters, if each comment character is escaped with a backslash character. For example, `\#`.

### External table

The supported file format for the content of an external table is a .csv file with header.

The following example shows a `create external table` statement, and the .csv file that specifies the content of this external table.

```
create external table Company2Location
  (name Text, location Text)
   allow_empty false;
```

The first line of the .csv file contains the header. The remaining lines contain the data.

```
name,location
IBM,USA
Infosys,India
LG,Korea
Vodafone,UK
```

### External view

The content of external views can be specified in the following ways:

-   When you run an extractor, you can specify external view content for a data collection only when you are using the JSON input format.



## Built-in functions

AQL has a collection of built-in functions for use in extraction rules.

-   **Aggregate functions**  
Aggregate functions are used to implement operations \(such as counting, mathematical operations, and other operations\) across a set of input values. These functions return only one result.
-   **Predicate functions**  
Predicate functions test a certain predicate over its input arguments and return a corresponding Boolean value.
-   **Scalar functions**  
Scalar functions perform an operation over the values of a field across a set of input tuples and return a non-Boolean value, such as a Span, Text, or Integer. These functions can be used within the `select` list of a `select` statement or an `extract` statement. They can also be used as inputs to predicate functions.



## Aggregate functions

Aggregate functions are used to implement operations \(such as counting, mathematical operations, and other operations\) across a set of input values. These functions return only one result.

These functions can be used within the `select` list of a `select` statement but not within an `extract` statement.

The following is the general form of an aggregate function call:

```
Aggregate_Function_Name(argument)
```

The `argument` can be:

-   An expression that consists of a column of a view in the `from` clause, or a combination of scalar functions that involve columns of the views in the `from` clause.

    In most cases, except as noted below, null values for argument are ignored.

-   The character `*` in the special case of the `Count(*)` aggregate function.

    In this case, all rows of the output are counted, including null values.


|Aggregate function|Argument type|Return type|Return value|
|------------------|-------------|-----------|------------|
|Avg\(expression\)|Integer, Float|Float|The average of all input values or null if no rows are selected|
|Count\(\*\)| |Integer|The number of all input rows|
|Count\(expression\)|Any|Integer|The number of all non-null input values|
|List\(expression\)|Integer, Float, Text, Span|List of scalar values of the same type as the input argument|An unordered list of non-null input values: a bag, not a set, hence might contain duplicates. An empty list if only null values are selected|
|Max\(expression\)|Integer, Float, Text, Span|Same as the argument type|The maximum element across all input values or null if no rows are selected|
|Min\(expression\)|Integer, Float, Text, Span|Same as the argument type|The minimum element across all input values or null if no rows are selected|
|Sum\(expression\)|Integer, Float|Same as the argument type|The sum of all input values or null if no rows are selected|

**Limitations of the current version:**

The current version of AQL supports the creation of scalar values through the `aggregate` function List.

### Examples

The following example illustrates how aggregate functions can count the number of person name annotations, or compute sets of first names that are associated with each distinct last name identified in a document:

```
-- identify occurrences of first names in the document
create view FirstName as
extract dictionary 'firstNames.dict' on D.text as name
from Document D;

-- identify occurrences of last names in the document
create view LastName as
extract dictionary 'lastNames.dict' on D.text as name
from Document D;
  
-- identify complete person names in the document
create view Person as
select F.name as firstname, L.name as lastname
from FirstName F, LastName L
where FollowsTok(F.name, L.name, 0, 0);

-- count the number of person annotations in the document  
create view CountPerson as
select Count(*)
from Person;

-- for each distinct last name, output a list of first names associated with it in the document
create view FamilyMembers as
select GetText(P.lastname) as lastname, List(GetText(P.firstname)) as firstnames
from Person P
group by GetText(P.lastname);

```

The following example illustrates the use of the Min and Max functions:

```
-- Extract stop words from input text
create view StopWords as
extract 
regex /\s(the|in|a|an|as|to|from)\s/ on D.text as match
from Document D;


-- Count the number of times each stop word matched above, was used in the text
create view StopWordsCount as
select 
GetText(S.match) as stopword,
Count(S.match) as stopwordcount
from StopWords S
group by GetText(S.match);

-- Retrieve the most used and least used stop word count
create view StopWordUsageCount as 
        select Min(S.stopwordcount) as least, Max(S.stopwordcount) as most
from StopWordsCount S; 
```

## Predicate functions

Predicate functions test a certain predicate over its input arguments and return a corresponding Boolean value.

Input arguments to predicate functions include return values of other scalar or aggregate functions in addition to dictionaries, regular expressions, and more. These functions can be employed within the `where` clause of a `select` statement, and the `having` clause of an extract statement.

### And

The `And` function accepts a variable number of Boolean arguments and returns the results of a logical `AND` operation across all the input arguments.

The AQL optimizer does not attempt to optimize the order of evaluation of the arguments to this function as part of the logical `AND` operation. If any input is `null`, the result is `null`.

Consider this query format:

```
select ...
from ...
where And(predicate1, predicate2);
```

As a result, a query format that uses the `AND` operation often runs considerably slower than the same query in the form of:

```
select ...
from ...
where predicate1 and predicate2;
```

When possible, use the SQL-style and keyword instead of this function.

### Contains

The `Contains` function takes two spans as arguments:

```
Contains(<span1>, <span2>)
```

This function returns `TRUE` if `span1` completely contains `span2`. If `span2` starts at or after the beginning of `span1`, and ends at or before the end of `span1`, `span2` is completely contained. If either argument is `null`, the function returns `null`.

### ContainsDict

The `ContainsDict` function checks if the text of a span contains any entry from a given dictionary. This function accepts as input arguments a dictionary, an optional flag specification, and a span to evaluate.

```
ContainsDict('<dictionary>', ['<flags>', ]<span>)
```

The `ContainsDict` function returns `TRUE` if the span contains one or more matches of the dictionary. The flags can be `Exact` or `IgnoreCase`.

-   If `Exact` is used, a case-sensitive match is performed against each term in the dictionary.
-   If `IgnoreCase` is used, the match that is performed against each term in the dictionary is not case-sensitive.
-   If no flag is specified, the dictionary will match based on any flag that was specified when it was created. If no flag was specified during creation, it will match by using the `IgnoreCase` flag.

If the span is `null`, the function returns `null`.

The following example illustrates the use of the `ContainsDict` function:

```
create dictionary EmployeePhoneDict as
(
 '121-222-2346', '121-234-1198', '121-235-8891'
);

create view PhoneNum as
extract regex /(\d{3})-(\d{3}-\d{4})/ 
    on between 4 and 5 tokens in D.text 
    return 
        group 1 as areaCode 
        and group 2 as restOfNumber
        and group 0 as number
from Document D;

create view PhoneNumbers as
select P.number as number  
from PhoneNum P
where ContainsDict('EmployeePhoneDict',P.number);
```

Dictionaries are always evaluated on token boundaries. For example, if a dictionary consists of the term fish, there is no match in the text Let's go fishing!.

### ContainsDicts

The `ContainsDicts` function checks if the text of a span contains any entry from any given dictionaries. This function accepts as input arguments two or more dictionaries, an optional flag specification, and a span to evaluate.

```
ContainsDicts('<dictionary>','<dictionary>','<dictionary>', ['<flags>', ]<span>)
```

The `ContainsDicts` function returns `TRUE` if the span contains one or more matches from at least one of the specified dictionaries. The flags can be `Exact` or `IgnoreCase`.

-   If `Exact` is used, a case-sensitive match is performed against each of the terms in the dictionaries.
-   If `IgnoreCase` is used, the match that is performed against each of the terms in the dictionaries is not case-sensitive.
-   If no flag is specified, the dictionary will match based on any flag that was specified when it was created. If no flag was specified during creation, it will match by using the `IgnoreCase` flag.

If either or both arguments are null, then the function returns `null`.

The following example illustrates the use of the `ContainsDicts` function. Note that the `Exact` flag is used:

```
create view PersonWithFirstName as
select P.reference as reference
from Person P
where ContainsDicts(
'FirstNamesUsedGlobally',
'FirstNamesUsedInGermanyLong',
'NickNamesUsedGlobally',
'FirstNamesUsedInGermanyShort',
'FirstNamesUsedInItaly',
'FirstNamesUsedInFrance',
'Exact',
P.reference);
```

### ContainsRegex

The `ContainsRegex` function checks whether the text of a span matches a given regular expression. This function accepts a regular expression with which to match, an optional flag specification, and the input span against which to match.

```
ContainsRegex(/<regular expression>/, ['<flags>', ]<span>)
```

The function returns `TRUE` if the text of the span, which is taken as a separate Java™ string, contains one or more matches of the regular expression. The function returns `null` if the span is `null`. The optional flags affect the matching behavior, similarly to flags used in Java regular expressions.

The flags string is formed by combining one or more of the following flags by using `|` as the separator:

-   CANON\_EQ
-   CASE\_INSENSITIVE
-   DOTALL
-   LITERAL
-   MULTILINE
-   UNICODE \(meaningless without CASE\_INSENSITIVE\)
-   UNIX\_LINES

An example of a flags string is

```
'UNICODE | CASE_INSENSITIVE'
```


Consider this example where `ContainsRegex` identifies product names along with their version number mentions on either sides. Unlike the example for `MatchesRegex`, a version number match is not strictly identified by using the `regex`, but by the context around a product name mention containing a token that matches against the `regex`.

```

-- dictionary of product names
create dictionary ProductNamesDict as
(
  'IBM WebSphere Application Server',
  'Microsoft Windows',
  'Apple Mac OS',
  'IBM Rational Application Developer',
  'Apache HTTP Server',
  'Eclipse',
  'Google Android'
);

-- extract product names from input text
create view ProductNames as
extract 
  dictionary 'ProductNamesDict' 
  on D.text as name
from Document D;

-- gather context around product name mention
create view ProductNamesWithContext as
select
  P.name as name,
  LeftContext(P.name, 5) as leftctxt,
  RightContext(P.name, 5) as rightctxt
from ProductNames P;

-- use a regex to identify products with version number mentions on either sides of the product mention
create view ProductsWithVersionNumbers as
(
  select 
    P.name as productname,
    P.leftctxt as productversion
  from ProductNamesWithContext P
  where ContainsRegex (/v\d((\.\d)+)?/, P.leftctxt)
)
union all
(
  select 
    P.name as productname,
    P.rightctxt as productversion
  from ProductNamesWithContext P
  where ContainsRegex (/v\d((\.\d)+)?/, P.rightctxt)
);
```

### Equals

The `Equals` function takes two arguments of arbitrary type:

```
Equals(<arg1>, <arg2>)
```

Two spans are considered equal if they both begin and end at the same offsets and contain the same text. If either or both arguments are null, the function returns `null`.

The following example illustrates the use of the `Equals` function.

```
-- Select phone number spans whose text is equal to 001-543-2217
create view PhoneNumber as
select P.number as number 
from PhoneNum P 
where Equals('001-543-2217',GetText(P.number));
```

### Follows

The `Follows` predicate function takes two span arguments and two integer arguments:

```
Follows(<span1>, <span2>, <minchar>, <maxchar>)
```

The function returns `TRUE` if the number of characters between the end of `span1` and the beginning of `span2` is between `minchar` and `maxchar`, inclusive. If any argument is `null`, the function returns `null`.

### FollowsTok

The `FollowsTok` predicate function is a version of `Follows`; however, the `FollowsTok` distance arguments are in terms of tokens instead of characters:

```
FollowsTok(<span1>, <span2>, <mintok>, <maxtok>)
```

The `FollowsTok` function returns `TRUE` if the number of tokens between the end of `span1` and the beginning of `span2` is between `mintok` and `maxtok`, inclusive. If any argument is `null`, the function returns `null`.

### GreaterThan

The `GreaterThan` predicate function takes two arguments of arbitrary type:

```
GreaterThan(<arg1>, <arg2>)
```

The function returns `TRUE` if `<arg1>` is greater than `<arg2>`. The function returns `FALSE` is either argument is `null`.

### IsNull

The `IsNull` function tests whether data is, or is not, null. It takes a single argument of any type and returns `TRUE` if the single argument is `null`, and `FALSE` otherwise. Note that the behavior of this predicate and the already defined `NotNull` predicate is different from all other predicates that return null on null input.

### MatchesDict

The `MatchesDict` function takes a dictionary \(as in a dictionary extraction\), an optional flag specification, and a span as arguments:

```
MatchesDict('<dictionary>', ['<flags>', ]<span>)
```

The `MatchesDict` function returns `TRUE` if the span exactly matches one or more of the terms in the dictionary. The flags can be `Exact` or `IgnoreCase`.

-   If `Exact` is used, a case-sensitive match is performed against each term in the dictionary.
-   If `IgnoreCase` is used, the match that is performed against each term in the dictionary is not case-sensitive.
-   If no flag is specified, the dictionary will match based on any flag that was specified when it was created. If no flag was specified during creation, it will match by using the `IgnoreCase` flag.

If any argument is `null`, the function returns `null`.

Dictionaries are always evaluated on token boundaries. For example, if a dictionary consists of the term fish, there is no match in the text Let's go fishing!.

### MatchesRegex

The `MatchesRegex` function has a similar syntax to `ContainsRegex`. Unlike `ContainsRegex` function, the `MatchesRegex` function returns `TRUE` only if the entire text of the span, taken as a separate Java string, matches the regular expression. If any argument is `null`, the function returns `null`. The optional flags affect the matching behavior similar to flags used in Java regular expressions.

```
MatchesRegex(/<regular expression>/, ['<flags>', ]<span>)
```

The flags string is formed by combining a subset of these flags by using `|` as the separator:

-   CANON\_EQ
-   CASE\_INSENSITIVE
-   DOTALL
-   LITERAL
-   MULTILINE
-   UNICODE \(meaningless without CASE\_INSENSITIVE\)
-   UNIX\_LINES

An example of a flags string is

```
'UNICODE | CASE_INSENSITIVE'
```


Consider this example where `MatchesRegex` is used to identify product names along with their version number mentions to the right. Unlike the example in `ContainsRegex` section, the exact version number is identified as the token immediately following the product name mention.

```
-- gather right context around product name mention
create view ProductNamesWithContext as
select
  P.name as name,
  RightContext(P.name, 5) as rightctxt
from ProductNames P;

-- use a regex to identify products with version number mentions to the right
create view ProductsWithVersionNumbers as
select 
  P.name as productname,
  P.rightctxt as productversion
from ProductNamesWithContext P
where MatchesRegex (/v\d((\.\d)+)?/, P.rightctxt);
```

### Not

The `Not` function takes a single Boolean argument and returns its complement. If the argument is `null`, the function returns `null`.

### NotNull

The `NotNull` function takes a single argument of any type.

As its name suggests, the `NotNull` function returns `TRUE` if the value of the argument is not null, and `FALSE` if the argument is `null`.

### Or

The `Or` function takes a variable number of non-null Boolean arguments. If any argument is `null`, the function returns `null`.

The `Or` function returns `TRUE` if any of them evaluates to `TRUE`.

### Overlaps

The `Overlaps` function takes two span arguments:

```
Overlaps(<span1>, <span2>)
```

The function returns `TRUE` if the two input spans overlap in the document text. The function returns `null` if either argument is `null`.

## Scalar functions

Scalar functions perform an operation over the values of a field across a set of input tuples and return a non-Boolean value, such as a Span, Text, or Integer. These functions can be used within the `select` list of a `select` statement or an `extract` statement. They can also be used as inputs to predicate functions.

If a Text object is provided where a Span object is required, a converted Span object is automatically generated, which is based on this Text object, with begin and end offsets covering the whole length of the Text object.

If a Span object is provided where a Text object is required, a converted Text object is automatically generated from the text value of the Span object.

### Chomp

The `Chomp` function is similar to the `Chomp` operator in Perl, except that `Chomp` operates over spans instead of strings:

```
Chomp(<span1>)
```

The following example illustrates the use of the `Chomp` function.

```
detag Document.text as DetaggedDoc
annotate
element 'a' as Anchor 
with attribute 'href' as linkTarget;

create view Links as 
select Chomp(A.linkTarget) as link
from Anchor A;
```

If the input span contains any white space at the beginning or end, the `Chomp` function shrinks the span enough to remove the white space. The function then returns a new span with no leading or trailing white space. If the input span has no leading or trailing white space, then the `Chomp` function returns the same span. If the input span is `null`, then Chomp returns `null`.

### CombineSpans

The `CombineSpans` function takes two spans as input and returns the shortest span that completely covers both input spans if the spans are based on the same text object.

```
CombineSpans(['IgnoreOrder',] <span1>, <span2>)
```

The `CombineSpans` function is sensitive to the order of its input spans, unless you use the IgnoreOrder parameter. When the optional IgnoreOrder parameter is used, the order of the two spans is ignored.

The following example illustrates the use of the `CombineSpans` function.

```
create view FullName as
     select
             CombineSpans('IgnoreOrder',F.name, L.name) as fullName
     from
             FirstName F,
             LastName L
     where
             FollowsTok(F.name, L.name, 0,0);
```

The semantics of the function are as follows:

-   If either `span1` or `span2` is `null`, or the two spans are over different Text objects, the function returns `null`.
-   Otherwise, if `span1` is smaller than `span2` or the `IgnoreOrder` parameter is used, the function returns the shortest span that covers both `span1` and `span2`.
-   Otherwise \(`span1` is larger than `span2` and the `IgnoreOrder` is not used\), the function returns a runtime error.

Based on the definition of Span, the different scenarios of arguments to the `CombineSpans` function are as follows:

-   Span 2 is always after span 1. That is, left-to-right order is maintained:

    ```
    CombineSpans([0,7], [3,7]) returns the span [0,7]
    CombineSpans([0,7], [8,10]) returns the span [0,10]
    CombineSpans([0,7], [3,6]) returns the span [0,7]
    CombineSpans([0,7], [0,7]) returns the span [0,7]
    ```

-   Span 2 is not after span 1 i.e. left-to-right order is *not* maintained:

    ```
    CombineSpans(‘IgnoreOrder’, [0,10], [0,7]) returns the span [0,10]
    CombineSpans(‘IgnoreOrder’, [3,6], [0,7]) returns the span [0,7]
    CombineSpans(‘IgnoreOrder’, [3,7], [0,7]) returns the span [0,7]
    CombineSpans(‘IgnoreOrder’, [8,10], [0,7]) returns the span [0,10]
    CombineSpans([3,6], [0,7]) will result in Runtime error as the IgnoreOrder flag has not been specified.
    ```


### GetBegin and GetEnd

The `GetBegin` function takes a single span argument and returns the begin offset of the input span.

For example,

```
GetBegin([5, 10])
```

returns the value `5`.

Likewise, the `GetEnd` function returns the end offset of its input span.

The following example illustrates the use of the `GetBegin` and `GetEnd` function.

```
create view PersonOffsets as 
select GetBegin(P.name) as offsetBegin, GetEnd(P.name) as offsetEnd 
from Person P;
```

For both of these functions, if the argument is `null`, the function returns `null`.

### GetLanguage

The `GetLanguage` function takes a single span argument and returns the two-letter language code of the source text of the span. If the argument is `null`, the function returns `null`.

This statement produces meaningful results only if the data source is tagging text fields with the appropriate languages.

### GetLemma

The `GetLemma` function takes a single Span or Text object as an argument and returns a string that contains the lemmatized form of the input span. If the argument is `null`, the function returns `null`. When preparing dictionary entries for lemma match, this function can determine the lemmatized form of various tokens as returned by the tokenizer. For example, for the span `went shopping` GetLemma returns the lemma string `go shop`.

The results of this function follow these rules:

-   If the input span starts at the beginning of a token and ends at the end of a token, the result will contain the sequence of lemmas that begins with the lemma of the first token, followed by a white space, followed by the lemma of the second token, followed by a white space, and so on \(for example, dog cat fish bird ...\). If the lemma for a token consists of white spaces, escape the white space by using the backslash character \( \\ \).
-   If the input span starts or ends with white space \(for example, it starts between two tokens or ends between two tokens\), the function ignores the beginning and trailing white space.
-   If the input span starts in the middle of a token or ends in the middle of a token, then the output consists of the following content, in this order, separated by a white space:
    -   The surface form of the first partial token if it exists.
    -   The sequence of lemmas that correspond to the first to last complete tokens. If the lemma for any of the complete tokens consists of white spaces, escape the white spaces by using the backslash character \( \\ \).
    -   The surface form of the last partial token if it exists.

This function will return an error if the tokenizer that is being used is not capable of producing lemmas.

You can use the GetLemma\(\) function to create dictionaries of lemmatized forms. Call GetLemma\(\) on an input that contains the terms whose lemmatized form you want to include in the dictionary.

### GetLength

The `GetLength` function takes a single span argument and returns the length of the input span. If the argument is `null`, the function returns `null`.

For example,

```
GetLength([5, 12])
```

returns a value of 7.

### GetLengthTok

The `GetLengthTok` function takes a single span argument and returns the length of the input span in tokens. If the input argument is `null`, the function returns `null`.

### GetString

The `GetString` function takes a single AQL object as its argument and returns a Text object formed from the string representation of the object.

For span and text arguments, the value returned are different from those returned by GetText\(\). For Text objects, the returned value includes single quotes surrounding the text string. For span objects, the returned value includes in addition offsets in brackets.

For scalar lists, this function returns the GetString\(\) values of the elements of the list, concatenated with semicolons. For Integer, Float, Boolean, and String arguments, this function returns the value of the argument as a string. For `null` arguments, this function returns `null`.

### GetText

The `GetText` function takes a single span or text as an argument. For span input, it returns the text object based on the actual text string that the span marks. For text input, it returns the input text object. If the input is `null`, then this function returns `null`. For example:

```
GetText([5, 12])
```

The span returns the substring of the document from character position 5 - 12.

The `GetText` function has two primary uses.

**Testing for string equality between the text marked by two spans.**

```
-- Create a dictionary of company names
create dictionary CompanyNames as
('IBM', 'BigCorp', 'Initech');

-- Find all matches of the company names dictionary.
create view Company as
extract
    dictionary 'CompanyNames' on D.text as company
from Document D;


-- Create a table that maps company names to locations of
-- corporate headquarters.
create table NameToLocation (name Text, location Text) as
values
    ('IBM', 'USA'),
    ('BigCorp', 'Apex'),
    ('Initech', 'Dallas'),
    ('Acme Fake Company Names', 'Somewhere');

-- Use the table to augment the Company view with location
-- information.
create view CompanyLoc as
select N2C.location as loc, C.company as company
from Company C, NameToLocation N2C
where Equals(GetText(C.company), GetText(N2C.name));

output view CompanyLoc;
```

**Splitting a document into smaller subdocuments.** 

For example, if the main document is a blog that consists of multiple blog entries, you can use GetText to create a subdocument for each blog entry.

```
detag Document.text as DetaggedBlog
annotate
    element 'blog' as Blog
    with attribute 'name' as title;


create view BlogEntry as
select B.match as entry, B.title as title
from Blog B;

-- Turn each tuple in the BlogEntry view into a sub-document
create view BlogEntryDoc as
select GetText(B.title) as title, GetText(B.entry) as body
from BlogEntry B;

output view BlogEntryDoc;

--Dictionary for Companies
create dictionary CompanyNameDict as
(
    'A Corporation', 'B Corporation'
);

-- Run an extraction over the sub-documents.
-- The spans that this "extract" statement creates will have
-- offsets relative to the blog entries themselves, as opposed
-- to the original multi-entry document.
create view CompanyName as
extract dictionary 'CompanyNameDict' on B.body as name
from BlogEntryDoc B;

output view CompanyName;
```


### LeftContext and RightContext

The `LeftContext` function takes a Span and an Integer as input:

```
LeftContext(<input span>, <nchars>)
```

The `LeftContext(<input span\>, <nchars\>)` function returns a new span that contains the nchars characters of the document immediately to the left of `<input span\>`. If the input span starts less than `<nchars\>` characters from the beginning of the document, then LeftContext\(\) returns a span that starts at the beginning of the document and continues until the beginning of the input span.

For example, LeftContext\(\[20, 30\], 10\) returns the span \[10, 20\]. The span LeftContext\(\[5, 10\], 10\) returns \[0, 5\].

If the input starts on the first character of the document, LeftContext\(\) returns a zero-length span. Similarly, the `RightContext` function returns the text to the right of its input span. For both functions, if either argument is `null`, the function returns `null`.

### LeftContextTok and RightContextTok

The `LeftContextTok` and `RightContextTok` functions are versions of `LeftContext` and `RightContext` that take distances in terms of tokens:

```
LeftContextTok(<input span>, <num tokens>)
RightContextTok(<input span>, <num tokens>)
```

The following example illustrates the use of the `RightContextTok` function.

```
create view Salutation as
extract 
 regex /Mr\.|Ms\.|Miss/
  on D.text as salutation
  from Document D;

--Select the token immediately following a Salutation span
create view NameCandidate as
select RightContextTok(S.salutation, 1) as name 
from Salutation S;
```

For both functions, if either argument is `null`, the function returns `null`.

### Remap

The `Remap` function takes a single span argument:

```
Remap(<span>)
```

If the input span is over a text object that was produced by transforming another text object , the `Remap` function converts the span into a span over the original "source" text.

For example, if the span `N.name` is over a detagged document that is produced by running HTML through the AQL `detag` statement, then

```
Remap(<N.name>)
```

returns an equivalent span over the original HTML.

If the span argument was produced by running the `detag` statement over an empty document, the function remaps the spans to the beginning of the document \(that is, Document.text\[0-0\]\). Also, if the `detag` statement produces an empty string, the function remaps the spans to the beginning of the document. The only part of AQL that produces such derived text object is the `detag` statement.

The following example illustrates the use of the `Remap` function:

```
-- Detag the HTML document and annotate the anchor tags
detag Document.text as DetagedDoc
    annotate 
    element 'a' as Anchor;

-- Remap the Anchor Tags
create view AnchorTag as
select Remap(A.match) as anchor
from Anchor A;
```

If the argument to Remap is not a derived text object or a span over a derived text object , the function generates an error. If the argument is `null`, the function returns `null`.

### SpanBetween

The `SpanBetween` function takes two spans as input and returns the span that exactly covers the text between the two spans if the spans are based on the same text object, and returns `null` if they are based on different text objects:

```
SpanBetween(['IgnoreOrder',] <span1>, <span2>)
```

When the optional `IgnoreOrder` parameter is used, the order of the two spans is ignored by the AQL compiler.

If there is no text between the two spans, then `SpanBetween` returns an empty span that starts at the end of `<span1>`.

Like `CombineSpans`, `SpanBetween` is sensitive to the order of its inputs, unless you use the `IgnoreOrder` parameter. So

```
SpanBetween([5, 10], [50, 60])
```

returns the span `[10, 50]`, while

```
SpanBetween([50, 60], [5, 10])
```

returns the span `[60, 60]`.

If the argument to `SpanBetween` is `null`, then the function returns `null`.

### SpanIntersection

The `SpanIntersection` function takes two spans as input and returns a span that covers the text that both inputs cover if the spans are based on the same text object, and returns `null` if they are based on different text objects:

```
SpanIntersection(<span1>, <span2>)
```

For example,

```
SpanIntersection([5, 20], [10, 60])
```

returns the span `[10, 20]`, while

```
SpanIntersection([5, 20], [7, 10])
```

returns the span `[7, 10]`.

If the two spans do not overlap, then SpanIntersection returns `null`. If either span input is `null`, the function returns `null`.

### SubSpanTok

The `SubSpanTok` function takes as input a span and a pair of offsets into the span:

```
SubSpanTok(<span>, <first_tok>, <last_tok>)
```

As the name of the function suggests, the `<first_tok>` and `<last_tok>` arguments are distances in tokens, according to whatever tokenizer the system is configured to use.

The `SubSpanTok` function returns a new span that covers the indicated range of tokens, inclusive, within the input span. If the specified range starts inside the span and goes beyond the end of the span, then the portion of the range that is contained is returned. If `<first_tok>` represents a distance beyond the target span, then SubSpanTok returns a zero-length span that starts at the beginning of the input span.

If any input is `null`, the function returns `null`.

### ToLowerCase

The `ToLowerCase` function takes a single object as its argument and returns a lowercase string representation of the object . The conversion to a string occurs in the same way that the GetString\(\) function performs the conversion.

The primary use of this function is to perform equality joins that are not case-sensitive:

```
where Equals(ToLowerCase(C.company), ToLowerCase(N2C.name)) 
```

If the input object is `null`, the function returns `null`.

## The `create` function statement

To perform operations on extracted values that are not supported by AQL, you can define custom functions to use in extraction rules called user-defined functions \(UDFs\).

AQL supports user-defined scalar functions and user-defined table functions. Java™ and PMML are the only supported implementation language for UDFs. A scalar function returns a single scalar value, and a table function returns one or more tuples, in other words, a table.

There are four steps for using user-defined functions \(UDFs\):

1.  Implementing the function.
2.  Declaring it in AQL.
3.  Using it in AQL.
4.  Debugging the UDF.

-   **Implementing user-defined functions**  
AQL supports user-defined functions \(UDFs\) that are implemented in Java or PMML.
-   **Declaring user-defined functions**  
You can make the user-defined scalar functions and machine learning models from PMML files available to AQL by using the `create function` statement.
-   **Using user-defined functions**  
User-defined functions work in conjunction with AQL statements and clauses.
-   **Procedure to debug Java based UDFs**  
Since Java based user-defined functions \(UDFs\) are implemented as public methods in Java classes, you debug your UDFs in the same way that you debug your Java programs.



## Implementing user-defined functions

AQL supports user-defined functions \(UDFs\) that are implemented in Java™ or PMML.

This section specifically focuses on UDFs that are implemented in Java. For UDFs implemented in PMML, the machine learning model is stored inside the PMML XML file. Refer to the documentation of PMML for how to create these models: [http://dmg.org/pmml/v4-1/GeneralStructure.html]

You can implement a Scalar UDF as a public method in a Java class. You can implement a table UDF as a public method in a Java class that extends the API com.ibm.avatar.api.udf.TableUDFBase. In addition, a table UDF can optionally override the method initState\(\) of the superclass com.ibm.avatar.api.udf.TableUDFBase.

If the UDF has an input parameter of type Span, Text, or ScalarList, or the return type of the UDF is Span, Text, or ScalarList, the Java class must import the classes com.ibm.avatar.algebra.datamodel.Span, com.ibm.avatar.algebra.datamodel.Text, or com.ibm.avatar.algebra.datamodel.ScalarList to compile.

Table functions require additional APIs to provide output schema information. These APIs belong to the base class com.ibm.systemt.api.udf.TableUDFbase. If a subclass contains more than one table function, a separate Java object is created for each instance.

For the UDF code to retrieve non-class resources from its JAR file, the only supported method is getResourceAsStream\(\). Other methods for accessing resources \(such as getResource\(\), getResources\(\), getSystemResource\(\)\) are not supported. For example, a UDF JAR file that contains the properties file my.properties in the package com.ibm.myproject.udfs, can access it with the following Java statement:

```
InputStream in = this.getClass().getClassLoader().
getResourceAsStream(“com/ibm/myproject/udfs/my.properties”);
```

### Lifecycle of FUDs implemented in Java

The following operations are performed when the extractor is compiled \(the CompileAQL.compile\(\) API\), instantiated \(OperatorGraph.createOG\(\) API\) and validated \(OperatorGraph.validateOG\(\) API\), exactly once for each create function statement in AQL:

1.  Load the Java class that contains the UDF method, using a fresh new class loader. The class is searched inside the UDF JAR specified in the corresponding create function statement. Any other classes that are required when loading this class are also searched inside the same UDF JAR, and if not found, the search is delegated to the classloader that instantiated the Runtime.
2.  Create an instance of that class.
3.  For table UDFs, invoke the method initState\(\).

Since those steps are performed for each create function statement, if a Java class contains multiple UDF methods \(and all methods are used in AQL in different create function statements\), then the class will be loaded multiple times, each time in a separate class loader \(Step 1\). Furthermore, multiple instances of the class are created \(Step 2\) and the method initState\(\) is called once for each instance \(Step 3\). The reason every UDF results in a separate class loader is to allow different UDFs to use different versions of the same class \(or library\).

At runtime \(OperatorGraph.execute\(\) API\), the UDF class is not loaded again, because the class has already been loaded during extractor instantiation. The Java method that implements the UDF is invoked when necessary to compute pieces of the output. When the extractor is used within a single thread, that means there are anywhere from zero invocation to possibly many invocations for each input document \(and most likely multiple invocations throughout the life of the Operator Graph object\). When the extractor is shared across multiple threads, different threads can hit the method around the same time \(with different inputs\).

If you require a specific part of the UDF code to be evaluated exactly once, for example, to initialize data structures needed by the UDF method across invocations, that code should not be placed in the UDF evaluation method, since that method is most likely executed multiple times throughout the life of the extractor \(like the OperatorGraph object\), and can be hit almost simultaneously when the extractor is shared across multiple threads. Instead:

1.  For scalar UDFs, follow standard Java programming principles. For example, place the code in a static block.
2.  For table UDFs, place the code in the initState\(\) method, or follow standard Java programming principles. For example, place the code in a static block.

When doing so, remember that the class may be loaded multiple times during extractor compilation, instantiation and validation, as explained in Steps 1-3 above. If the code that initializes the UDF is placed in a static block, that code will be executed each time the class is loaded \(potentially multiple times\), therefore, introducing an overhead during compilation and operator graph instantiation. If the overhead is large, follow these best practices:

-   To minimize overhead during compilation time, the best practice is to place compile time heavy resources like large dictionaries or UDFs with large initialization time in a separate AQL module and export them. Try compiling only the AQL modules that changed and other modules that depending on them.
-   To minimize overhead during operator graph instantiation and validation:
    1.  If the initialization code is required by a single UDF method, then place that UDF method in a separate Java class \(and place the heavy instantiation code in a static initializer as before, or use some other mechanism that ensures the code is executed once\).
    2.  If the initialization code is shared by multiple UDF methods, then the Runtime and AQL do not provide an explicit mechanism to ensure that initialization code is executed exactly once. In such a situation, if the initialization time is prohibitive, the only solution is to place the shared resources and initialization code on the system classpath. That is, place the initialization code in a new class MySeparateClass.java, and store the initialization result in a static variable of this class, such as MySeparateClass.myVar. Package MySeparateClass.java along with any resources needed during initialization in a JAR file and place that JAR on the system classpath. The UDF methods can refer to the initialized model using the MySeparateClass.myVar static variable. The initialization code will now be executed exactly once - when the class MySeparateClass.java is loaded by the system classloader.

**Tip:**

The compiled representation of a module \(the .tam file\) contains the serialized binary code of the UDF. Therefore, if the same UDF code is referenced by `create function` statements in two different modules, the UDF code is serialized in the compiled representation of both modules. In other words, the UDF code is serialized twice. In such cases, you can avoid the redundancy by creating a separate module that acts as a library of UDFs, and reuse that library in other modules. To create a library of UDFs, follow these steps:

1.  Create one module.
2.  Place all UDF JAR files inside that module.
3.  Define all necessary functions with the `create function` statements.
4.  Export them all with `export function` statements so that they can be imported and used in other modules.

### Examples

**Example 1: Implementing a scalar UDF**

This example shows the implementation of a scalar UDF named toUpperCase. This UDF takes as input a value of type Span and outputs a string value that consists of the text content of the input Span, converted to uppercase.

```
package com.ibm.biginsights.textanalytics.udf;
import com.ibm.avatar.algebra.datamodel.Span;

/**
  * @param s input Span
  * @return all upper-case version of the text of the input Span
  */
public String toUpperCase(Span s) {
  return s.getText().toUpperCase();
}
```

**Example 2: Implementing a scalar UDF that uses a table as input**

This example shows the implementation of a scalar UDF named TableConsumingScalarFunc. This UDF takes as input two lists of tuples and outputs a string value that concatenates the content of the two input tuple lists.

```
import com.ibm.avatar.algebra.datamodel.TupleList;

/**
  * Example implementation of a user-defined scalar function using a table as input
*/
public class TableConsumingScalarFunc 
{

  /**
    * Main entry point to the `scalar` function. This function takes two lists of tuples and concatenates them into a single string.
    * 
    * @param arg1 first set of tuples to merge
    * @param arg2 second set of tuples to merge
    * @return the two sets of tuples, concatenated
    */
  public String eval (TupleList arg1, TupleList arg2)
  {
    StringBuilder sb = new StringBuilder ();
    
    sb.append("Input1: ");
    sb.append(arg1.toPrettyString ());
    sb.append("\nInput2: ");
    sb.append(arg2.toPrettyString ());
    
    return sb.toString ();
  }
}
```

**Example 3: Implementing a table UDF that uses a table as input**

This example shows the implementation of a table UDF named TableConsumingTableFunc. This UDF takes as input two lists of tuples and outputs a single list of tuples that contains tuples from the first input interspersed with tuples from the second input. Notice that the implementation extends from the base class com.ibm.avatar.api.udf.TableUDFBase, which provides APIs for obtaining the input and output schemas.

```
package com.ibm.test.udfs;

import java.lang.reflect.Method;

import com.ibm.avatar.algebra.datamodel.AbstractTupleSchema;
import com.ibm.avatar.algebra.datamodel.FieldCopier;
import com.ibm.avatar.algebra.datamodel.Tuple;
import com.ibm.avatar.algebra.datamodel.TupleList;
import com.ibm.avatar.algebra.datamodel.TupleSchema;
import com.ibm.avatar.api.exceptions.TableUDFException;
import com.ibm.avatar.api.udf.TableUDFBase;

/**
  * Example implementation of a user-defined table function
*/
public class TableConsumingTableFunc extends TableUDFBase
{

  /** Accessors for copying fields from input tuples to output tuples. */
  private FieldCopier arg1Copier, arg2Copier;

  /**
    * Main entry point to the `table` function. This function takes two lists of tuples and generates a new list of wide
    * tuples, where element i of the returned list is created by joining element i of the first input with element i of
    * the second input.
    * 
    * @param arg1 first set of tuples to merge
    * @param arg2 second set of tuples to merge
    * @return the two sets of tuples, interleaved
    */
  public TupleList eval (TupleList arg1, TupleList arg2)
  {

    TupleSchema retSchema = getReturnTupleSchema ();
    TupleList ret = new TupleList (retSchema);

    // We skip any records that go off the end
    int numRecs = Math.min (arg1.size (), arg2.size ());

    for (int i = 0; i < numRecs; i++) {
      Tuple retTuple = retSchema.createTup ();

      Tuple inTup1 = arg1.getElemAtIndex (i);
      Tuple inTup2 = arg2.getElemAtIndex (i);

      arg1Copier.copyVals (inTup1, retTuple);
      arg2Copier.copyVals (inTup2, retTuple);

      // System.err.printf ("%s + %s = %s\n", inTup1, inTup2, retTuple);

      ret.add (retTuple);
    }

    return ret;
  }

  /**
    * Initialize the internal state of the `table` function. In this case, we create accessors to copy fields from input
    * tuples to output tuples.
    * 
    * @see com.ibm.avatar.api.udf.TableUDFBase#initState() for detailed description
    */
  @Override
  public void initState () throws TableUDFException
  {
    // Create accessors to do the work of copying fields from input tuples to output tuples
    AbstractTupleSchema arg1Schema = getRuntimeArgSchema ().getFieldTypeByIx (0).getRecordSchema ();
    AbstractTupleSchema arg2Schema = getRuntimeArgSchema ().getFieldTypeByIx (1).getRecordSchema ();
    TupleSchema retSchema = getReturnTupleSchema ();

    // Create offsets tables for a straightforward copy.
    String[] srcs1 = new String[arg1Schema.size ()];
    String[] dests1 = new String[arg1Schema.size ()];
    String[] srcs2 = new String[arg2Schema.size ()];
    String[] dests2 = new String[arg2Schema.size ()];

    for (int i = 0; i < srcs1.length; i++) {
      srcs1[i] = arg1Schema.getFieldNameByIx (i);
      dests1[i] = retSchema.getFieldNameByIx (i);
    }
    for (int i = 0; i < srcs2.length; i++) {
      srcs2[i] = arg2Schema.getFieldNameByIx (i);
      dests2[i] = retSchema.getFieldNameByIx (i + srcs1.length);
    }

    arg1Copier = retSchema.fieldCopier (arg1Schema, srcs1, dests1);
    arg2Copier = retSchema.fieldCopier (arg2Schema, srcs2, dests2);
  }

  /**
    * Check the validity of tuple schemas given in the AQL “create function”.
    * 
    * @see com.ibm.avatar.api.udf.TableUDFBase#validateSchema(TupleSchema, TupleSchema, TupleSchema, Method, Boolean) for
    *      description of arguments
    */
  @Override
  public void validateSchema (TupleSchema declaredInputSchema, TupleSchema runtimeInputSchema,
    TupleSchema returnSchema, Method methodInfo, boolean compileTime) throws TableUDFException
  {
    // The output schema should contain the columns of the two input schemas in order.
    AbstractTupleSchema arg1Schema = declaredInputSchema.getFieldTypeByIx (0).getRecordSchema ();
    AbstractTupleSchema arg2Schema = declaredInputSchema.getFieldTypeByIx (1).getRecordSchema ();

    System.err.printf ("TableConsumingTableFunc: Input schemas are %s and %s\n", arg1Schema, arg2Schema);

    // First check sizes
    if (returnSchema.size () != arg1Schema.size () + arg2Schema.size ()) { throw new TableUDFException (
      "Schema sizes don't match (%d + %d != %d)", arg1Schema.size (), arg2Schema.size (), returnSchema.size ()); }

    // Then check types
    for (int i = 0; i < arg1Schema.size (); i++) {
      if (false == (arg1Schema.getFieldTypeByIx (i).equals (returnSchema.getFieldTypeByIx (i)))) { throw new TableUDFException (
        "Field type %d of output doesn't match corresponding field of first input arg (%s != %s)", i,
        returnSchema.getFieldTypeByIx (i), arg1Schema.getFieldTypeByIx (i)); }
    }

    for (int i = 0; i < arg2Schema.size (); i++) {
      if (false == (arg2Schema.getFieldTypeByIx (i).equals (returnSchema.getFieldTypeByIx (i + arg1Schema.size ())))) { throw new TableUDFException (
        "Field type %d of output doesn't match corresponding field of first input arg (%s != %s)", i
          + arg1Schema.size (), returnSchema.getFieldTypeByIx (i + arg1Schema.size ()), arg2Schema.getFieldTypeByIx (i)); }
    }
  }

}
```




## Declaring user-defined functions

You can make the user-defined scalar functions and machine learning models from PMML files available to AQL by using the `create function` statement.

### Syntax

The general syntax of the `create function` statement is as follows:

```
create function <function-name>(<input-schema-definition>)
return <return-type> [like <column-name>] | table ( <output-schema-definition)
external_name <ext-name>
language [java | pmml]
[deterministic | not deterministic]
[return null on null input | called on null input];
```

```
<input-schema-definition>
<column-name> <data-type> | table (<output-schema-definition>) as locator [,<column-name> <data-type> | table (<output-schema-definition>) as locator ]*
```

```
<output-schema-definition>
<column-name> <data-type> [,<column-name> <data-type>]*
```

### Description

-   `<function-name\>`

    The `<function-name\>` declares the AQL name of the UDF. The UDF is referred to in the AQL code with this name

-   `<input-schema-definition\>`

    Specifies the input parameters of the UDF. An input parameter has a name, specified as `<column-name\>`, and can be either a scalar type or a table locator. When the language is PMML, the function must take a single table called paramsas the argument.

-   `<column-name\>`

    Specifies the name of a column in the input or the output of the UDF.

-   `<data-type\>`

    The type of an input scalar parameter to the UDF, the type of a column in the schema of an input table to the UDF or in the schema of the output table of the UDF. Possible values for `<data-type\>` are Integer, Float, String, Text, Span, Boolean, or ScalarList.

-   `table \(<output-schema-definition\>) as locator`

    This input type allows a function to take as input the entire contents of a given AQL view as computed on the current document. The locator parameter references views or tables as arguments.

-   `<return-type\>`

    For scalar UDFs, the `<return-type\>` specifies the type of the scalar value returned by the UDF. Possible values for the return type are: Integer, Float, String, Text, Span, Boolean, or ScalarList. If the return type is Integer, the Java™ function that implements the UDF returns objects of type Integer. The UDF implementation cannot return the primitive int type. If the return type is Text or Span, specify the input parameter from which the return type is derived. You can specify the input parameter by using the optional like specification, since spans are always from an underlying column. If the return type is ScalarList, specify the input parameter from which the scalar type inside the ScalarList is to be inferred. When the language is PMML, the function must return a table.

-   `<output-schema-definition\>`

    For table UDFs, the `<output-schema-definition\>` specifies the output schema of the table returned by the UDF, including the column names and their types.

-   `<ext-name\>`

    The external\_name specifies where to find the implementation of the UDF. When the language is Java, it is a string of the form `'<jar-file-name\>:<fully-qualified-class-name\>!<method-name\>'`, which consists of three parts:

    -   JAR file name: When you compile modular AQL, the location references of UDF JAR files must be relative to the root of the module in which the reference is made.
    -   Class name: Fully qualified class name that contains the UDF implementation
    -   Method name: The method must be a public method of the class. The method signature must match the parameter types that are specified in the `create function` statement. Automatic type conversion is not done by the runtime component.
    When the language is PMML, the external\_name clause will specify a string which will be the location of the PMML file relative to the module’s root directory. The current implementation supports models expressed using the PMML standard version 4.1 and evaluates them using the version 1.0.22 org.jpmml library .

-   `language`

    The language specification points to the language of implementation of the UDF. The runtime component supports only UDFs that are implemented in Java™.

-   `deterministic/not deterministic`

    The optional deterministic/not deterministic specifies whether the function is stateless. A deterministic function always returns the same value for the same set of input values.

-   `return null on null input`

    The optional return null on null input specifies the function behavior when one or more of the input values are null. If return null on null input is specified, the system returns `null` on null input without actually invoking the UDF. If called on null input is specified, the UDF is invoked even for null input values.


### Usage notes for UDFs implemented in PMML

Functions created from PMML files take a single table called a params as their argument and output a table. The implementation of the function will map input fields between the input and output schema declared in the create function statement and the schema specified in the PMML file. In other words, the **DataDictionary** section that describes the names and types of fields that can appear in the input and output records that the model produces and consumes, the **MiningSchema** section that tells which named files defined in the DataDictionary section are in each tuple that represents a feature vector ,and the **Output** section that tells which named fields defined in the **DataDictionary** section are present in each tuple of the external representation of the output of the model. These functions must be table functions; each row in the table will be passed to the PMML model and produce an output row.

This schema information is necessary because the PMML and AQL type systems do not match perfectly. For example, PMML has several types to represent timestamps, while AQL currently requires users to encode timestamps as string values. The schema information also allows developers who know AQL but not PMML to understand the AQL rule set.

The AQL compiler will check the input schema against the input schema of the PMML file to ensure that the two schemas are compatible. If the two schemas contain fields with the same name but incompatible types, compilation will fail with an appropriate error message. If the function’s input or output schemas contain extra or missing columns, the `resulting` function will ignore these columns and will not generate an error. The order of column names can be different between the AQL definition and the PMML file. If a column name appears in both input and output schemas but not in the PMML schema, then the values of that column will be passed through to the output of the function.

### Examples

**Example 1: Declaring scalar UDFs with scalar values as input using Java**

The following example shows a `create function` statement that declares a function named udfCombineSpans. The user-defined function takes in two spans as input and returns a merged span similar to the first input span. The actual UDF Java™ function is packaged in a JAR file named udfs.jar, under the udfjars directory. The method that implements the function is combineSpans in class com.ibm.test.udfs.MiscScalarFunc. The method also declares a function udfSpanGreaterThan that returns true if the span is greater than the specified size.

```
/** 
* A function to combine two spans and return the resultant span from beginOffset of first span, to endOffset of second span
* @param p1 first input span
* @param p2 second input span
* @return a span from beginOffset of p1 till endOffset of p2
*/

create function udfCombineSpans(p1 Span, p2 Span)
return Span like p1
external_name 'udfjars/udfs.jar:com.ibm.test.udfs.MiscScalarFunc!combineSpans'
language java 
deterministic
return null on null input;

/** 
* A function to compare an input Span's size against an input size
* @param span input span
* @param size input size to be compared against
* @return Boolean true if input span's size is greater than input argument size, else false
*/

create function udfSpanGreaterThan(span Span, size Integer)
return Boolean
external_name 'udfjars/udfs.jar:com.ibm.test.udfs.MiscScalarFunc!spanGreaterThan'
language java 
deterministic;
```

The next example shows how to declare a function named udfCompareNames that is given a list of names nameList and a single name myName. The output is a list similar to the input list, which contains only the entries from nameList similar to myName.

```
/** 
* A function to compare an input string against a list of names 
* and returns a list of entries from nameList similar to myName.
* @param nameList a list of names
* @param myName a name to compare against the list
* @return a list of entries from nameList similar to myName
*/

create function udfCompareNames(nameList ScalarList, myName String)
return ScalarList like nameList
external_name 'udfjars/udfs.jar:com.ibm.test.udfs.MiscScalarFunc!compareNames'
language java 
deterministic;
```

**Example 2: Declaring scalar UDFs with tables as input using Java**

The following example illustrates the use of the `table as locator` input type. It shows a `create function` statement that declares a function called MyScalarFunc. The Java™ implementation of the UDF is packaged inside the class com.ibm.test.udfs.TableConsumingScalarFunc.

This UDF takes as input two lists of tuples and outputs a string value that concatenates the content of the two input tuple lists. The Java™ implementation of the UDF is included in [Implementing user-defined functions.

```
-- Declare a simple scalar function that turns two tables into a big string
create function MyScalarFunc( 
    firstArg table( spanVal Span ) as locator,
    secondArg table( spanVal Span, strVal Text ) as locator
)
return String
external_name 
  'udfjars/udfs.jar:com.ibm.test.udfs.TableConsumingScalarFunc!eval'
language java
deterministic
called on null input;
```

**Example 3: Declaring table FUDs using Java**

The following example illustrates the use of the `return table` clause. The example shows a `create function` statement that declares a table function called MyScalarFunc. The Java™ implementation of the UDF is packaged inside the class com.ibm.test.udfs.TableConsumingTableFunc. This UDF takes as input two lists of tuples and outputs a list of tuples that merges together the input lists. The Java™ implementation of the UDF is included in [Implementing user-defined functions.

```
-- Declare a simple table function that "zips together" two input tables
create function MyTableFunc( 
    firstArg table( spanVal Span ) as locator,
    secondArg table( spanVal Span, strVal Text ) as locator
)
return table( outSpan1 Span, outSpan2 Span, outStr Text)
external_name 
  'udfjars/udfs.jar:com.ibm.test.udfs.TableConsumingTableFunc!eval'
language java
deterministic
called on null input;
```


**Example 4: Declaring a table UDF implemented in PMML**

The following example shows a `create function` statement that declares a table function named IrisDecisionTree using PMML language. The PMML implementation of the UDF is specified in the IrisTree.xml file, [whose content is shown below. The model stored in the IrisTree.xml is a decision tree model..

```
-- Scoring function based on a decision tree model stored in IrisTree.xml
create function IrisDecisionTree(
    params table(
        sepal_length Float,
        sepal_width Float,
        petal_length Float,
        petal_width Float
    ) as locator
)
return table( class Text, actual_class Text,
    -- This PMML file also defines additional output fields
    "Probability_Iris-setosa" Float,
    "Probability_Iris-versicolor" Float,
    "Probability_Iris-virginica" Float)
external_name 'IrisTree.xml'
language pmml;
```

**IrisTree.xml**

```
<?xml version="1.0"?>
<PMML version="3.2" xmlns="http://www.dmg.org/PMML-3_2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.dmg.org/PMML-3_2 http://www.dmg.org/v3-2/pmml-3-2.xsd">
  <Header copyright="Copyright (c) 2012 DMG" description="RPart Decision Tree Model">
  <Extension name="user" value="DMG" extender="Rattle/PMML"/>
  <Application name="Rattle/PMML" version="1.2.29"/>
  <Timestamp>2012-09-27 12:46:08</Timestamp>
  </Header>
  <DataDictionary numberOfFields="5">
  <DataField name="class" optype="categorical" dataType="string">
    <Value value="Iris-setosa"/>
    <Value value="Iris-versicolor"/>
    <Value value="Iris-virginica"/>
  </DataField>
  <DataField name="sepal_length" optype="continuous" dataType="double">
    <Interval closure="closedClosed" leftMargin="4.3" rightMargin="7.9"/>
  </DataField>
  <DataField name="sepal_width" optype="continuous" dataType="double">
    <Interval closure="closedClosed" leftMargin="2" rightMargin="4.4"/>
  </DataField>
  <DataField name="petal_length" optype="continuous" dataType="double">
    <Interval closure="closedClosed" leftMargin="1" rightMargin="6.91"/>
  </DataField>
  <DataField name="petal_width" optype="continuous" dataType="double">
    <Interval closure="closedClosed" leftMargin="0.1" rightMargin="2.5"/>
  </DataField>
  </DataDictionary>
  <TreeModel modelName="RPart_Model" functionName="classification" algorithmName="rpart" splitCharacteristic="binarySplit" missingValueStrategy="defaultChild">
  <MiningSchema>
    <MiningField name="class" usageType="predicted"/>
    <MiningField name="sepal_length" usageType="supplementary"/>
    <MiningField name="sepal_width" usageType="supplementary"/>
    <MiningField name="petal_length" usageType="active"/>
    <MiningField name="petal_width" usageType="supplementary"/>
  </MiningSchema>
  <Output>
    <OutputField name="class" optype="categorical" dataType="string" feature="predictedValue"/>
    <OutputField name="Probability_Iris-setosa" optype="continuous" dataType="double" feature="probability" value="Iris-setosa"/>
    <OutputField name="Probability_Iris-versicolor" optype="continuous" dataType="double" feature="probability" value="Iris-versicolor"/>
    <OutputField name="Probability_Iris-virginica" optype="continuous" dataType="double" feature="probability" value="Iris-virginica"/>
  </Output>
  <Node id="1" score="Iris-virginica" recordCount="105" defaultChild="3">
    <True/>
    <ScoreDistribution value="Iris-setosa" recordCount="33" confidence="0.314285714285714"/>
    <ScoreDistribution value="Iris-versicolor" recordCount="35" confidence="0.333333333333333"/>
    <ScoreDistribution value="Iris-virginica" recordCount="37" confidence="0.352380952380952"/>
    <Node id="2" score="Iris-setosa" recordCount="33">
    <SimplePredicate field="petal_length" operator="lessThan" value="2.6"/>
    <ScoreDistribution value="Iris-setosa" recordCount="33" confidence="1"/>
    <ScoreDistribution value="Iris-versicolor" recordCount="0" confidence="0"/>
    <ScoreDistribution value="Iris-virginica" recordCount="0" confidence="0"/>
    </Node>
    <Node id="3" score="Iris-virginica" recordCount="72" defaultChild="7">
    <SimplePredicate field="petal_length" operator="greaterOrEqual" value="2.6"/>
    <ScoreDistribution value="Iris-setosa" recordCount="0" confidence="0"/>
    <ScoreDistribution value="Iris-versicolor" recordCount="35" confidence="0.486111111111111"/>
    <ScoreDistribution value="Iris-virginica" recordCount="37" confidence="0.513888888888889"/>
    <Node id="6" score="Iris-versicolor" recordCount="37">
      <SimplePredicate field="petal_length" operator="lessThan" value="4.85"/>
      <ScoreDistribution value="Iris-setosa" recordCount="0" confidence="0"/>
      <ScoreDistribution value="Iris-versicolor" recordCount="34" confidence="0.918918918918919"/>
      <ScoreDistribution value="Iris-virginica" recordCount="3" confidence="0.0810810810810811"/>
    </Node>
    <Node id="7" score="Iris-virginica" recordCount="35">
      <SimplePredicate field="petal_length" operator="greaterOrEqual" value="4.85"/>
      <ScoreDistribution value="Iris-setosa" recordCount="0" confidence="0"/>
      <ScoreDistribution value="Iris-versicolor" recordCount="1" confidence="0.0285714285714286"/>
      <ScoreDistribution value="Iris-virginica" recordCount="34" confidence="0.971428571428571"/>
    </Node>
    </Node>
  </Node>
  </TreeModel>
</PMML>
```


### Documenting the `create function` statement with comments

The AQL Doc comment for a create function statement contains the following information:

-   A general description about the function.
-   The @param description that specifies each parameter name that is used in the function. The description should indicate the type of the parameter, whether it is a scalar type or a table. If the parameter is a table, it should describe the schema of the table, including column names and types in the order in which they appear in the schema of the table expected as input.
-   The @return description that specifies the information that is returned by the function. If the function returns a table, specify the output schema of the table, including column names and types in the order in which they appear in the schema of the output table.

```
/** 
* A function to compare an input string against a list of names 
* and returns a list of entries from nameList similar to myName.
* @param nameList a list of names
* @param myName a name to compare against the list
* @return a list of entries from nameList similar to myName
*/

create function udfCompareNames(nameList ScalarList, myName String)
  return ScalarList like nameList
  external_name 'udfjars/udfs.jar:com.ibm.test.udfs.MiscScalarFunc!compareNames'
  language java 
  deterministic;
```

## Using user-defined functions

User-defined functions work in conjunction with AQL statements and clauses.

User-defined scalar functions work in conjunction with AQL statements and clauses, similar to built-in functions. Specifically, scalar UDFs can be used in the `select`, `where`, `having`, `group by`, and `order by` clauses in the same way as built-in scalar functions, such as `GetBegin` and `LeftContext`. User-defined scalar functions that return a Boolean type can be used as predicates in `where` and `having` clauses.

User-defined table functions \(table UDFs\) can be used within the `from` clause of a `select` statement or an `extract` statement.

### Examples

**Example 1: Using scalar UDFs implemented in Java with scalar values as input**

This example demonstrates how to use the `udfCombineSpans` and `udfSpanGreaterThan` functions that are declared in [Declaring user-defined functions.

```
create function udfCombineSpans(p1 Span, p2 Span)
return Span like p1
external_name 'udfjars/udfs.jar:com.ibm.test.udfs.MiscScalarFunc!combineSpans'
language java 
deterministic
return null on null input;

create function udfSpanGreaterThan(span Span, size Integer)
return Boolean
external_name 'udfjars/udfs.jar:com.ibm.test.udfs.MiscScalarFunc!spanGreaterThan'
language java 
deterministic;

-- identify occurrences of first names in the document
create dictionary FirstNamesDict from file 'firstNames.dict';

create view FirstName as
extract dictionary 'FirstNamesDict' on D.text as name
from Document D;

-- Use a UDF to merge the name that is longer than 7 characters with the text to its right in a
-- way that is appropriate to the application.
create view NameAndContext as
select udfCombineSpans(F.name, RightContext(F.name, 50)) as name
from FirstName F
where udfSpanGreaterThan(F.name, 7);
```

**Example 2: Using Scalar UDFs implemented in Java with tables as input**

The following example shows how to use a scalar function that uses tables as input. This example illustrates the usage of the MyScalarFunc table UDF function, whose Java™ implementation is included in [Implementing user-defined functions`. They are the same column types, but have different column names.

```
-- Declare a simple scalar function that turns two tables into a big string
create function MyScalarFunc( 
    firstArg table( spanVal Span ) as locator,
    secondArg table( spanVal Span, strVal Text ) as locator
)
return String
external_name 
  'udfjars/udfs.jar:com.ibm.test.udfs.TableConsumingScalarFunc!eval'
language java
deterministic
called on null input;

-- Create two views to serve as inputs to the `table` function.
-- Note that column names don't match, but types do.
create view FirstInputView as
extract regex /\d+/ on 1 token in D.text as match
from Document D;

create view SecondInputView as
select S.match as spanCol, 'Dummy string' as textCol
from 
    (extract regex /[A-Z][a-z]+/ on 1 token in D.text as match
    from Document D) S;

-- Call the `scalar` function defined above from the select list.
create view ScalarFuncOutput as 
select MyScalarFunc(FirstInputView, SecondInputView) as func
from Document D;

```

**Example 3: Using Table UDFs implemented in Java**

This example illustrates the usage of the MyTableFunc table UDF function, whose Java™ implementation is included in [Implementing user-defined functions.

```
-- Declare a simple table function that "zips together" two input tables
create function MyTableFunc( 
    firstArg table( spanVal Span ) as locator,
    secondArg table( spanVal Span, strVal Text ) as locator
)
return table( outSpan1 Span, outSpan2 Span, outStr Text)
external_name 
  'udfjars/udfs.jar:com.ibm.test.udfs.TableConsumingTableFunc!eval'
language java
deterministic
called on null input;

-- Create two views to serve as inputs to the `table` function.
-- Note that column names don't match, but types do.
create view FirstInputView as
extract regex /\d+/ on 1 token in D.text as match
from Document D;


create view SecondInputView as
select S.match as spanCol, 'Dummy string' as textCol
from 
    (extract regex /[A-Z][a-z]+/ on 1 token in D.text as match
    from Document D) S;

-- Use the `table` function
create view TabFuncOutput as 
select T.outSpan1 as span1, T.outSpan2 as span2
from MyTableFunc(FirstInputView, SecondInputView) T;
```

As in Example 2, The example defines two views: `FirstInputView` with schema `(match Span)` and `SecondInputView` with schema `(spanCol Span, textCol Text)`. The last view in the example, `TabFuncOutput` invokes the `table` function MyTableFunc in the `from` clause, with the two input views. As explained in Example 2, a view is compatible with a table locator argument of a function, as long as the number of columns and the column types in the schema of the input view and table locator match. However, it is not necessary that the column names match.

Finally, the `select` clause discards column `outStr` from the output table of MyTableFunc, keeping only the first two columns `outSpan1` and `outSpan2`.

**Example 4: Using a table UDF implemented in PMML**

This example illustrates the usage of the IrisDecisionTree table UDF function that is declared in example 4 of [Declaring user-defined functions.

```
-- External view to hold the input records
create external view IrisData(
    sepal_length Float,
    sepal_width Float,
    petal_length Float,
    petal_width Float
)
external_name 'IrisData';
--Invoke the function on the input data records
create view IrisDecisionTreeOutput as
select * from IrisDecisionTree(IrisData);

output view IrisDecisionTreeOutput;
```
