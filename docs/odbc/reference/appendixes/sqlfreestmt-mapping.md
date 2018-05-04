---
title: SQLFreeStmt マッピング |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeStmt function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeStmt
ms.assetid: 267d95f2-4f0c-47ab-9411-5afe105215a2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb7ad5a362b7b193f1e6e6f8fae7cfb493131cc5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlfreestmt-mapping"></a>SQLFreeStmt マッピング
アプリケーションを呼び出すと**SQLFreeStmt**で、*オプション*SQL_DROP から ODBC 3 の引数 *.x*ドライバーへの呼び出し  
  
```  
SQLFreeStmt(hstmt, SQL_DROP)   
```  
  
 をマップされます。  
  
```  
SQLFreeHandle(SQL_HANDLE_STMT,Handle)  
```  
  
 *処理*引数の値に設定されて*hstmt*です。
