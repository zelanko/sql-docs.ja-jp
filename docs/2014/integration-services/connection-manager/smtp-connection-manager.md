---
title: SMTP 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a00a8295904d8fdc5a1ad87c6ac60dbf70ce6fa9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084364"
---
# <a name="smtp-connection-manager"></a>SMTP 接続マネージャー
  SMTP 接続マネージャーを使用すると、パッケージから簡易メール転送プロトコル (SMTP) サーバーに接続できます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれるメール送信タスクでは、SMTP 接続マネージャーを使用します。  
  
 Microsoft Exchange を SMTP サーバーとして使用する場合に、Windows 認証を使用するには SMTP 接続マネージャーの構成を必要とする場合があります。 未認証の SMTP 接続を許可しないように Exchange サーバーを構成できます。  
  
## <a name="configuration-the-smtp-connection-manager"></a>SMTP 接続マネージャーの構成  
 SMTP 接続マネージャーをパッケージに追加するときに[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]接続マネージャーを実行時に SMTP 接続を解決する、接続マネージャーのプロパティを設定する接続マネージャーを追加作成、`Connections`コレクションに、パッケージです。 `ConnectionManagerType`接続マネージャーのプロパティに設定されて`SMTP`です。  
  
 SMTP 接続マネージャーは、次の方法で構成できます。  
  
-   接続文字列を指定します。  
  
-   SMTP サーバーの名前を指定します。  
  
-   使用する認証方法を指定します。  
  
    > [!IMPORTANT]  
    >  SMTP 接続マネージャーでは、匿名認証と Windows 認証のみがサポートされています。 基本認証はサポートされていません。  
  
-   電子メール メッセージを送信するときに、SSL (Secure Sockets Layer) を使用して通信を暗号化するかどうかを指定します。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [SMTP 接続マネージャー エディター](../smtp-connection-manager-editor.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成方法の詳細については、次を参照してください。<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>と[プログラムで接続を追加する](../building-packages-programmatically/adding-connections-programmatically.md)です。  
  
  