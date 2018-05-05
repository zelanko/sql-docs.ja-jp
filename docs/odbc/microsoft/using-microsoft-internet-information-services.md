---
title: Microsoft インターネット インフォメーション サービスを使用して |Microsoft ドキュメント
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
- ODBC driver for Oracle [ODBC], IIS
- internet information services [ODBC]
- IIS [ODBC]
ms.assetid: 3328f2f1-b34a-472f-82cf-ad49768ff061
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 09aa384d3b5cd3f67d6bf6b75615bbf9047dff35
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-microsoft-internet-information-services"></a>Microsoft インターネット インフォメーション サービスを使用します。
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 ある場合 (特にか 12641 エラーが発生する) 場合は、IIS スクリプト内からの接続に問題は、Sqlnet.ora ファイルに次の行を追加します。  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 匿名認証を使用して接続するために、これが、セキュリティで保護されたネットワーク サービスを無効になります。
