---
title: SQLFreeStmt マッピング |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- SQLFreeStmt function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeStmt
ms.assetid: 267d95f2-4f0c-47ab-9411-5afe105215a2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 72f3924b668750030329e118e7201cbc0ea835d8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlfreestmt-mapping"></a>SQLFreeStmt マッピング
アプリケーションを呼び出すと**SQLFreeStmt**で、*オプション*SQL_DROP から ODBC 3 の引数*.x*ドライバーへの呼び出し  
  
```  
SQLFreeStmt(hstmt, SQL_DROP)   
```  
  
 をマップされます。  
  
```  
SQLFreeHandle(SQL_HANDLE_STMT,Handle)  
```  
  
 *処理*引数の値に設定されて*hstmt*です。
