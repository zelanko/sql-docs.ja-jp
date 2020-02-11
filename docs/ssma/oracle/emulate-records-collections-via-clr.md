---
title: CLR UDT を使用したレコードとコレクションのエミュレーション
description: SQL Server Migration Assistant (SSMA) for Oracle が SQL Server 共通言語ランタイム (CLR) のユーザー定義データ型 (UDT) を使用して Oracle のレコードとコレクションをエミュレートする方法について説明します。
authors: nahk-ivanov
ms.service: ssma
ms.devlang: sql
ms.topic: article
ms.date: 1/22/2020
ms.author: alexiva
ms.openlocfilehash: 39a7e8d59425db7ce2d7e81083012321caac35ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "76762816"
---
# <a name="emulating-records-and-collections-via-clr-udt"></a>CLR UDT を使用したレコードとコレクションのエミュレーション

この記事では、SQL Server Migration Assistant (SSMA) for Oracle が SQL Server 共通言語ランタイム (CLR) のユーザー定義データ型 (UDT) を使用して Oracle のレコードとコレクションをエミュレートする方法について説明します。

## <a name="declaring-record-or-collection-types-and-variables"></a>レコードまたはコレクション型と変数の宣言

SSMA は、次の3つの CLR ベースの Udt を作成します。

* `CollectionIndexInt`
* `CollectionIndexString`
* `Record`

この`CollectionIndexInt` `VARRAY`型は、、入れ子になったテーブル、整数キーベースの連想配列など、整数によってインデックス付けされたコレクションをエミュレートするためのものです。 この`CollectionIndexString`型は、文字キーによってインデックス付けされた連想配列に使用されます。 Oracle レコード機能は、 `Record`型によってエミュレートされます。

レコードまたはコレクション型のすべての宣言は、次の Transact-sql 宣言に変換されます。

```sql
declare @Collection$TYPE varchar(max) = '<type definition>'
```

ソース`<type definition>`の PL/SQL 型を一意に識別する説明テキストを次に示します。

次の例を確認してください。

```sql
DECLARE
    TYPE Manager IS RECORD
    (
        mgrid integer,
        mgrname varchar2(40),
        hiredate date
    );

    TYPE Manager_table is TABLE OF Manager INDEX BY PLS_INTEGER;

    Mgr_rec Manager;
    Mgr_table_rec Manager_table;
BEGIN
    mgr_rec.mgrid := 1;
    mgr_rec.mgrname := 'Mike';
    mgr_rec.hiredate := sysdate;

    select
        empno,
        ename,
        hiredate
    BULK COLLECT INTO
        mgr_table_rec
    FROM
        emp;
END;
```

SSMA を使用して変換すると、次の Transact-sql コードになります。

```sql
BEGIN
    DECLARE
        @CollectionIndexInt$TYPE varchar(max) =
            ' TABLE INDEX BY INT OF ( RECORD ( MGRID INT , MGRNAME STRING , HIREDATE DATETIME ) )'

    DECLARE
        @Mgr_rec$mgrid int,
        @Mgr_rec$mgrname varchar(40),
        @Mgr_rec$hiredate datetime2(0),
        @Mgr_table_rec dbo.CollectionIndexInt =
            dbo.CollectionIndexInt::[Null].SetType(@CollectionIndexInt$TYPE)

    SET @mgr_rec$mgrid = 1
    SET @mgr_rec$mgrname = 'Mike'
    SET @mgr_rec$hiredate = sysdatetime()

    SET @mgr_table_rec = @mgr_table_rec.RemoveAll()
    SET @mgr_table_rec =
        @mgr_table_rec.AssignData(
            ssma_oracle.fn_bulk_collect2CollectionComplex((
                SELECT
                    CAST(EMP.EMPNO AS int) AS mgrid,
                    EMP.ENAME AS mgrname,
                    EMP.HIREDATE AS hiredate
                FROM dbo.EMP
                FOR XML PATH
            ))
        )
END
```

