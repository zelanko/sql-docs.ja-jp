---
title: "相関名 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- correlation names [ODBC]
- SQL grammar [ODBC], correlation names
ms.assetid: 76c36c6f-f8e1-4ece-a77b-611dde3bdd8a
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f5dba38b9248e0b367805860d0c6ec520c885d66
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="correlation-names"></a>相関名
相関名は完全にサポートされて、テーブルの一覧内を含むです。 たとえば、次の文字列では、E1 では、Emp という名前のテーブルの相関名には。  
  
```  
SELECT * FROM Emp E1   
WHERE E1.LastName = 'Smith'  
```
