---
title: SQLParamOptions のマッピング |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLParamOptions
- SQLParamOptions function [ODBC], mapping
ms.assetid: 57ed65f6-9620-4738-b331-19d2a2b5cae4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 821af40a9550cc6e5fc038bb8e9a24f9e4323441
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792823"
---
# <a name="sqlparamoptions-mapping"></a>SQLParamOptions のマッピング
アプリケーションを呼び出すと**SQLParamOptions** ODBC を通じて*3.x*ドライバーでは、呼び出し  
  
```  
SQLParamOptions(hstmt, crow, piRow);  
```  
  
 2 つの呼び出しにマップされる**SQLSetStmtAttr**次のようにします。  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMSET_SIZE, crow, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMS_PROCESSED_PTR, piRow, 0);  
```
