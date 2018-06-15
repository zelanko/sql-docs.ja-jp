---
title: SQLAllocConnect マッピング |Microsoft ドキュメント
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
- SQLAllocConnect function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocConnect
ms.assetid: ac89dd1f-c565-47cc-8fa3-6fa5f80b5d63
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e1f2485112213bb3b4168bc72f96cee353cd1101
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908087"
---
# <a name="sqlallocconnect-mapping"></a>SQLAllocConnect マッピング
アプリケーションを呼び出すと**SQLAllocConnect**から ODBC 3 *。x*ドライバーへの呼び出し**SQLAllocConnect**(*henv*、 *phdbc*) にマップされて**SQLAllocHandle**次のようにします。  
  
1.  ドライバー マネージャーは、接続を割り当てるし、アプリケーションに返します。  
  
2.  アプリケーションでは、接続を確立するときに、ドライバー マネージャーを呼び出す  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     使用してドライバーで*InputHandle*に設定*henv*、および*OutputHandlePtr* 'éý' *phdbc*です。
