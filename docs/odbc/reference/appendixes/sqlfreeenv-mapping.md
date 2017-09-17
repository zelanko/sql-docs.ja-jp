---
title: "SQLFreeEnv マッピング |Microsoft ドキュメント"
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
- SQLFreeEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeEnv
ms.assetid: c0f76455-d072-4bae-bee7-452277dfa479
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a5c1dae2fb67d530e9e8bfefd041eb978eb5bf15
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlfreeenv-mapping"></a>SQLFreeEnv マッピング
アプリケーションを呼び出すと**SQLFreeEnv**から ODBC 3*.x*ドライバーへの呼び出し  
  
```  
SQLFreeEnv(henv)   
```  
  
 をマップされます。  
  
```  
SQLFreeHandle(SQL_HANDLE_ENV,Handle)  
```  
  
 *処理*引数の値に設定されて*henv*です。
