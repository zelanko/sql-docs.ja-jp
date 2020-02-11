---
title: SQLAllocEnv Mapping |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
author: MightyPen
ms.author: genemi
ms.openlocfilehash: afbd1404cb40408166ecfc59993db7b183ae5ed2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68065014"
---
# <a name="sqlallocenv-mapping"></a>SQLAllocEnv のマッピング
アプリケーションが ODBC *3. x*ドライバーを使用して**sqlallocenv**を呼び出すと **、sqlallocenv**(*phenv*) への呼び出しは次のように**SQLAllocHandle**にマップされます。  
  
1.  ドライバーマネージャーは、環境ハンドルを割り当ててアプリケーションに返します。 ドライバーマネージャーは**SQLSetEnvAttr**を呼び出して、SQL_ATTR_ODBC_VERSION 環境属性を SQL_OV_ODBC2 に設定します。  
  
2.  アプリケーションがドライバーへの最初の接続を確立すると、ドライバーマネージャーはを呼び出します。  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     *OutputHandlePtr*が*phenv*に設定されているドライバー。
