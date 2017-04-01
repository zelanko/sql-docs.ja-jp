---
title: "ワイルドカードを使用したテキスト検索 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.wildcards"
  - "vswildcardsbuilder"
helpviewer_keywords: 
  - "検索 [SQL Server Management Studio], ワイルドカード"
  - "クエリ エディター [SQL Server Management Studio], ワイルドカード検索"
  - "ワイルドカード オプション [SQL Server Management Studio]"
ms.assetid: 449600f8-cc87-4b3f-878a-59c158a88a40
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# ワイルドカードを使用したテキスト検索
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の **[検索と置換]** ダイアログ ボックスの **[検索する文字列]** フィールドでは、文字や数字の代わりに以下の式を使用できます。  
  
#### ワイルドカードを使用して検索を行うには  
  
1.  [クイック検索]、**[フォルダーを指定して検索]**、**[クイック置換]**、**[フォルダーを指定して置換]** の各操作に関して、**[検索する文字列]** フィールドでのワイルドカードの使用を有効にするには、**[検索オプション]** の下の **[条件]** をオンにして、**[ワイルドカード]** をオンにします。  
  
2.  **[検索する文字列]** フィールドの横にある三角形の**参照一覧**ボタンが使用可能になります。 このボタンをクリックすると、使用可能なワイルドカードの一覧が表示されます。 **参照一覧**から項目を選択すると、その項目が **[検索する文字列]** の文字列に挿入されます。  
  
 **参照一覧**から使用できるワイルドカードを以下にまとめます。  
  
|式|構文|説明|  
|----------------|------------|-----------------|  
|任意の 1 文字|?|任意の 1 文字に相当します。|  
|任意の 1 つの数字|#|任意の 1 つの数字に相当します。 一例として、7# は 7 とその後の 1 つの数字に相当します (たとえば、71 は一致項目ですが、17 は違います)。|  
|セット内以外の文字|[! ]|セット内に指定されていない任意の 1 文字に相当します。|  
|1 つ以上の文字|*|任意の 1 つ以上の文字に相当します。 一例として、new* は「new」を含む任意のテキスト (newfile.txt など) に相当します。|  
|文字のセット|[ ]|セット内に指定されている任意の 1 文字に相当します。|  
  
## 参照  
 [検索と置換](../../relational-databases/scripting/search-and-replace.md)   
 [正規表現によるテキストの検索](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
  
  