---
title: "SQLAllocEnv マッピング |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1061472d46a49ca105fb970b19a2f2d950470a12
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlallocenv-mapping"></a>SQLAllocEnv マッピング
アプリケーションを呼び出すと**SQLAllocEnv**から ODBC 3*.x*ドライバーへの呼び出し**SQLAllocEnv**(*phenv*)にマップされて**SQLAllocHandle**次のようにします。  
  
1.  ドライバー マネージャーは、環境ハンドルを割り当てるし、アプリケーションに返します。 ドライバー マネージャー呼び出し**SQLSetEnvAttr** SQL_OV_ODBC2 にまた環境属性を設定します。  
  
2.  アプリケーションでは、ドライバーには、最初の接続を確立するときに、ドライバー マネージャーを呼び出す  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     使用してドライバーで*OutputHandlePtr* 'éý' *phenv*です。
