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
- SQLFreeEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeEnv
ms.assetid: c0f76455-d072-4bae-bee7-452277dfa479
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1f56bfeaee32e83ded6d8269873c9c4c33ed434e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302033"
---
# <a name="sqlfreeenv-mapping"></a>SQLFreeEnv のマッピング
アプリケーションが ODBC *3.x*ドライバーを使用して**SQLFreeEnv**を呼び出すと、次の  
  
```  
SQLFreeEnv(henv)   
```  
  
 にマップされています  
  
```  
SQLFreeHandle(SQL_HANDLE_ENV,Handle)  
```  
  
 引数*Handle*が*henv*の値に設定されている。