ここでは、 `Manager`テーブルは数値インデックス (`INDEX BY PLS_INTEGER`) に関連付けられているため、使用される対応する`@CollectionIndexInt$TYPE`t-sql 宣言の型はです。 テーブルが文字セットインデックス (など`VARCHAR2`) に関連付けられている場合、対応する t-sql 宣言の型`@CollectionIndexString$TYPE`は次のようになります。

```sql
-- Oracle
TYPE Manager_table is TABLE OF Manager INDEX BY VARCHAR2(40);

-- SQL Server
@CollectionIndexString$TYPE varchar(max) =
    ' TABLE INDEX BY STRING OF ( RECORD ( MGRID INT , MGRNAME STRING , HIREDATE DATETIME ) )'
```

Oracle レコード機能は、 `Record`型によってのみエミュレートされます。

`CollectionIndexInt`、、 `CollectionIndexString`、 `Record`の各型には、空のインスタンスを`[Null]`返す静的プロパティがあります。 `SetType`メソッドは、(上の例に示すように) 特定の型の空のオブジェクトを受け取るために呼び出されます。

## <a name="constructor-call-conversions"></a>コンストラクター呼び出しの変換

コンストラクターの表記は、入れ子になったテーブル`VARRAY`およびに対してのみ使用できます。したがって、 `CollectionIndexInt`明示的なコンストラクター呼び出しはすべて、型を使用して変換されます。 空のコンストラクター呼び出しは、 `SetType`の null インスタンスで呼び出され`CollectionIndexInt`た呼び出しを介して変換されます。 プロパティ`[Null]`は、null インスタンスを返します。 コンストラクターに要素のリストが含まれている場合は、コレクションに値を追加するために、特別なメソッド呼び出しが順番に適用されます。

次に例を示します。

```sql
-- Oracle

DECLARE
    TYPE nested_type IS TABLE OF VARCHAR2(20);
    TYPE varray_type IS VARRAY(5) OF INTEGER;

    v1 nested_type;
    v2 varray_type;
BEGIN
   v1 := nested_type('Arbitrary','number','of','strings');
   v2 := varray_type(10, 20, 40, 80, 160);
END;

-- SQL Server

BEGIN
    DECLARE
        @CollectionIndexInt$TYPE varchar(max) = ' VARRAY OF INT',
        @CollectionIndexInt$TYPE$2 varchar(max) = ' TABLE OF STRING',
        @v1 dbo.CollectionIndexInt,
        @v2 dbo.CollectionIndexInt

    SET @v1 =
        dbo.CollectionIndexInt::[Null]
            .SetType(@CollectionIndexInt$TYPE$2)
            .AddString('Arbitrary')
            .AddString('number')
            .AddString('of')
            .AddString('strings')

   SET @v2 =
       dbo.CollectionIndexInt::[Null]
            .SetType(@CollectionIndexInt$TYPE)
            .AddInt(10)
            .AddInt(20)
            .AddInt(40)
            .AddInt(80)
            .AddInt(160)
END
```

## <a name="referencing-and-assigning-record-and-collection-elements"></a>レコード要素とコレクション要素の参照と割り当て

各 Udt には、さまざまなデータ型の要素を操作する一連のメソッドがあります。 たとえば、メソッドは`SetDouble` 、レコードまた`float(53)`はコレクションに値を割り当て、 `GetDouble`この値を読み取ることができます。 メソッドの完全な一覧を次に示します。

