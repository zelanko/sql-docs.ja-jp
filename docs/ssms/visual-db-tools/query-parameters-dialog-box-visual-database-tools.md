---
title: "[クエリ パラメーター] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fbf5a6857226aee3b091aa63ac8fe7868c55c68d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/18/2017

---
# <a name="query-parameters-dialog-box-visual-database-tools"></a>[クエリ パラメーター] ダイアログ ボックス (Visual Database Tools)
このダイアログ ボックスを使用すると、クエリに定義されたパラメーターの値を入力できます。 このダイアログ ボックスは、エンド ユーザーが値を入力する必要があるパラメーターを含むクエリを実行するときに表示されます。  
  
## <a name="options"></a>オプション  
**名前**  
実行するクエリに対して定義されているパラメーターを一覧表示します。 クエリに名前付きのパラメーターが含まれる場合は、名前が表示されます。 クエリに名前のないパラメーターが含まれる場合、クエリ内のパラメーターごとに、システム定義のパラメーター名が一覧表示されます。  
  
**値**  
**[名前]**に一覧表示された各パラメーターの値を入力します。 最後に使用した値が既定の値として表示されます。  
  
## <a name="example"></a>例  
SQL ペインに入力された次のクエリが [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject_md.md)] データベースで実行されると、[クエリ パラメーター] ダイアログ ボックスが開きます。  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a>参照  
[パラメーターを使用したクエリ (Visual Database Tools)](../../ssms/visual-db-tools/query-with-parameters-visual-database-tools.md)  
  

