---
title: SQLFreeEnv のマッピング |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeEnv
ms.assetid: c0f76455-d072-4bae-bee7-452277dfa479
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6070d7a9d9a7d2eafa35b87c94d6cfd320f916ae
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793572"
---
# <a name="sqlfreeenv-mapping"></a>SQLFreeEnv のマッピング
アプリケーションを呼び出すと**SQLFreeEnv** ODBC を通じて*3.x*ドライバーへの呼び出し  
  
```  
SQLFreeEnv(henv)   
```  
  
 をマップされます。  
  
```  
SQLFreeHandle(SQL_HANDLE_ENV,Handle)  
```  
  
 *処理*引数の値に設定*henv*します。
