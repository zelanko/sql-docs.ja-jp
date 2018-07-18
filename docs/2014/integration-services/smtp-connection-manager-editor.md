---
title: SMTP 接続マネージャー エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.smtpconnection.f1
helpviewer_keywords:
- SMTP Connection Manager Editor
ms.assetid: 2693de0d-b04d-4325-a856-ce667d2b8aa1
caps.latest.revision: 37
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c67233452d294a6bc0f6f106a59678827ef17b3d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37235212"
---
# <a name="smtp-connection-manager-editor"></a>SMTP 接続マネージャー エディター
  **[SMTP 接続マネージャー エディター]** ダイアログ ボックスを使用すると、SMTP (Simple Mail Transfer Protocol) サーバーを指定できます。  
  
 SMTP 接続マネージャーの詳細については、「 [SMTP Connection Manager](connection-manager/smtp-connection-manager.md)」を参照してください。  
  
## <a name="options"></a>および  
 **名前**  
 接続マネージャーの一意な名前を指定します。  
  
 **[説明]**  
 接続マネージャーの説明を記述します。 パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続マネージャーの目的について記述することをお勧めします。  
  
 **[SMTP サーバー]**  
 SMTP サーバーの名前を指定します。  
  
 **[Windows 認証を使用する]**  
 選択すると、Windows 認証を使用してサーバーへのアクセスを認証する SMTP サーバーで、メールが送信されます。  
  
> [!IMPORTANT]  
>  SMTP 接続マネージャーでは、匿名認証と Windows 認証のみがサポートされています。 基本認証はサポートされていません。  
  
> [!NOTE]  
>  Microsoft Exchange を SMTP サーバーとして使用する場合は、設定する必要があります**Windows 認証を使用**に`True`します。 未認証の SMTP 接続を許可しないように Exchange サーバーを構成することもできます。  
  
 **[SSL (Secure Sockets Layer) を有効にする]**  
 選択すると、電子メール メッセージの送信時に SSL (Secure Sockets Layer) を使用して通信が暗号化されます。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーとメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
