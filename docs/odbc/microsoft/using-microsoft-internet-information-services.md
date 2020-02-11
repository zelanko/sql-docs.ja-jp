---
title: Microsoft インターネットインフォメーションサービス | を使用するMicrosoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], IIS
- internet information services [ODBC]
- IIS [ODBC]
ms.assetid: 3328f2f1-b34a-472f-82cf-ad49768ff061
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9e531149af21facd80e9e6ddab19a76c3bdc0fa6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088141"
---
# <a name="using-microsoft-internet-information-services"></a>Microsoft インターネット インフォメーション サービスの使用
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用してください。  
  
 IIS スクリプト内からの接続が困難な場合 (特に、ORA-12641 エラーが発生した場合)、次の行を Sqlnet. ORA ファイルに追加します。  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 これにより、セキュリティで保護された Network Services が無効になり、匿名認証を使用して接続できるようになります。
