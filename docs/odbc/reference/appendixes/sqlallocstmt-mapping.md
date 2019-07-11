---
title: SQLAllocStmt のマッピング |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 1139d87d9f97a3d63236c03e7cf4ced787ad8e85
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793546"
---
# <a name="sqlallocstmt-mapping"></a>SQLAllocStmt のマッピング
アプリケーションを呼び出すと**SQLAllocStmt** ODBC を通じて*3.x*ドライバーへの呼び出し。  
  
```  
SQLAllocStmt(hdbc, phstmt)  
```  
  
 マップされて**SQLAllocHandle**ドライバー マネージャーによってドライバーとして次のとおりです。  
  
```  
SQLAllocHandle(SQL_HANDLE_STMT, InputHandle, OutputHandlePtr)  
```  
  
 *InputHandle*に設定*hdbc*と*OutputHandlePtr*設定*phstmt*します。
