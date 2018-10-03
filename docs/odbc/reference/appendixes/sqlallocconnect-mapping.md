---
title: SQLAllocConnect のマッピング |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocConnect function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocConnect
ms.assetid: ac89dd1f-c565-47cc-8fa3-6fa5f80b5d63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bdb63e9610d00c0736f640b6f4c4d743f3335c7d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47606240"
---
# <a name="sqlallocconnect-mapping"></a>SQLAllocConnect のマッピング
アプリケーションを呼び出すと**SQLAllocConnect**を通じて、ODBC 3 *。x*ドライバーでは、呼び出し**SQLAllocConnect**(*henv*、 *phdbc*) にマップされて**SQLAllocHandle**次のようにします。  
  
1.  ドライバー マネージャーは、接続を割り当てるし、アプリケーションに返します。  
  
2.  ドライバー マネージャーは、アプリケーションでは、接続を確立するときに  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     ドライバーで*InputHandle*に設定*henv*、および*OutputHandlePtr*に設定*phdbc*します。
