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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb26e3443fabda2d6490c071b1f2668895e66b8d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304043"
---
# <a name="sqlallocenv-mapping"></a>SQLAllocEnv のマッピング
アプリケーションが ODBC *3. x*ドライバーを使用して**sqlallocenv**を呼び出すと **、sqlallocenv**(*phenv*) への呼び出しは次のように**SQLAllocHandle**にマップされます。  
  
1.  ドライバーマネージャーは、環境ハンドルを割り当ててアプリケーションに返します。 ドライバーマネージャーは**SQLSetEnvAttr**を呼び出して、SQL_ATTR_ODBC_VERSION 環境属性を SQL_OV_ODBC2 に設定します。  
  
2.  アプリケーションがドライバーへの最初の接続を確立すると、ドライバーマネージャーはを呼び出します。  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     *OutputHandlePtr*が*phenv*に設定されているドライバー。
