---
title: "相関名 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- correlation names [ODBC]
- SQL grammar [ODBC], correlation names
ms.assetid: 76c36c6f-f8e1-4ece-a77b-611dde3bdd8a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7f757a0609490c280e2d6acb3679059e7f56dace
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="correlation-names"></a>相関名
相関名は完全にサポートされて、テーブルの一覧内を含むです。 たとえば、次の文字列では、E1 では、Emp という名前のテーブルの相関名には。  
  
```  
SELECT * FROM Emp E1   
WHERE E1.LastName = 'Smith'  
```
