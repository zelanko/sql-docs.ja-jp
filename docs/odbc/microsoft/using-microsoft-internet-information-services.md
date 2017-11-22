---
title: "Microsoft インターネット インフォメーション サービスを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], IIS
- internet information services [ODBC]
- IIS [ODBC]
ms.assetid: 3328f2f1-b34a-472f-82cf-ad49768ff061
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8d3fafae5326b9631965ffdf7714b4de781cc5fa
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="using-microsoft-internet-information-services"></a>Microsoft インターネット インフォメーション サービスを使用します。
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 ある場合 (特にか 12641 エラーが発生する) 場合は、IIS スクリプト内からの接続に問題は、Sqlnet.ora ファイルに次の行を追加します。  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 匿名認証を使用して接続するために、これが、セキュリティで保護されたネットワーク サービスを無効になります。
