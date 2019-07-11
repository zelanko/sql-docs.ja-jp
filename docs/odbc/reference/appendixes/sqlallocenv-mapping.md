---
title: SQLAllocEnv のマッピング |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 841310d1e51084ae6a61c629b8782a8b84c665f8
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793581"
---
# <a name="sqlallocenv-mapping"></a>SQLAllocEnv のマッピング
アプリケーションを呼び出すと**SQLAllocEnv** ODBC を通じて*3.x*ドライバーでは、呼び出し**SQLAllocEnv**(*phenv*)にマップされて**SQLAllocHandle**次のようにします。  
  
1.  ドライバー マネージャーは、環境ハンドルを割り当てるし、アプリケーションに返します。 ドライバー マネージャー呼び出し**SQLSetEnvAttr** SQL_OV_ODBC2 を SQL_ATTR_ODBC_VERSION 環境属性を設定します。  
  
2.  ドライバー マネージャーは、アプリケーションがドライバーには、最初の接続を確立する場合  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     ドライバーで*OutputHandlePtr*設定*phenv*します。
