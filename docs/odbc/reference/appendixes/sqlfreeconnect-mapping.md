---
title: SQLFreeConnect のマッピング |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLFreeConnect
- SQLFreeConnect function [ODBC], mapping
ms.assetid: 8a844538-93c0-4709-bab6-35c45e771d80
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ef90025a129bc624377bfe7891f122a838180a51
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199623"
---
# <a name="sqlfreeconnect-mapping"></a>SQLFreeConnect のマッピング
アプリケーションを呼び出すと**SQLFreeConnect**を通じて、ODBC 3 *.x*ドライバーへの呼び出し  
  
```  
SQLFreeConnect(hdbc)   
```  
  
 をマップされます。  
  
```  
SQLFreeHandle(SQL_HANDLE_DBC,Handle)  
```  
  
 *処理*引数の値に設定*hdbc*します。
