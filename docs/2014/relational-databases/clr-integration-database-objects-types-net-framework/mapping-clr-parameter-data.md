---
title: CLR パラメーターデータのマッピング |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlBinary data type
- SqlInt16 data type
- SqlMoney data type
- SqlString data type
- SqlSingle data type
- data types [CLR integration]
- SqlInt64 data type
- SqlDateTime data type
- SqlXml data type
- SqlBoolean data type
- SqlDecimal data type
- SqlBytes data type
- mapping data types [CLR integration]
- SqlChars data type
- SqlInt32 data type
ms.assetid: 89b43ee9-b9ad-4281-a4bf-c7c8d116daa2
author: rothja
ms.author: jroth
ms.openlocfilehash: 70274fcc16caec38d4d960f89fe586b32662dc57
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84954782"
---
# <a name="mapping-clr-parameter-data"></a>CLR パラメーター データのマッピング
  次の表は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型、名前空間のの共通言語ランタイム (CLR) に相当するデータ型、および .NET Framework 内のネイティブ CLR に相当するものを示して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `System.Data.SqlTypes` [!INCLUDE[msCoName](../../includes/msconame-md.md)] います。  
  
||||  
|-|-|-|  
|**SQL Server のデータ型**|型 (System.Data.SqlTypes または Microsoft.SqlServer.Types)|**CLR データ型 (.NET Framework)**|  
|`bigint`|`SqlInt64`|**Int64、Nullable\<Int64>**|  
|`binary`|`SqlBytes, SqlBinary`|`Byte[]`|  
|`bit`|`SqlBoolean`|**ブール型、Null 値を許容\<Boolean>**|  
|`char`|None|None|  
|`cursor`|None|None|  
|`date`|`SqlDateTime`|**DateTime、Nullable\<DateTime>**|  
|`datetime`|`SqlDateTime`|**DateTime、Nullable\<DateTime>**|  
|`datetime2`|None|**DateTime、Nullable\<DateTime>**|  
|`DATETIMEOFFSET`|`None`|**DateTimeOffset、Nullable\<DateTimeOffset>**|  
|`decimal`|`SqlDecimal`|**Decimal、Nullable\<Decimal>**|  
|`float`|`SqlDouble`|**Double、Nullable\<Double>**|  
|`geography`|`SqlGeography`<br /><br /> `SqlGeography`は Microsoft.SqlServer.Types.dll で定義され、SQL Server と共にインストールされ、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [feature pack](https://www.microsoft.com/download/details.aspx?id=53164)からダウンロードできます。|None|  
|`geometry`|`SqlGeometry`<br /><br /> `SqlGeometry`は Microsoft.SqlServer.Types.dll で定義され、SQL Server と共にインストールされ、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [feature pack](https://www.microsoft.com/download/details.aspx?id=53164)からダウンロードできます。|None|  
|`hierarchyid`|`SqlHierarchyId`<br /><br /> `SqlHierarchyId`は Microsoft.SqlServer.Types.dll で定義され、SQL Server と共にインストールされ、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [feature pack](https://www.microsoft.com/download/details.aspx?id=53164)からダウンロードできます。|None|  
|`image`|None|None|  
|`int`|`SqlInt32`|**Int32、Nullable\<Int32>**|  
|`money`|`SqlMoney`|**Decimal、Nullable\<Decimal>**|  
|`nchar`|`SqlChars, SqlString`|`String, Char[]`|  
|`ntext`|None|None|  
|`numeric`|`SqlDecimal`|**Decimal、Nullable\<Decimal>**|  
|`nvarchar`|`SqlChars, SqlString`<br /><br /> `SQLChars` はデータの転送とアクセスに適しています。また、`SQLString` は文字列操作に適しています。|`String, Char[]`|  
|`nvarchar(1), nchar(1)`|`SqlChars, SqlString`|**Char、String、Char []、Nullable\<char>**|  
|`real`|`SqlSingle`(`SqlSingle` の範囲内。ただし `real` より大きい)|**Single、Nullable\<Single>**|  
|`rowversion`|None|`Byte[]`|  
|`smallint`|`SqlInt16`|**Int16、Nullable\<Int16>**|  
|`smallmoney`|`SqlMoney`|**Decimal、Nullable\<Decimal>**|  
|`sql_variant`|None|`Object`|  
|`table`|None|None|  
|`text`|None|None|  
|`time`|None|**TimeSpan、Nullable\<TimeSpan>**|  
|`timestamp`|None|None|  
|`tinyint`|`SqlByte`|**Byte、Nullable\<Byte>**|  
|`uniqueidentifier`|`SqlGuid`|**Guid、Nullable\<Guid>**|  
|`User-defined type(UDT)`|None|同じアセンブリまたは依存アセンブリ内のユーザー定義型にバインドされている同じクラス|  
|**varbinary**|`SqlBytes, SqlBinary`|`Byte[]`|  
|`varbinary(1), binary(1)`|`SqlBytes, SqlBinary`|**byte、Byte []、Nullable\<byte>**|  
|`varchar`|None|None|  
|`xml`|`SqlXml`|None|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>out パラメーターによるデータ型の自動変換  
 CLR メソッドでは、入力パラメーターを `out` 修飾子 (Microsoft Visual C#) または `<Out()> ByRef` (Microsoft Visual Basic) でマークすることにより、呼び出し側のコードまたはプログラムに情報を返すことができます。`System.Data.SqlTypes` 名前空間での入力パラメーターが CLR データ型で、呼び出し側のプログラムがこれと同等な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を入力パラメーターとして指定する場合、CLR メソッドがデータ型を返すと、自動的に型の変換が行われます。  
  
 たとえば、次の CLR ストアド プロシージャには、`SqlInt32` (C#) または `out` (Visual Basic) でマークされている `<Out()> ByRef` CLR データ型の入力パラメーターがあります。  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ ... }  
```  
  
```vb  
<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
...  
End Sub  
```  
  
 データベースでアセンブリがビルドおよび作成された後、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、OUTPUT パラメーターとして `int` の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を指定する、次の Transact-SQL によりストアド プロシージャが作成されます。  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 CLR ストアド プロシージャが呼び出されると、`SqlInt32` データ型は自動的に `int` データ型に変換され、呼び出し側のプログラムに返されます。  
  
 ただし、out パラメーターにより自動的にすべての CLR データ型を同等な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型に変換できるとは限りません。 次の表に、これらの例外を示します。  
  
|||  
|-|-|  
|**CLR データ型 (SQL Server)**|**SQL Server のデータ型**|  
|`Decimal`|smallmoney|  
|`SqlMoney`|smallmoney|  
|`Decimal`|money|  
|`DateTime`|smalldatetime|  
|`SQLDateTime`|smalldatetime|  
  
## <a name="change-history"></a>変更履歴  
  
|変更内容|  
|---------------------|  
|マッピング テーブルに `SqlGeography` 型、`SqlGeometry` 型、および `SqlHierarchyId` 型を追加しました。|  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](sql-server-data-types-in-the-net-framework.md)  
  
  
