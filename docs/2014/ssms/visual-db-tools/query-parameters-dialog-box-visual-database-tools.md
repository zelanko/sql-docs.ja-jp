---
title: '[クエリ パラメーター] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 745d3b42b51ed9c86681f584fcf3c62a61c0f7d0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064920"
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a>[クエリ パラメーター] ダイアログ ボックス (Visual Database Tools)
  このダイアログ ボックスを使用すると、クエリに定義されたパラメーターの値を入力できます。 このダイアログ ボックスは、エンド ユーザーが値を入力する必要があるパラメーターを含むクエリを実行するときに表示されます。  
  
## <a name="options"></a>オプション  
 **Name**  
 実行するクエリに対して定義されているパラメーターを一覧表示します。 クエリに名前付きのパラメーターが含まれる場合は、名前が表示されます。 クエリに名前のないパラメーターが含まれる場合、クエリ内のパラメーターごとに、システム定義のパラメーター名が一覧表示されます。  
  
 **Value**  
 **[名前]** に一覧表示された各パラメーターの値を入力します。 最後に使用した値が既定の値として表示されます。  
  
## <a name="example"></a>例  
 SQL ペインに入力された次のクエリが [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースで実行されると、[クエリ パラメーター] ダイアログ ボックスが開きます。  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a>参照  
 [パラメーターを使用したクエリ (Visual Database Tools)](visual-database-tools.md)  
  
  
