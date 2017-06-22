---
title: "FOR JSON が SQL Server データ型を JSON データ型に変換する方法 (SQL Server) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/07/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON, data type conversion
ms.assetid: da356f06-efd0-4ea3-8157-77395bf790d7
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 527cb99c5caf0bb805e17f3b77b7d5e017e28ace
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server"></a>FOR JSON が SQL Server データ型を JSON データ型に変換する方法 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  **FOR JSON** 句は、次の規則に従って、JSON 出力で SQL Server データ型を JSON 型に変換します。  
  
|カテゴリ|SQL Server データ型|JSON データ型|  
|--------------|--------------|---------------|  
|文字型と文字列型|char、nchar、varchar、nvarchar|string|  
|数値型|int、bigint、float、decimal、numeric|number|  
|ビット型|bit|Boolean (true または false)|  
|日付型と時刻型|date、datetime、datetime2、time、datetimeoffset|string|  
|バイナリ型|varbinary、binary、image、timestamp、rowversion|BASE64 エンコード文字列|  
|CLR 型|geometry、geography、他の CLR 型|サポートされていません。 これらの型はエラーを返します。<br /><br /> SELECT ステートメントでは、キャストを使用して変換、または、ソース データを JSON 型に正常に変換できる SQL Server データ型に変換する CLR プロパティまたはメソッドを使用します。 たとえば、使用して**:stastext()** geometry 型、または使用**ToString()**任意の CLR 型のです。 JSON 出力値の型は、SELECT ステートメントに適用される変換の戻り値の型から導き出されます。|  
|その他の種類|uniqueidentifier、money|string|  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>詳細については、組み込みの JSON が SQL Server のサポート  
特定のソリューションの多くは、ケース、および推奨事項を使用して、参照してください、[組み込みの JSON サポートに関するブログの投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)SQL Server および Microsoft のプログラム マネージャー Jovan Popovic による Azure SQL データベースでします。
  
## <a name="see-also"></a>参照  
 [FOR JSON を使用してクエリ結果を JSON として書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  

