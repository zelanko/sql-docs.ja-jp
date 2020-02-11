---
title: SQLAllocStmt Mapping |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLAllocStmt
- SQLAllocStmt function [ODBC], mapping
ms.assetid: a2449dbb-1b6c-4b49-81b9-ebdddd4442fd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cf79d3ef813e87e785cea588cfc1d6e3eed44ee4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064990"
---
# <a name="sqlallocstmt-mapping"></a>SQLAllocStmt のマッピング
アプリケーション*が ODBC 3.x*ドライバーを介して**sqlallocstmt**を呼び出すと、次のような呼び出しが行われます。  
  
```  
SQLAllocStmt(hdbc, phstmt)  
```  
  
 は、ドライバーのドライバーマネージャーによって次のように**SQLAllocHandle**にマップされます。  
  
```  
SQLAllocHandle(SQL_HANDLE_STMT, InputHandle, OutputHandlePtr)  
```  
  
 *InputHandle*を*hdbc*に設定し、 *OutputHandlePtr*を*phstmt*に設定します。
