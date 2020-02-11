---
title: 文字列に関する制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7faab41bd52397ac0d352e04a9ec153571e93f1e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948760"
---
# <a name="string-limitations"></a>文字列の制限事項
SQL ステートメント文字列の最大長は65000文字です。  
  
 Microsoft Access ドライバーが使用されている場合は、SQL-92 文字列定数 (二重引用符ではなく、単一引用符で囲む) のみがサポートされます。  
  
 文字が逆引用符で囲まれているかどうかにかかわらず、パイプ文字 (&#124;) を文字列内で使用することはできません。  
  
 相互運用性を最大にするために、アプリケーションは、引用符で囲まれた文字列を渡すのではなく、パラメーターに文字列を渡す必要があります。
