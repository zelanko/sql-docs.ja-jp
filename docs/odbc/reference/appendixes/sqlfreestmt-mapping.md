---
title: SQLFreeStmt Mapping |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeStmt function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeStmt
ms.assetid: 267d95f2-4f0c-47ab-9411-5afe105215a2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a92af35d8a1b1e98a484c69d7d2e66bf5bef3196
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086079"
---
# <a name="sqlfreestmt-mapping"></a>SQLFreeStmt のマッピング
アプリケーションが ODBC *3. x*ドライバーを使用して SQL_DROP の*オプション*引数を使用して**SQLFreeStmt**を呼び出すと、が呼び出されます。  
  
```  
SQLFreeStmt(hstmt, SQL_DROP)   
```  
  
 がにマップされています  
  
```  
SQLFreeHandle(SQL_HANDLE_STMT,Handle)  
```  
  
 *ハンドル*引数が*hstmt*の値に設定されている。
