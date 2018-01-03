---
title: "エスケープ シーケンスと同様に |Microsoft ドキュメント"
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
- ODBC escape sequences [ODBC], LIKE
- LIKE escape sequence [ODBC]
- escape sequences [ODBC], LIKE
ms.assetid: 798d75ea-be9d-4bef-b297-318bc327f1ca
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a481e7dc539abc9fa206b7c1dab61de09816cd97
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="like-escape-sequence"></a>などのエスケープ シーケンス
ODBC では、LIKE 句のエスケープ シーケンスを使用します。 このエスケープ シーケンスの構文は次のとおりです。  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>解説  
 BNF 表記で、構文のとおりです。  
  
 *ODBC like エスケープ*:: =  
  
 *ODBC esc イニシエーター*エスケープ '*エスケープ文字*' *esc 終端の ODBC*  
  
 *エスケープ文字*:: =*文字*  
  
 *ODBC esc イニシエーター* :: = {  
  
 *Esc 終端の ODBC* :: =}  
  
 ドライバーが LIKE エスケープをサポートしているかどうかはシーケンス、アプリケーションが呼び出すことができます**SQLGetInfo** SQL_LIKE_ESCAPE_CLAUSE 情報の種類とします。
