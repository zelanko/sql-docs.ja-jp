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
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c256bc9ecc0e518bb54d206a04f36d2b736500d8
ms.lasthandoff: 04/11/2017

---
# <a name="how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server"></a>FOR JSON が SQL Server データ型を JSON データ型に変換する方法 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  **FOR JSON** 句は、次の規則に従って、JSON 出力で SQL Server データ型を JSON 型に変換します。  
  
|カテゴリ|SQL Server データ型|JSON データ型|  
|--------------|--------------|---------------|  
|文字型と文字列型|(n)(var)(char)|string|  
|数値型|int、bigint、float、decimal、numeric|number|  
|ビット型|bit|Boolean (true または false)|  
|日付型と時刻型|date、datetime、datetime2、time、datetimeoffset|string|  
|バイナリ型|varbinary、binary、image、timestamp、rowversion|BASE64 エンコード文字列|  
|CLR 型|CLR、geometry、geography|サポートされていません。 これらの型はエラーを返します。<br /><br /> SELECT ステートメントで CAST または CONVERT を使用するか、CLR プロパティまたはメソッドを使用して、JSON 型に変換できるデータ型にデータを変換します。 たとえば、任意の CLR 型には **ToString()** を使用し、geometry 型には **STAsText()** を使用します。 次に、JSON 出力値の型が、SELECT ステートメントで使用している変換の戻り値の型から導き出されます。|  
|その他の種類|uniqueidentifier、money|string|  
  
## <a name="see-also"></a>参照  
 [FOR JSON を使用してクエリ結果を JSON として書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  

