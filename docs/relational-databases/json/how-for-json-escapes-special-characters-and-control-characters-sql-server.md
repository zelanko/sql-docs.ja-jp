---
title: "FOR JSON での特殊文字のエスケープと制御文字 (SQL Server) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON, special characters
ms.assetid: 4ba90025-5a09-4f0a-836a-54c886324530
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 21d0e35636e7c34c395f8c2bfe4f5c7ea07a4d9b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/31/2017

---
# <a name="how-for-json-escapes-special-characters-and-control-characters-sql-server"></a>FOR JSON での特殊文字のエスケープと制御文字 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  このトピックでは、SQL Server **SELECT** ステートメントの **FOR JSON** 句が JSON 出力で特殊文字をどのようにエスケープするか、また制御文字をどのように表すかについて説明します。  

> [!IMPORTANT]
> このページでは、Microsoft SQL Server の JSON の組み込みサポートについて説明します。 JSON のエスケープとエンコードの全般情報については、JSON RFC - [http://www.ietf.org/rfc/rfc4627.txt](http://www.ietf.org/rfc/rfc4627.txt) のセクション 2.5 をご覧ください。

## <a name="escaping-of-special-characters"></a>特殊文字のエスケープ  
ソース データに特殊文字が含まれる場合、**FOR JSON** 句は JSON 出力の特殊文字を `\` でエスケープします。次の表をご覧ください。 このエスケープは、プロパティの名前と値の両方で行われます。  
  
|**特殊文字**|**エスケープされた出力**|  
|---------------------------|--------------------------|  
|引用符 (")|\\"|  
|円記号 (\\)|\\\|  
|スラッシュ (/)|\\/|  
|バックスペース|\b|  
|改ページ|\f|  
|改行|\n|  
|キャリッジ リターン|\r|  
|水平タブ|\t|  
  
## <a name="control-characters"></a>制御文字。  
ソース データに制御文字が含まれる場合、**FOR JSON** 句は JSON 出力の制御文字を `\u<code>` 形式でエンコードします。次の表をご覧ください。  
  
|**制御文字**|**エンコードされた出力**|  
|---------------------------|--------------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|…|…|  
|CHAR(31)|\u001f|  
  
## <a name="example"></a>例  
 次は、特殊文字と制御文字の両方を含むソース データの **FOR JSON** 出力の例です。  
  
 クエリ:  
  
```sql  
SELECT  
  'VALUE\    /  
  "' as [KEY\/"],  
  CHAR(0) as '0',  
  CHAR(1) as '1',  
  CHAR(31) as '31'  
FOR JSON PATH  
```  
  
 結果:  
  
```json  
{
    "KEY\\\t\/\"": "VALUE\\\t\/\r\n\"",
    "0": "\u0000",
    "1": "\u0001",
    "31": "\u001f"
}
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>SQL Server に組み込まれている JSON サポートの詳細情報  
多くの具体的なソリューション、ユース ケース、推奨事項については、Microsoft のプログラム マネージャー Jovan Popovic による SQL Server および Azure SQL Database に[組み込まれている JSON のサポートに関するブログ投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)をご覧ください。
  
## <a name="see-also"></a>参照  
 [FOR JSON を使用してクエリ結果を JSON として書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
[FOR 句](../../t-sql/queries/select-for-clause-transact-sql.md)

