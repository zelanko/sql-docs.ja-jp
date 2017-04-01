---
title: "R データ型の処理 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/31/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5df99e1c-a89a-42c1-9d68-ffe8d9577c94
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# R データ型の処理
  一方 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] いくつかの多数のデータ型をサポート R は限られた数のスカラー データ型 (数値、複雑な論理、文字、整数の日付/時刻と生) です。 そのため、R スクリプトの  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータを使用すると、通常とは異なる結果が発生する可能性があります。  
  
-   データは、暗黙的に互換性のあるデータ型に変換されます。  
  
-   データは暗黙的に変換できず、エラーが返されます。  
  
 一般的に、特定のデータ型またはデータ構造を R で使用する方法についてわからない点がある場合は、  `str()` 関数を使用して内部構造と R オブジェクトの種類を取得してください。 この関数の結果は R コンソールに出力され、 **の** [メッセージ] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]タブのクエリ結果で確認することもできます。  
  
 特定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] R では、データ型はサポートされていないが、R スクリプトでデータの列を使用する必要がある、使用することをお勧めします [CAST および CONVERT & #40 です。Transact SQL と #41;](../../t-sql/functions/cast-and-convert-transact-sql.md) データが変換を入力することを確認する関数は、R スクリプト内のデータを使用する前に意図したとおりに実行されます。  
  
 詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を参照してください [データの型と #40 です。Transact SQL と #41 です。](../../t-sql/data-types/data-types-transact-sql.md)  
  
## R と SQL Server 間のデータ型の変換  
 次の表は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータを R スクリプトで使用する場合と、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に返された場合のデータ型と値の変化の一覧です。  
  
|||||  
|-|-|-|-|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 型|R クラス| **RESULT SET**の型|コメント|  
|**smalldatetime**|`POSIXct`|**datetime**|GMT として表現されます|  
|**smallmoney**|`numeric`|**float**||  
|**datetime**|`POSIXct`|**datetime**|GMT として表現されます|  
|**money**|`numeric`|**float**||  
|**uniqueidentifier**|`character`|**varchar(max)**||  
|**numeric(p,s)**|`numeric`|**float**||  
|**decimal(p,s)**|`numeric`|**float**||  
|**date**|`POSIXct`|**datetime**|GMT として表現されます|  
|**tinyint**|`integer`|**int**||  
|**bit**|`logical`|**bit**||  
|**smallint**|`integer`|**int**||  
|**int**|`integer`|**int**||  
|**float**|`numeric`|**float**||  
|**real**|`numeric`|**float**||  
|**bigint**|`numeric`|**float**||  
|**binary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|入力パラメーターと出力にのみ使用できます。|  
|**char(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||  
|**varbinary (n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|入力パラメーターと出力にのみ使用できます。|  
|**varchar (n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||  
|**varbinary(max)**|`raw`|**varbinary(max)**|入力パラメーターと出力にのみ使用できます。|  
  
## データ型の変換の例  
 次のクエリは、一連からの値を取得、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブル、およびストアド プロシージャを使用して  [sp_execute_external_script & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) R のランタイムを使用して値を出力します。  
  
```  
CREATE TABLE MyTable (    
 c1 int,    
 c2 varchar(10),    
 c3 uniqueidentifier    
);    
go    
INSERT MyTable VALUES(1, 'Hello', newid());    
INSERT MyTable VALUES(-11, 'world', newid());    
SELECT * FROM MyTable;    
  
EXECUTE sp_execute_external_script    
 @language = N'R'    
 , @script = N'    
inputDataSet["cR"] <- c(4, 2)    
str(inputDataSet)    
outputDataSet <- inputDataSet'    
 , @input_data_1 = N'SELECT c1, c2, c3 FROM MyTable'    
 , @input_data_1_name = N'inputDataSet'    
 , @output_data_1_name = N'outputDataSet'    
 WITH RESULT SETS((C1 int, C2 varchar(max), C3 varchar(max), C4 float));  
```  
  
 **[結果]**  
  
||||||  
|-|-|-|-|-|  
||C1|C2|C3|C4|  
|1|1|Hello|6e225611-4b58-4995-a0a5-554d19012ef1|4|  
|1|-11|world|6732ea46-2d5d-430b-8ao1-86e7f3351c3e|2|  
  
 R で `str` 関数を使用すると、出力データのスキーマが取得されます。 この関数からは、次の情報が返されます。  
  
```  
'data.frame':2 obs. of  4 variables:   
 $ c1: int  1 -11   
 $ c2: Factor w/ 2 levels "Hello","world": 1 2   
 $ c3: Factor w/ 2 levels "6732EA46-2D5D-430B-8A01-86E7F3351C3E",..: 2 1   
 $ cR: num  4 2  
```  
  
 その結果から、次のデータ型の変換がこのクエリの一部として暗黙的に実行されたことがわかります。  
  
-   **列 C1**。 列として表されます **int** で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 、`integer` r でと **int** 出力結果セットにします。  
  
     型変換は実行されていません。  
  
-   **列 C2**。 列は、として表されます。 **varchar (10)** で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 、`factor` r でと **varchar (max)** 出力します。  
  
     出力の変更方法に注意してください。R (係数または通常の文字列) から任意の文字列として表されます **varchar (max)**, 、文字列の長さ内容に関係なく。  
  
-   **列 C3**。  列は、として表されます。 **uniqueidentifier** で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 、`character` r でと **varchar (max)** 出力にします。  
  
     発生したデータ型の変換に注目してください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サポートしています、 **uniqueidentifier** が R しません。 そのため、識別子は、文字列として表されます。 します。  
  
-   **列 C4**。 この列には、元のデータには存在しない、R スクリプトで生成された値が含まれます。  
 
 ## 参照
 [SQL Server R Services の機能とタスク](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)
  
  