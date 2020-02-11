---
title: 相関名 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- correlation names [ODBC]
- SQL grammar [ODBC], correlation names
ms.assetid: 76c36c6f-f8e1-4ece-a77b-611dde3bdd8a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 535c169123923cdb36c355e098f6e0c55ebb9d56
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68127309"
---
# <a name="correlation-names"></a>相関名
相関名は、テーブルの一覧の中など、完全にサポートされています。 たとえば、次の文字列では、E1 は Emp という名前のテーブルの相関名です。  
  
```  
SELECT * FROM Emp E1   
WHERE E1.LastName = 'Smith'  
```
