---
title: LIKE エスケープ シーケンス |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 65447904f32b7e0457ed807f18e942b334ddc236
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188809"
---
# <a name="like-escape-sequence"></a>LIKE エスケープ シーケンス
ODBC では、LIKE 句のエスケープ シーケンスを使用します。 このエスケープ シーケンスの構文は次のとおりです。  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>Remarks  
 BNF 表記では、構文がとおりです。  
  
 *ODBC のエスケープ似た*:: =  
  
 *ODBC のイニシエーター esc*エスケープ '*エスケープ文字*' *esc 終端の ODBC*  
  
 *エスケープ文字*:: =*文字*  
  
 *ODBC のイニシエーター esc* :: = {  
  
 *Esc 終端の ODBC* :: =}  
  
 ドライバーが LIKE エスケープをサポートしているかを決定するシーケンス、アプリケーションが呼び出すことができます**SQLGetInfo** SQL_LIKE_ESCAPE_CLAUSE 情報の種類にします。
