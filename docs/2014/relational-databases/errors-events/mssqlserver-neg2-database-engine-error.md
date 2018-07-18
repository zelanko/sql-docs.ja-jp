---
title: MSSQLSERVER_-2 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- -2 (Database Engine error)
ms.assetid: f37a7b7d-26e1-4b9e-bcb4-57f7805393d2
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 38c551b7d45d18a7c60ab3de15b62c27f80f521e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410901"
---
# <a name="mssqlserver-2"></a>MSSQLSERVER_-2
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|-2|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名||  
|メッセージ テキスト|タイムアウトが発生しました。  処理が完了する前にタイムアウト期間が経過したか、サーバーが応答していません。 (Microsoft SQL Server、エラー: -2)。|   
  
## <a name="explanation"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントがサーバーに接続できません。 このエラーは、サーバー上のファイアウォールで接続が拒否されたために発生する場合があります。 
  
## <a name="user-action"></a>ユーザーの操作  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサーバー インスタンスで、接続を許可するようにファイアウォールを構成していることを確認します。  
  
## <a name="see-also"></a>参照  
 [SQL Server のアクセスを許可するための Windows ファイアウォールを構成します。](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)   
 [データベース エンジン アクセス用の Windows ファイアウォールを構成します。](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [クライアント プロトコルを構成します。](../../database-engine/configure-windows/configure-client-protocols.md)   
 [ネットワーク プロトコルとネットワーク ライブラリ](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [クライアント ネットワーク構成](../../database-engine/configure-windows/client-network-configuration.md)   
 [クライアント プロトコルを構成します。](../../database-engine/configure-windows/configure-client-protocols.md)   
 [サーバー ネットワーク プロトコルの有効化または無効化](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
