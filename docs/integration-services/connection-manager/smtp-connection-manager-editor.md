---
title: "SMTP 接続マネージャー エディター |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.smtpconnection.f1
helpviewer_keywords:
- SMTP Connection Manager Editor
ms.assetid: 2693de0d-b04d-4325-a856-ce667d2b8aa1
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3ef8edce1f187ac427463a0a0722c12666265d93
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="smtp-connection-manager-editor"></a>SMTP 接続マネージャー エディター
  **[SMTP 接続マネージャー エディター]** ダイアログ ボックスを使用すると、SMTP (Simple Mail Transfer Protocol) サーバーを指定できます。  
  
 SMTP 接続マネージャーの詳細については、「 [SMTP Connection Manager](../../integration-services/connection-manager/smtp-connection-manager.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **名前**  
 接続マネージャーの一意な名前を指定します。  
  
 **Description**  
 接続マネージャーの説明を記述します。 パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続マネージャーの目的について記述することをお勧めします。  
  
 **[SMTP サーバー]**  
 SMTP サーバーの名前を指定します。  
  
 **[Windows 認証を使用する]**  
 選択すると、Windows 認証を使用してサーバーへのアクセスを認証する SMTP サーバーで、メールが送信されます。  
  
> [!IMPORTANT]  
>  SMTP 接続マネージャーでは、匿名認証と Windows 認証のみがサポートされています。 基本認証はサポートされていません。  
  
> [!NOTE]  
>  SMTP サーバーとして Microsoft Exchange を使用する場合は、 **[Windows 認証を使用]** を **True**に設定する必要があります。 未認証の SMTP 接続を許可しないように Exchange サーバーを構成することもできます。  
  
 **[SSL (Secure Sockets Layer) を有効にする]**  
 選択すると、電子メール メッセージの送信時に SSL (Secure Sockets Layer) を使用して通信が暗号化されます。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)  
  
  
