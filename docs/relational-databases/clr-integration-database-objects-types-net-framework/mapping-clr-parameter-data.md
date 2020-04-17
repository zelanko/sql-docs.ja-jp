---
title: CLR パラメータ データのマッピング |マイクロソフトドキュメント
description: この資料では、SQL Server のデータ型、SQL Server 用 CLR の対応するデータ型、および .NET Framework のネイティブ CLR の対応を一覧表示します。
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
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
ms.openlocfilehash: 360a94229b107e9f24bb2a769157c75cdeb3c143
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488465"
---
# <a name="mapping-clr-parameter-data"></a>CLR パラメーター データのマッピング
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  次の表は[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、データ型、**共通言語**ランタイム (CLR)[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の対応する名前空間、および .NET Framework のネイティブ CLR の対応を示しています。  
  
||||  
|-|-|-|  
|**SQL サーバーのデータ型**|型 (System.Data.SqlTypes または Microsoft.SqlServer.Types)|**CLR データ型 (.NET Framework)**|  
|**bigint**|**SqlInt64**|**Int64, Null\<許容 Int64>**|  
|**[バイナリ]**|**Sql バイト、Sql バイナリ**|**バイト[]**|  
|**bit**|**SqlBoolean**|**ブール値、Null\<許容ブール>**|  
|**char**|なし|なし|  
|**cursor**|なし|なし|  
|**date**|**Sqldatetime**|**日付時刻、null\<許容日時>**|  
|**datetime**|**Sqldatetime**|**日付時刻、null\<許容日時>**|  
|**datetime2**|なし|**日付時刻、null\<許容日時>**|  
|**Datetimeoffset**|**なし**|**>値を指定\<します。**|  
|**decimal**|**10 進数**|**10 進数\<、null 許容 10 進数>**|  
|**float**|**SqlDouble**|**ダブル、ヌル\<ブルダブル>**|  
|**geography**|**SqlGeography**<br /><br /> **SqlGeography**は、SQL Server と共にインストールされ、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][機能パック](https://www.microsoft.com/download/details.aspx?id=52676)からダウンロードできる Microsoft.SqlServer.Types.dll で定義されています。|なし|  
|**geometry**|**SqlGeometry**<br /><br /> **SqlGeometry**は、SQL Server と共にインストールされ、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][機能パック](https://www.microsoft.com/download/details.aspx?id=52676)からダウンロードできる Microsoft.SqlServer.Types.dll で定義されています。|なし|  
|**hierarchyid**|**SqlHierarchyId**<br /><br /> **SqlHierarchyId**は、SQL Server と共にインストールされ、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][機能パック](https://www.microsoft.com/download/details.aspx?id=52676)からダウンロードできる Microsoft.SqlServer.Types.dll で定義されています。|なし|  
|**image**|なし|なし|  
|**int**|**SqlInt32**|**Int32, Null\<許容 Int32>**|  
|**money**|**Sqlmoney**|**10 進数\<、null 許容 10 進数>**|  
|**nchar**|**を使用します。**|**String, Char[]**|  
|**ntext**|なし|なし|  
|**numeric**|**SqlDecimal**|**10 進数\<、null 許容 10 進数>**|  
|**nvarchar**|**を使用します。**<br /><br /> **SQLChars**は、データ転送とアクセスに適した一致であり **、SQLString**は文字列操作を実行する場合に適しています。|**String, Char[]**|  
|**nvarchar(1)、nchar(1)**|**を使用します。**|**文字、文字列、Char[]、null\<許容文字>**|  
|**real**|**SqlSingle** (ただし **、SqlSingle**の範囲は**実**数より大きい )|**単一、Null\<許容のシングル>**|  
|**rowversion**|なし|**バイト[]**|  
|**smallint**|**SqlInt16**|**Int16, Null\<許容 Int16>**|  
|**smallmoney**|**Sqlmoney**|**10 進数\<、null 許容 10 進数>**|  
|**sql_variant**|なし|**Object**|  
|**テーブル**|なし|なし|  
|**text**|なし|なし|  
|**time**|なし|**タイムスパン、null\<許容タイムスパン>**|  
|**timestamp**|なし|なし|  
|**tinyint**|**SqlByte**|**バイト、NULL\<許容バイト>**|  
|**uniqueidentifier**|**SqlGuid**|**GUID、Null\<許容 GUID>**|  
|**User-defined type(UDT)**|なし|同じアセンブリまたは依存アセンブリ内のユーザー定義型にバインドされている同じクラス|  
|**varbinary**|**Sql バイト、Sql バイナリ**|**バイト[]**|  
|**varbinary(1),バイナリ(1)**|**Sql バイト、Sql バイナリ**|**バイト、バイト[]、Null\<許容バイト>**|  
|**varchar**|なし|なし|  
|**xml**|**Sqlxml**|なし|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>out パラメーターによるデータ型の自動変換  
 CLR メソッドは、入力パラメーターに**Out**修飾子 (Microsoft Visual C#) または**System.Data.SqlTypes**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**\<Out()> ByRef** (Microsoft Visual Basic) を指定して、呼び出し元のコードまたはプログラムに情報を返すことができます。  
  
 たとえば、次の CLR ストアド プロシージャには、**出力**(C#) または**\<Out() > ByRef** (Visual Basic) でマークされている**SqlInt32** CLR データ型の入力パラメーターがあります。  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ ... }  
```  
  
```vb  
\<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( \<Out()> ByRef value As SqlInt32)  
...  
End Sub  
```  
  
 データベースでアセンブリを構築して作成すると、ストアド プロシージャは、次の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Transact-SQL[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して作成されます。 **int**  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 CLR ストアド プロシージャが呼び出されると **、SqlInt32**データ型は自動的に**int**データ型に変換され、呼び出し元のプログラムに返されます。  
  
 ただし、out パラメーターにより自動的にすべての CLR データ型を同等な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型に変換できるとは限りません。 次の表に、これらの例外を示します。  
  
|||  
|-|-|  
|**CLR データ型 (SQL Server)**|**SQL サーバーのデータ型**|  
|**Decimal**|smallmoney|  
|**Sqlmoney**|smallmoney|  
|**Decimal**|money|  
|**DateTime**|smalldatetime|  
|**Sqldatetime**|smalldatetime|  
  
## <a name="change-history"></a>変更履歴  
  
|変更内容|  
|---------------------|  
|マッピング テーブル**に SqlGeography** **、SqlGeometry**、および**SqlHierarchyId**型を追加しました。|  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
