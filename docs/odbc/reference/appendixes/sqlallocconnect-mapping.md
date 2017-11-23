---
title: "SQLAllocConnect マッピング |Microsoft ドキュメント"
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
- SQLAllocConnect function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocConnect
ms.assetid: ac89dd1f-c565-47cc-8fa3-6fa5f80b5d63
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7a699be0e0c93ea48646375c0f6d9c0ab55ba74a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlallocconnect-mapping"></a>SQLAllocConnect マッピング
アプリケーションを呼び出すと**SQLAllocConnect**から ODBC 3 *。x*ドライバーへの呼び出し**SQLAllocConnect**(*henv*、 *phdbc*) にマップされて**SQLAllocHandle**次のようにします。  
  
1.  ドライバー マネージャーは、接続を割り当てるし、アプリケーションに返します。  
  
2.  アプリケーションでは、接続を確立するときに、ドライバー マネージャーを呼び出す  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     使用してドライバーで*InputHandle*に設定*henv*、および*OutputHandlePtr* 'éý' *phdbc*です。
