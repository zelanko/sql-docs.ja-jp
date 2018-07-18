---
title: WITHOUT_ARRAY_WRAPPER オプションを使用して JSON から角かっこを削除する | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.reviewer: douglasl
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- WITHOUT_ARRAY_WRAPPER
ms.assetid: aa86c2d1-458e-465f-abfa-75470137d054
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 86475dd98be8c8e5917aea2d6a728a384586e778
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423381"
---
# <a name="remove-square-brackets-from-json---withoutarraywrapper-option"></a>WITHOUT_ARRAY_WRAPPER オプションを使用して JSON から角かっこを削除する
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

既定で **FOR JSON** 句の JSON 出力を囲んでいる角かっこを削除するには、 **WITHOUT_ARRAY_WRAPPER** オプションを指定します。 単一要素の配列の代わりに、単一の JSON オブジェクトを出力として生成するには、このオプションと単一行の結果を使います。

このオプションと複数行の結果を使うと、複数の要素が生成されて角かっこがないため、結果の出力は有効な JSON ではなくなります。  
  
## <a name="example-single-row-result"></a>例 (単一行の結果)  
**WITHOUT_ARRAY_WRAPPER** オプションを指定した場合と指定しなかった場合の **FOR JSON** 句の出力例を以下に示します。  
  
 **クエリ**  
  
```sql  
SELECT 2015 as year, 12 as month, 15 as day  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER 
```  

 **WITHOUT_ARRAY_WRAPPER** オプションを使用した**結果**  
  
```json  
{
    "year": 2015,
    "month": 12,
    "day": 15
} 
```  
  
 **WITHOUT_ARRAY_WRAPPER** オプションを使わない**結果** (既定)  
  
```json  
[{
    "year": 2015,
    "month": 12,
    "day": 15
}]
```  

## <a name="example-multiple-row-result"></a>例 (複数行の結果)
次に、 **FOR JSON** オプションを指定した場合と指定しなかった場合の **WITHOUT_ARRAY_WRAPPER** オプションを指定します。 この例では、複数行の結果が生成されます。 複数の要素があり、角かっこがないため、出力は有効な JSON ではありません。
  
 **クエリ**  
  
```sql  
SELECT TOP 3 SalesOrderNumber, OrderDate, Status  
FROM Sales.SalesOrderHeader  
ORDER BY ModifiedDate  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER 
```  
  
 **WITHOUT_ARRAY_WRAPPER** オプションを使用した**結果**  
  
```json  
{
    "SalesOrderNumber": "SO43662",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43661",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43660",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
} 
```  
  
 **WITHOUT_ARRAY_WRAPPER** オプションを使わない**結果** (既定)  
  
```json  
[{
    "SalesOrderNumber": "SO43662",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43661",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43660",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}]
```  

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>SQL Server と Azure SQL Database の JSON の詳細情報  
  
### <a name="microsoft-blog-posts"></a>マイクロソフトのブログ記事  
  
具体的なソリューション、ユース ケース、推奨事項については、SQL Server および Azure SQL Database に組み込まれている JSON のサポートに関する[ブログ投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)を参照してください。  

### <a name="microsoft-videos"></a>Microsoft ビデオ

SQL Server と Azure SQL Database に組み込まれている JSON のサポートの視覚的な紹介は、次のビデオをご覧ください。

-   [SQL Server 2016 と JSON のサポート](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

-   [SQL Server 2016 と Azure SQL Database での JSON の使用](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database)

-   [NoSQL とリレーショナル環境間の架け橋としての JSON](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)
  
## <a name="see-also"></a>参照  
 [FOR 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  
