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
- SQLAllocConnect function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocConnect
ms.assetid: ac89dd1f-c565-47cc-8fa3-6fa5f80b5d63
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 25e72cd3830cea8504983f4348f6c200261490f4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305523"
---
# <a name="sqlallocconnect-mapping"></a>SQLAllocConnect のマッピング
アプリケーションが ODBC 3 を介して**SQLAllocConnect**を呼び出すとき。*x*ドライバー **、SQLAllocConnect**(*henv*, *phdbc*) への呼び出しは、次のように**SQLAllocHandle**にマップされます。  
  
1.  ドライバー マネージャーは、接続を割り当て、アプリケーションに返します。  
  
2.  アプリケーションが接続を確立すると、ドライバー マネージャーは  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     *InputHandle*が*henv*に設定され *、OutputHandlePtr*が*phdbc*に設定されているドライバーで。
