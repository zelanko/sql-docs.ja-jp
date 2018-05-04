---
title: SQLFreeEnv マッピング |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeEnv
ms.assetid: c0f76455-d072-4bae-bee7-452277dfa479
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0e17b07e842960908bf7ac306d09f1aa46ff157
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlfreeenv-mapping"></a>SQLFreeEnv マッピング
アプリケーションを呼び出すと**SQLFreeEnv**から ODBC 3 *.x*ドライバーへの呼び出し  
  
```  
SQLFreeEnv(henv)   
```  
  
 をマップされます。  
  
```  
SQLFreeHandle(SQL_HANDLE_ENV,Handle)  
```  
  
 *処理*引数の値に設定されて*henv*です。
