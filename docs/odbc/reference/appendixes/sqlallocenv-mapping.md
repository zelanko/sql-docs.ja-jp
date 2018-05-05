---
title: SQLAllocEnv マッピング |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ca05f911091bd3c18641371281f3ac4b1372063
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlallocenv-mapping"></a>SQLAllocEnv マッピング
アプリケーションを呼び出すと**SQLAllocEnv**から ODBC 3 *.x*ドライバーへの呼び出し**SQLAllocEnv**(*phenv*)にマップされて**SQLAllocHandle**次のようにします。  
  
1.  ドライバー マネージャーは、環境ハンドルを割り当てるし、アプリケーションに返します。 ドライバー マネージャー呼び出し**SQLSetEnvAttr** SQL_OV_ODBC2 にまた環境属性を設定します。  
  
2.  アプリケーションでは、ドライバーには、最初の接続を確立するときに、ドライバー マネージャーを呼び出す  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     使用してドライバーで*OutputHandlePtr* 'éý' *phenv*です。
