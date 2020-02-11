---
title: CLR パラメーターデータのマッピング |Microsoft Docs
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
ms.openlocfilehash: 530db4d31d3db4773713816f1b68404990997512
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081311"
---
# <a name="mapping-clr-parameter-data"></a>CLR パラメーター データのマッピング
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  次の表は[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 **SqlTypes**名前空間のの[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]共通言語ランタイム (CLR) に相当するデータ型と、それらのネイティブ CLR に .NET Framework 相当するものを示しています。  
  
||||  
|-|-|-|  
|**SQL Server のデータ型**|型 (System.Data.SqlTypes または Microsoft.SqlServer.Types)|**CLR データ型 (.NET Framework)**|  
|**bigint**|**SqlInt64**|**Int64、Null\<許容の int64>**|  
|**binary**|**SqlBytes、Sqlbytes**|**Byte []**|  
|**bit**|**SqlBoolean**|**ブール値、\<null 許容のブール値>**|  
|**char**|なし|なし|  
|**g**|なし|なし|  
|**date**|**SqlDateTime**|**DateTime、Nullable\<datetime>**|  
|**DATETIME**|**SqlDateTime**|**DateTime、Nullable\<datetime>**|  
|**datetime2**|なし|**DateTime、Nullable\<datetime>**|  
|**DATETIMEOFFSET**|**なし**|**DateTimeOffset、Null\<値を許容する datetimeoffset>**|  
|**decimal**|**SqlDecimal**|**Decimal、Nullable\<decimal>**|  
|**float**|**SqlDouble**|**Double、Null\<値を許容する double>**|  
|**geography**|**SqlGeography**<br /><br /> **Sqlgeography**は、SQL Server と共にインストールされ、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [feature pack](https://www.microsoft.com/download/details.aspx?id=52676)からダウンロードできる、SqlServer に定義されています。|なし|  
|**geometry**|**SqlGeometry**<br /><br /> **Sqlgeometry**は、SQL Server と共にインストールされ、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [feature pack](https://www.microsoft.com/download/details.aspx?id=52676)からダウンロードできる、SqlServer で定義されています。|なし|  
|**hierarchyid**|**SqlHierarchyId**<br /><br /> **Sqlhierarchyid**は、SQL Server と共にインストールされ、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [feature pack](https://www.microsoft.com/download/details.aspx?id=52676)からダウンロードできる、SqlServer に定義されています。|なし|  
|**絵**|なし|なし|  
|**int**|**SqlInt32**|**Int32、Nullable\<int32>**|  
|**money**|**SqlMoney**|**Decimal、Nullable\<decimal>**|  
|**nchar**|**SqlChars、SqlString**|**String, Char[]**|  
|**ntext**|なし|なし|  
|**番号**|**SqlDecimal**|**Decimal、Nullable\<decimal>**|  
|**nvarchar**|**SqlChars、SqlString**<br /><br /> **Sqlchars**は、データの転送とアクセスに適しています。また、 **SQLString**は、文字列操作を実行する場合に適しています。|**String, Char[]**|  
|**nvarchar (1)、nchar (1)**|**SqlChars、SqlString**|**Char、String、Char []、Null\<値を許容する char>**|  
|**本当の**|**Sqlsingle** ( **sqlsingle**の範囲は**real**より大きい)|**単一の Null\<許容の単一>**|  
|**rowversion**|なし|**Byte []**|  
|**smallint**|**SqlInt16**|**Int16、Nullable\<int16>**|  
|**smallmoney**|**SqlMoney**|**Decimal、Nullable\<decimal>**|  
|**sql_variant**|なし|**Object**|  
|**一覧**|なし|なし|  
|**本文**|なし|なし|  
|**time**|なし|**TimeSpan、Nullable\<timespan>**|  
|**timestamp**|なし|なし|  
|**tinyint**|**SqlByte**|**バイト、Null\<値を許容するバイト>**|  
|**UNIQUEIDENTIFIER**|**SqlGuid**|**Guid、Null\<許容 guid>**|  
|**ユーザー定義型 (UDT)**|なし|同じアセンブリまたは依存アセンブリ内のユーザー定義型にバインドされている同じクラス|  
|**varbinary**|**SqlBytes、Sqlbytes**|**Byte []**|  
|**varbinary (1)、binary (1)**|**SqlBytes、Sqlbytes**|**byte、Byte []、Null\<値を許容するバイト>**|  
|**varchar**|なし|なし|  
|**xml**|**SqlXml**|なし|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>out パラメーターによるデータ型の自動変換  
 Clr メソッドは、入力パラメーターがシステムの clr データ型である場合に、入力パラメーターを**out**修飾子 (microsoft Visual C#) または** \<out () > ByRef** (microsoft Visual Basic) でマークすることによって、呼び出し元のコードまたはプログラムに情報を返すことができ**ます。 SqlTypes**名前空間、および呼び出し元のプログラムは、対応[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]するデータ型を入力パラメーターとして指定します。 CLR メソッドがデータ型を返すと、型変換が自動的に行われます。  
  
 たとえば、次の clr ストアドプロシージャには、 **out** (C#) または** \<out () > ByRef** (Visual Basic) でマークされている**SqlInt32** CLR データ型の入力パラメーターがあります。  
  
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
  
 アセンブリがデータベースに構築されて作成されると、次の Transact-sql を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用してストアドプロシージャが作成されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。これは、出力パラメーターとして**int**のデータ型を指定します。  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 CLR ストアドプロシージャを呼び出すと、 **SqlInt32**データ型が自動的に**int**データ型に変換され、呼び出し元のプログラムに返されます。  
  
 ただし、out パラメーターにより自動的にすべての CLR データ型を同等な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型に変換できるとは限りません。 次の表に、これらの例外を示します。  
  
|||  
|-|-|  
|**CLR データ型 (SQL Server)**|**SQL Server のデータ型**|  
|**位**|smallmoney|  
|**SqlMoney**|smallmoney|  
|**位**|money|  
|**/**|smalldatetime|  
|**SQLDateTime**|smalldatetime|  
  
## <a name="change-history"></a>変更履歴  
  
|変更内容|  
|---------------------|  
|マッピングテーブルに**Sqlgeography**、 **sqlgeography**、および**sqlgeography**型を追加しました。|  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
