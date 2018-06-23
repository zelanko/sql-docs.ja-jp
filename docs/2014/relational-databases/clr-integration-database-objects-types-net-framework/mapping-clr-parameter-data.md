---
title: CLR パラメーター データのマッピング |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 69
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6a7c442f3bf102c668f0889f008b8a87205b2257
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178023"
---
# <a name="mapping-clr-parameter-data"></a>CLR パラメーター データのマッピング
  次の表にリスト[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型の場合、共通言語ランタイム (CLR) 用の同等の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で、`System.Data.SqlTypes`名前空間、およびネイティブ CLR の同等の[!INCLUDE[msCoName](../../includes/msconame-md.md)].NET Framework。  
  
||||  
|-|-|-|  
|**SQL Server データ型**|型 (System.Data.SqlTypes または Microsoft.SqlServer.Types)|**CLR データ型 (.NET Framework)**|  
|`bigint`|`SqlInt64`|**Int64 では、null 許容\<Int64 >**|  
|`binary`|`SqlBytes, SqlBinary`|`Byte[]`|  
|`bit`|`SqlBoolean`|**ブール値、null 許容\<ブール値 >**|  
|`char`|なし|なし|  
|`cursor`|なし|なし|  
|`date`|`SqlDateTime`|**DateTime、null 許容\<DateTime >**|  
|`datetime`|`SqlDateTime`|**DateTime、null 許容\<DateTime >**|  
|`datetime2`|なし|**DateTime、null 許容\<DateTime >**|  
|`DATETIMEOFFSET`|`None`|**DateTimeOffset では、null 許容\<DateTimeOffset >**|  
|`decimal`|`SqlDecimal`|**Null 値は 10 進\<Decimal >**|  
|`float`|`SqlDouble`|**Double 型、null 許容\<二重 >**|  
|`geography`|`SqlGeography`<br /><br /> `SqlGeography` Microsoft.SqlServer.Types.dll に定義、SQL Server と共にインストールされからダウンロードできます、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][機能パック](http://go.microsoft.com/fwlink/?LinkId=131220)です。|なし|  
|`geometry`|`SqlGeometry`<br /><br /> `SqlGeometry` Microsoft.SqlServer.Types.dll に定義、SQL Server と共にインストールされからダウンロードできます、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][機能パック](http://go.microsoft.com/fwlink/?LinkId=131220)です。|なし|  
|`hierarchyid`|`SqlHierarchyId`<br /><br /> `SqlHierarchyId` Microsoft.SqlServer.Types.dll に定義、SQL Server と共にインストールされからダウンロードできます、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][機能パック](http://go.microsoft.com/fwlink/?LinkId=131220)です。|なし|  
|`image`|なし|なし|  
|`int`|`SqlInt32`|**Int32、null 許容\<Int32 >**|  
|`money`|`SqlMoney`|**Null 値は 10 進\<Decimal >**|  
|`nchar`|`SqlChars, SqlString`|`String, Char[]`|  
|`ntext`|なし|なし|  
|`numeric`|`SqlDecimal`|**Null 値は 10 進\<Decimal >**|  
|`nvarchar`|`SqlChars, SqlString`<br /><br /> `SQLChars` はデータの転送とアクセスに適しています。また、`SQLString` は文字列操作に適しています。|`String, Char[]`|  
|`nvarchar(1), nchar(1)`|`SqlChars, SqlString`|**Char、String、Char、Nullable\<char >**|  
|`real`|`SqlSingle`(`SqlSingle` の範囲内。ただし `real` より大きい)|**Null 値の 1 つ\<単一 >**|  
|`rowversion`|なし|`Byte[]`|  
|`smallint`|`SqlInt16`|**Int16 型、null 許容\<Int16 >**|  
|`smallmoney`|`SqlMoney`|**Null 値は 10 進\<Decimal >**|  
|`sql_variant`|なし|`Object`|  
|`table`|なし|なし|  
|`text`|なし|なし|  
|`time`|なし|**TimeSpan、null 許容\<TimeSpan >**|  
|`timestamp`|なし|なし|  
|`tinyint`|`SqlByte`|**Byte、null 許容\<バイト >**|  
|`uniqueidentifier`|`SqlGuid`|**Guid、null 許容\<Guid >**|  
|`User-defined type(UDT)`|なし|同じアセンブリまたは依存アセンブリ内のユーザー定義型にバインドされている同じクラス|  
|**varbinary**|`SqlBytes, SqlBinary`|`Byte[]`|  
|`varbinary(1), binary(1)`|`SqlBytes, SqlBinary`|**バイト、byte[]、Nullable\<バイト >**|  
|`varchar`|なし|なし|  
|`xml`|`SqlXml`|なし|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>out パラメーターによるデータ型の自動変換  
 CLR メソッドでは、入力パラメーターを `out` 修飾子 (Microsoft Visual C#) または `<Out()> ByRef` (Microsoft Visual Basic) でマークすることにより、呼び出し側のコードまたはプログラムに情報を返すことができます。`System.Data.SqlTypes` 名前空間での入力パラメーターが CLR データ型で、呼び出し側のプログラムがこれと同等な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を入力パラメーターとして指定する場合、CLR メソッドがデータ型を返すと、自動的に型の変換が行われます。  
  
 たとえば、次の CLR ストアド プロシージャには、`SqlInt32` (C#) または `out` (Visual Basic) でマークされている `<Out()> ByRef` CLR データ型の入力パラメーターがあります。  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ … }  
```  
  
```vb  
<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
…  
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
|**CLR データ型 (SQL Server)**|**SQL Server データ型**|  
|`Decimal`|SMALLMONEY|  
|`SqlMoney`|SMALLMONEY|  
|`Decimal`|money|  
|`DateTime`|smalldatetime|  
|`SQLDateTime`|smalldatetime|  
  
## <a name="change-history"></a>変更履歴  
  
|変更内容|  
|---------------------|  
|マッピング テーブルに `SqlGeography` 型、`SqlGeometry` 型、および `SqlHierarchyId` 型を追加しました。|  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](sql-server-data-types-in-the-net-framework.md)  
  
  