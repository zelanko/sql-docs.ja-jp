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
ms.openlocfilehash: ad5f394eb30e70838bdc0a7b8ae6380c145a1952
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63298221"
---
# <a name="sqlparamoptions-mapping"></a>SQLParamOptions のマッピング
アプリケーションを呼び出すと**SQLParamOptions**を通じて、ODBC 3 *.x*ドライバーでは、呼び出し  
  
```  
SQLParamOptions(hstmt, crow, piRow);  
```  
  
 2 つの呼び出しにマップされる**SQLSetStmtAttr**次のようにします。  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMSET_SIZE, crow, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMS_PROCESSED_PTR, piRow, 0);  
```
