---
title: "SQLAllocConnect マッピング |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLAllocConnect function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocConnect
ms.assetid: ac89dd1f-c565-47cc-8fa3-6fa5f80b5d63
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0188c47d6abfd294dc1a9c20c04ea7d271443a18
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlallocconnect-mapping"></a>SQLAllocConnect マッピング
アプリケーションを呼び出すと**SQLAllocConnect**から ODBC 3* 。x*ドライバーへの呼び出し**SQLAllocConnect**(*henv*、 *phdbc*) にマップされて**SQLAllocHandle**次のようにします。  
  
1.  ドライバー マネージャーは、接続を割り当てるし、アプリケーションに返します。  
  
2.  アプリケーションでは、接続を確立するときに、ドライバー マネージャーを呼び出す  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     使用してドライバーで*InputHandle*に設定*henv*、および*OutputHandlePtr* 'éý' *phdbc*です。

