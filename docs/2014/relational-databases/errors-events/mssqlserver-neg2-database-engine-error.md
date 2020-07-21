---
title: MSSQLSERVER_-2 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- -2 (Database Engine error)
ms.assetid: f37a7b7d-26e1-4b9e-bcb4-57f7805393d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1ccfdf4f2409fa4a91e5b287b45c25918e41d1aa
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552997"
---
# <a name="mssqlserver_-2"></a>MSSQLSERVER_-2
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|-2|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名||  
|メッセージ テキスト|タイムアウトに達しました。  処理が完了する前にタイムアウト期間が経過したか、サーバーが応答していません。 (Microsoft SQL Server、エラー: -2)。|   
  
## <a name="explanation"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントがサーバーに接続できません。 このエラーは、サーバー上のファイアウォールで接続が拒否されたために発生する場合があります。 
  
## <a name="user-action"></a>ユーザーの操作  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサーバー インスタンスで、接続を許可するようにファイアウォールを構成していることを確認します。  
  
## <a name="see-also"></a>参照  
 [SQL Server アクセスを許可するように Windows ファイアウォールを構成する](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)   
 [データベースエンジンアクセスできるように Windows ファイアウォールを構成する](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md)   
 [ネットワークプロトコルとネットワークライブラリ](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [クライアント ネットワーク構成](../../database-engine/configure-windows/client-network-configuration.md)   
 [クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md)   
 [サーバー ネットワーク プロトコルの有効化または無効化](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