```sql
GetCollectionIndexInt(@key <KeyType>) returns CollectionIndexInt;
SetCollectionIndexInt(@key <KeyType>, @value CollectionIndexInt) returns <UDT_type>;
GetCollectionIndexString(@key <KeyType>) returns CollectionIndexString;
SetCollectionIndexString(@key <KeyType>, @value CollectionIndexString) returns <UDT_type>;
Record GetRecord(@key <KeyType>) returns Record;
SetRecord(@key <KeyType>, @value Record) returns <UDT_type>;
GetString(@key <KeyType>) returns nvarchar(max);
SetString(@key <KeyType>, @value nvarchar(max)) returns nvarchar(max);
GetDouble(@key <KeyType>) returns float(53);
SetDouble(@key <KeyType>, @value float(53)) returns <UDT_type>;
GetDatetime(@key <KeyType>) returns datetime;
SetDatetime(@key <KeyType>, @value datetime) returns <UDT_type>;
GetVarbinary(@key <KeyType>) returns varbinary(max);
SetVarbinary(@key <KeyType>, @value varbinary(max)) returns <UDT_type>;
SqlDecimal GetDecimal(@key <KeyType>);
SetDecimal(@key <KeyType>, @value numeric) returns <UDT_type>;
GetXml(@key <KeyType>) returns xml;
SetXml(@key <KeyType>, @value xml) returns <UDT_type>;
GetInt(@key <KeyType>) returns bigint;
SetInt(@key <KeyType>, @value bigint) returns <UDT_type>;
```

これらのメソッドは、コレクション/レコードの要素に対して値を参照したり、割り当てたりするときに使用されます。

```sql
-- Oracle
a_collection(i) := 'VALUE';

-- SQL Server
SET @a_collection = @a_collection.SetString(@i, 'VALUE');
```

レコード要素を使用して多次元コレクションまたはコレクションの代入ステートメントを変換すると、SSMA により、set メソッド内の親要素を参照する次のメソッドが追加されます。

```sql
GetOrCreateCollectionIndexInt(@key <KeyType>) returns CollectionIndexInt;
GetOrCreateCollectionIndexString(@key <KeyType>) returns CollectionIndexString;
GetOrCreateRecord(@key <KeyType>) returns Record;
```

たとえば、レコード要素のコレクションは次のように作成されます。

```sql
-- Oracle
DECLARE
    TYPE rec_details IS RECORD (id int, name varchar2(20));
    TYPE ntb1 IS TABLE of rec_details index BY binary_integer;
    c ntb1;
BEGIN
    c(1).id := 1;
END;

-- SQL Server
DECLARE
   @CollectionIndexInt$TYPE varchar(max) =
       ' TABLE INDEX BY INT OF ( RECORD ( ID INT , NAME STRING ) )',
   @c dbo.CollectionIndexInt =
       dbo.CollectionIndexInt::[Null].SetType(@CollectionIndexInt$TYPE)

SET @c = @c.SetRecord(1, @c.GetOrCreateRecord(1).SetInt(N'ID', 1))
```

## <a name="collection-built-in-methods"></a>コレクションの組み込みメソッド

SSMA では、次の UDT メソッドを使用して、PL/SQL コレクションの組み込みメソッドをエミュレートします。

Oracle の収集方法 | `CollectionIndexInt`および`CollectionIndexString`同等のもの
--- | ---
[COUNT] | `Count returns int`
DELETE | `RemoveAll() returns <UDT_type>`
削除 (n) | `Remove(@index int) returns <UDT_type>`
DELETE (m, n) | `RemoveRange(@indexFrom int, @indexTo int) returns <UDT_type>`
EXISTS | `ContainsElement(@index int) returns bit`
できる | `Extend() returns <UDT_type>`
拡張 (n) | `Extend() returns <UDT_type>`
拡張 (n, i) | `ExtendDefault(@count int, @def int) returns <UDT_type>`
FIRST | `First() returns int`
LAST | `Last() returns int`
LIMIT | 該当なし
PRIOR | `Prior(@current int) returns int`
NEXT | `Next(@current int) returns int`
TRIM | `Trim() returns <UDT_type>`
TRIM (n) | `TrimN(@count int) returns <UDT_type>`

## <a name="bulk-collect-operation"></a>一括収集操作

