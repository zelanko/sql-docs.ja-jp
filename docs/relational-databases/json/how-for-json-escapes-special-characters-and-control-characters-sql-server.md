---
title: "FOR JSON での特殊文字のエスケープと制御文字 (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FOR JSON, 特殊文字"
ms.assetid: 4ba90025-5a09-4f0a-836a-54c886324530
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# FOR JSON での特殊文字のエスケープと制御文字 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  このトピックでは、 **FOR JSON** 句が JSON 出力で特殊文字をどのようにエスケープするか、また制御文字をどのように表すかについて説明します。  
  
## 特殊文字のエスケープ  
 次の表に示すように、**FOR JSON** 句は `\` を使用して JSON 出力の特殊文字をエスケープします。 このエスケープは、プロパティの名前と値の両方で行われます。  
  
|**特殊文字**|**エンコードされたシーケンス**|  
|---------------------------|--------------------------|  
|引用符 (")|\\"|  
|円記号 (\\)|\\\|  
|スラッシュ (/)|\\/|  
|バックスペース|\b|  
|改ページ|\f|  
|改行|\n|  
|キャリッジ リターン|\r|  
|水平タブ|\t|  
  
## 制御文字。  
 次の表に示すように、**FOR JSON** 句は JSON 出力の制御文字を `\u<code>` の形式で表します。  
  
|**制御文字**|**エンコードされたシーケンス**|  
|---------------------------|--------------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|…|…|  
|CHAR(31)|\u001f|  
  
## 例  
 エスケープと制御文字の両方を含む **FOR JSON** 句の例を示します。  
  
 クエリ:  
  
```tsql  
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
   "KEY\\\t\/\"":"VALUE\\\t\/\r\n\"",  
   "0":"\u0000",  
   "1":"\u0001",  
  "31":"\u001f“  
}  
```  
  
## 参照  
 [FOR JSON を使用してクエリ結果を JSON として書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  