---
title: MSSQLSERVER_10060 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "10060"
helpviewer_keywords:
- 10060 (Database Engine error)
ms.assetid: 28c21277-cad8-406c-a955-07933a56982a
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5497c254a431718d4f958d441b3e7ee99854639d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432471"
---
# <a name="mssqlserver10060"></a>MSSQLSERVER_10060
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10060|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名||  
|メッセージ テキスト|サーバーへの接続を確立中にエラーが発生しました。  SQL Server に接続している場合、既定の設定では SQL Server によるリモート接続が許可されていないために、このエラーが発生した可能性があります。 (プロバイダー: TCP プロバイダー、エラー: 0 - 接続済みの呼び出し先が一定の時間を過ぎても正しく応答しなかったため、接続できませんでした。または接続済みのホストが応答しなかったため、確立された接続は失敗しました。) (Microsoft SQL Server、エラー: 10060)|  
  
## <a name="explanation"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントがサーバーに接続できません。 このエラーは、サーバーのファイアウォールで接続が拒否されたか、サーバーがリモート接続を許可するように構成されていないことが原因で発生することがあります。  
  
## <a name="user-action"></a>ユーザーの操作  
 このエラーを解決するには、以下のいずれかの操作を試してみます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のこのインスタンスで、接続を許可するようにファイアウォールを構成していることを確認します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャー ツールを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリモート接続を許可できるようにします。  
  
## <a name="see-also"></a>参照  
 [データベース エンジン アクセス用の Windows ファイアウォールを構成します。](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [クライアント プロトコルを構成します。](../../database-engine/configure-windows/configure-client-protocols.md)   
 [ネットワーク プロトコルとネットワーク ライブラリ](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [クライアント ネットワーク構成](../../database-engine/configure-windows/client-network-configuration.md)   
 [クライアント プロトコルを構成します。](../../database-engine/configure-windows/configure-client-protocols.md)   
 [サーバー ネットワーク プロトコルの有効化または無効化](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
