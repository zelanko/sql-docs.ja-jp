---
title: LIKE エスケープシーケンス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC escape sequences [ODBC], LIKE
- LIKE escape sequence [ODBC]
- escape sequences [ODBC], LIKE
ms.assetid: 798d75ea-be9d-4bef-b297-318bc327f1ca
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 629ceaf666ae732d0838a216272c308dcb5b5658
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041713"
---
# <a name="like-escape-sequence"></a>LIKE エスケープ シーケンス
ODBC では、LIKE 句にエスケープシーケンスを使用します。 このエスケープシーケンスの構文は次のとおりです。  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>解説  
 BNF 表記では、構文は次のようになります。  
  
 *ODBC のような-escape* :: =  
  
 *Odbc-esc-開始側*エスケープ '*エスケープ文字*' *odbc-esc-ターミネータ*  
  
 *エスケープ文字*:: =*文字*  
  
 *ODBC-esc-イニシエーター* :: = {  
  
 *ODBC-esc-ターミネータ*:: =}  
  
 ドライバーで LIKE エスケープシーケンスがサポートされているかどうかを判断するために、アプリケーションは SQL_LIKE_ESCAPE_CLAUSE 情報の種類を使用して**SQLGetInfo**を呼び出すことができます。
