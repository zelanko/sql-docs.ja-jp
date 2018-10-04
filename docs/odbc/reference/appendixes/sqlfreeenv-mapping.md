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
ms.openlocfilehash: 5c1ab12a975d7b9c0aba77db9af31accac398a16
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47618990"
---
# <a name="sqlfreeenv-mapping"></a>SQLFreeEnv のマッピング
アプリケーションを呼び出すと**SQLFreeEnv**を通じて、ODBC 3 *.x*ドライバーへの呼び出し  
  
```  
SQLFreeEnv(henv)   
```  
  
 をマップされます。  
  
```  
SQLFreeHandle(SQL_HANDLE_ENV,Handle)  
```  
  
 *処理*引数の値に設定*henv*します。