SSMA は`BULK COLLECT INTO` 、ステートメントを`SELECT ... FOR XML PATH` SQL Server ステートメントに変換します。その結果は、次のいずれかの関数にラップされます。

* `ssma_oracle.fn_bulk_collect2CollectionSimple`
* `ssma_oracle.fn_bulk_collect2CollectionComplex`

選択は、ターゲットオブジェクトの種類によって異なります。 これらの関数は、、 `CollectionIndexInt` `CollectionIndexString`および`Record`型で解析できる XML 値を返します。 特別な`AssignData`関数は、XML ベースのコレクションを UDT に割り当てます。

SSMA は、3種類`BULK COLLECT INTO`のステートメントを認識します。

### <a name="the-collection-contains-elements-with-scalar-types-and-the-select-list-contains-one-column"></a>コレクションにはスカラー型の要素が含まれ`SELECT` 、リストには1つの列が含まれます。

```sql
-- Oracle
SELECT column_name_1
BULK COLLECT INTO <collection_name_1>
FROM <data_source>

-- SQL Server
SET @<collection_name_1> =
    @<collection_name_1>.AssignData(
        ssma_oracle.fn_bulk_collect2CollectionSimple(
            (SELECT column_name_1 FROM <data_source> FOR XML PATH)))
```

### <a name="the-collection-contains-elements-with-record-types-and-the-select-list-contains-one-column"></a>コレクションにはレコード型の要素が含まれ`SELECT` 、リストには1つの列が含まれます。

```sql
-- Oracle
SELECT
    column_name_1[, column_name_2...]
BULK COLLECT INTO
    <collection_name_1>
FROM
    <data_source>

-- SQL Server
SET @<collection_name_1> =
    @<collection_name_1>.AssignData(
        ssma_oracle.fn_bulk_collect2CollectionComplex(
            (SELECT
                column_name_1 as [collection_name_1_element_field_name_1],
                column_name_2 as [collection_name_1_element_field_name_2]
            FROM <data_source>
            FOR XML PATH)))
```

### <a name="the-collection-contains-elements-with-scalar-type-and-the-select-list-contains-multiple-columns"></a>コレクションにスカラー型の要素が含まれて`SELECT`いますが、リストに複数の列が含まれています。

```sql
-- Oracle
SELECT
    column_name_1[, column_name_2 ...]
BULK COLLECT INTO
    <collection_name_1>[, <collection_name_2> ...]
FROM
    <data_source>

-- SQL Server
;WITH bulkC AS (
    SELECT
        column_name_1 [collection_name_1_element_field_name_1],
        column_name_2 [collection_name_1_element_field_name_2]
    FROM
        <data_source>
)
SELECT
    @<collection_name_1> =
        @<collection_name_1>.AssignData(
            ssma_oracle.fn_bulk_collect2CollectionSimple(
                (SELECT
                    [collection_name_1_element_field_name_1]
                FROM
                    bulkC
                FOR XML PATH))),
    @<collection_name_2> =
        @<collection_name_2>.AssignData(
            ssma_oracle.fn_bulk_collect2CollectionSimple(
                (SELECT
                    [collection_name_1_element_field_name_2]
                FROM bulkC
                FOR XML PATH)))
```

## <a name="select-into-record"></a>SELECT INTO レコード

Oracle クエリの結果が PL/SQL レコード変数に保存されている場合は、ssma の [レコードを分離された**変数の一覧として変換**する ([**ツール**] メニューの [**プロジェクトの設定**]、[**一般的な** -> **変換**] の順に選択できます) に応じて、2つのオプションがあります。 この設定の値が **[はい]** (既定値) の場合、ssma ではレコードの種類のインスタンスは作成されません。 代わりに、レコードフィールドごとに個別の Transact-sql 変数を作成することにより、レコードを編成フィールドに分割します。 設定が [**いいえ**] の場合、レコードはインスタンス化され、メソッドを使用`Set`して各フィールドに値が割り当てられます。
