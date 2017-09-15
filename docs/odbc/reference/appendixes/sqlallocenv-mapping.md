---
title: "SQLAllocEnv マッピング |Microsoft ドキュメント"
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
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 66261c8fd8236a4abc35ac70e29f63b49f646daf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlallocenv-mapping"></a>SQLAllocEnv マッピング
アプリケーションを呼び出すと**SQLAllocEnv**から ODBC 3*.x*ドライバーへの呼び出し**SQLAllocEnv**(*phenv*)にマップされて**SQLAllocHandle**次のようにします。  
  
1.  ドライバー マネージャーは、環境ハンドルを割り当てるし、アプリケーションに返します。 ドライバー マネージャー呼び出し**SQLSetEnvAttr** SQL_OV_ODBC2 にまた環境属性を設定します。  
  
2.  アプリケーションでは、ドライバーには、最初の接続を確立するときに、ドライバー マネージャーを呼び出す  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     使用してドライバーで*OutputHandlePtr* 'éý' *phenv*です。
