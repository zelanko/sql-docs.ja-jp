---
title: "CLR パラメーター データのマッピング |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
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
caps.latest.revision: "71"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: bee49e277d3492dc93bcdf29b65c1c3007cebe50
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="mapping-clr-parameter-data"></a>CLR パラメーター データのマッピング
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]次の表にリスト[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型の場合、共通言語ランタイム (CLR) 用の同等の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で、 **System.Data.SqlTypes**名前空間、およびネイティブ CLR の同等で、[!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET フレームワークです。  
  
||||  
|-|-|-|  
|**SQL Server データ型**|型 (System.Data.SqlTypes または Microsoft.SqlServer.Types)|**CLR データ型 (.NET Framework)**|  
|**bigint**|**SqlInt64**|**Int64 では、null 許容\<Int64 >**|  
|**[バイナリ]**|**SqlBytes、SqlBinary**|**Byte[]**|  
|**bit**|**SqlBoolean**|**ブール値、null 許容\<ブール値 >**|  
|**char**|なし|なし|  
|**カーソル (cursor)**|なし|なし|  
|**date**|**SqlDateTime**|**DateTime、null 許容\<DateTime >**|  
|**datetime**|**SqlDateTime**|**DateTime、null 許容\<DateTime >**|  
|**datetime2**|なし|**DateTime、null 許容\<DateTime >**|  
|**DATETIMEOFFSET**|**なし**|**DateTimeOffset では、null 許容\<DateTimeOffset >**|  
|**decimal**|**SqlDecimal**|**Null 値は 10 進\<Decimal >**|  
|**float**|**SqlDouble**|**Double 型、null 許容\<二重 >**|  
|**geography**|**SqlGeography**<br /><br /> **SqlGeography** Microsoft.SqlServer.Types.dll は、SQL Server と共にインストールされからダウンロードできますで定義された、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [機能パック](https://www.microsoft.com/download/details.aspx?id=52676)です。|なし|  
|**geometry**|**SqlGeometry**<br /><br /> **SqlGeometry** Microsoft.SqlServer.Types.dll は、SQL Server と共にインストールされからダウンロードできますで定義された、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [機能パック](https://www.microsoft.com/download/details.aspx?id=52676)です。|なし|  
|**hierarchyid**|**SqlHierarchyId**<br /><br /> **SqlHierarchyId** Microsoft.SqlServer.Types.dll は、SQL Server と共にインストールされからダウンロードできますで定義された、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [機能パック](https://www.microsoft.com/download/details.aspx?id=52676)です。|なし|  
|**image**|なし|なし|  
|**int**|**SqlInt32**|**Int32、null 許容\<Int32 >**|  
|**money**|**SqlMoney**|**Null 値は 10 進\<Decimal >**|  
|**nchar**|**SqlChars、SqlString**|**String、Char**|  
|**ntext**|なし|なし|  
|**numeric**|**SqlDecimal**|**Null 値は 10 進\<Decimal >**|  
|**nvarchar**|**SqlChars、SqlString**<br /><br /> **SQLChars**データ転送とアクセスに適しているは、 **SQLString**文字列操作を実行するための優れた一致です。|**String、Char**|  
|**nvarchar(1)、nchar (1)**|**SqlChars、SqlString**|**Char、String、Char、Nullable\<char >**|  
|**real**|**SqlSingle** (範囲**SqlSingle**、ただしよりも大きいは**実際**)|**Null 値の 1 つ\<単一 >**|  
|**rowversion**|なし|**Byte[]**|  
|**smallint**|**SqlInt16**|**Int16 型、null 許容\<Int16 >**|  
|**smallmoney**|**SqlMoney**|**Null 値は 10 進\<Decimal >**|  
|**sql_variant**|なし|**オブジェクト**|  
|**テーブル**|なし|なし|  
|**text**|なし|なし|  
|**time**|なし|**TimeSpan、null 許容\<TimeSpan >**|  
|**timestamp**|なし|なし|  
|**tinyint**|**SqlByte**|**Byte、null 許容\<バイト >**|  
|**uniqueidentifier**|**SqlGuid**|**Guid、null 許容\<Guid >**|  
|**ユーザー定義の type(UDT)**|なし|同じアセンブリまたは依存アセンブリ内のユーザー定義型にバインドされている同じクラス|  
|**varbinary**|**SqlBytes、SqlBinary**|**Byte[]**|  
|**varbinary(1)、binary(1)**|**SqlBytes、SqlBinary**|**バイト、byte[]、Nullable\<バイト >**|  
|**varchar**|なし|なし|  
|**xml**|**SqlXml**|なし|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>out パラメーターによるデータ型の自動変換  
 CLR メソッドは、呼び出し元のコードまたはプログラムに情報を入力パラメーターをマークすることで返すことができます、**アウト**修飾子 (Microsoft Visual C# の場合) または **\<Out() > ByRef** (Microsoft Visual Basic)入力パラメーターが CLR データ型がかどうか、 **System.Data.SqlTypes**名前空間と呼び出し元のプログラムは、それと等価なを指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型、入力パラメーターとして、型の変換が自動的に行われます。ときに、CLR メソッドは、データ型を返します。  
  
 たとえば、次の CLR ストアド プロシージャは、入力パラメーターとして**SqlInt32**でマークされている CLR データ型**アウト**(c#) または **\<Out() > ByRef** (Visual Basic の場合):  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ … }  
```  
  
```vb  
\<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( \<Out()> ByRef value As SqlInt32)  
…  
End Sub  
```  
  
 ストアド プロシージャが作成された後、アセンブリがビルドされ、データベースが作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を指定する次 transact-sql、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータ型**int**出力パラメーターとして。  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 CLR ストアド プロシージャが呼び出されると、 **SqlInt32**データ型が自動的に変換、 **int**データ型、呼び出し元のプログラムに返されます。  
  
 ただし、out パラメーターにより自動的にすべての CLR データ型を同等な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型に変換できるとは限りません。 次の表に、これらの例外を示します。  
  
|||  
|-|-|  
|**CLR データ型 (SQL Server)**|**SQL Server データ型**|  
|**10 進数**|smallmoney|  
|**SqlMoney**|smallmoney|  
|**10 進数**|money|  
|**DateTime**|smalldatetime|  
|**SQLDateTime**|smalldatetime|  
  
## <a name="change-history"></a>変更履歴  
  
|変更内容|  
|---------------------|  
|追加**SqlGeography**、 **SqlGeometry**、および**SqlHierarchyId**型マッピング テーブルにします。|  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
