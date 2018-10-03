---
title: インストール後の手順を完了 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fc79b6d3b1eff69a87a878f1dde5c5f88ef48de8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48065902"
---
# <a name="complete-the-post-installation-steps"></a>インストール後の手順の実行
  分散再生をインストールした後、分散再生コントローラー サービスおよび分散再生クライアント サービスのアカウントを変更する必要があります。  
  
### <a name="to-complete-the-post-installation-steps"></a>インストール後の手順を実行するには  
  
1.  **ファイアウォール ルールを作成する**: コントローラー コンピューターとクライアント コンピューターで、対応するサービスのファイアウォール経由の受信トラフィックを許可する必要があります。 インストール フォルダーに配置されているサービス実行可能ファイルのファイアウォール ルールを指定します。  
  
    1.  コントローラー サービスの場合は、インストール フォルダーにある **DReplayController.exe**のルールを作成します。 たとえば、次のコマンドを実行すると、このルールが有効になります ( `%InstallPath%` はサービスのインストール フォルダーです)。  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  クライアント サービスの場合は、クライアント コンピューターごとに、インストール フォルダーにある **DReplayClient.exe**のルールを作成します。 たとえば、次のコマンドを実行すると、このルールが有効になります ( `%InstallPath%` はサービスのインストール フォルダーです)。  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  **対象サーバーで各クライアントの権限を与える**: クライアント コンピューターへのクライアント サービスのインストールが完了したら、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の対象インスタンスの sysadmin ロールにクライアント サービス アカウントを手動で追加する必要があります。  
  
## <a name="net-framework-security"></a>.NET Framework のセキュリティ  
 分散再生の機能をインストールするには、管理権限が必要です。 sysadmin 権限を持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのみが、テスト サーバーの sysadmin サーバー ロールにクライアント サービス アカウントを追加できます。 Distributed Replay のセキュリティ上の考慮事項の詳細については、「 [Distributed Replay のセキュリティ](distributed-replay-security.md)」を参照してください。  
  
  
