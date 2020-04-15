---
title: マッピング |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304043"
---
# <a name="sqlallocenv-mapping"></a>SQLAllocEnv のマッピング
アプリケーションが ODBC *3.x*ドライバーを使用して**SQLAllocEnv**を呼び出すと、次のように**SQLAllocEnv**(*phenv*) への呼び出しが**SQLAllocHandle**にマップされます。  
  
1.  ドライバー マネージャーは、環境ハンドルを割り当て、アプリケーションに返します。 ドライバー マネージャーは、SQL_ATTR_ODBC_VERSION環境属性をSQL_OV_ODBC2に設定する**SQLSetEnvAttr**を呼び出します。  
  
2.  アプリケーションがドライバーへの最初の接続を確立すると、ドライバー マネージャーは、  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     *ドライバーで、出力ハンドルPtr*を*phenv*に設定します。
