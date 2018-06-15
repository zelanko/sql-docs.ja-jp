---
title: SQLFreeEnv マッピング |Microsoft ドキュメント
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
- SQLFreeEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeEnv
ms.assetid: c0f76455-d072-4bae-bee7-452277dfa479
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fe0941bc094efbb4c0d0f0ef348b7d17df760997
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32905997"
---
# <a name="sqlfreeenv-mapping"></a>SQLFreeEnv マッピング
アプリケーションを呼び出すと**SQLFreeEnv**から ODBC 3 *.x*ドライバーへの呼び出し  
  
```  
SQLFreeEnv(henv)   
```  
  
 をマップされます。  
  
```  
SQLFreeHandle(SQL_HANDLE_ENV,Handle)  
```  
  
 *処理*引数の値に設定されて*henv*です。
