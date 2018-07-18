---
title: MSSQLSERVER_233 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "233"
helpviewer_keywords:
- 233 (Database Engine error)
ms.assetid: 201665dc-7ac8-4c19-90d3-33354c5caa72
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e394ab73599bc785aa9b444bf866ddd8375c5d88
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432321"
---
# <a name="mssqlserver233"></a>MSSQLSERVER_233
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|233|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名||  
|メッセージ テキスト|サーバーとの接続は正常に確立されましたが、ログイン プロセスでエラーが発生しました。 (プロバイダー: 共有メモリ プロバイダー、エラー: 0 - パイプの他端にプロセスがありません。) (Microsoft SQL Server、エラー: 233)|  
  
## <a name="explanation"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントがサーバーに接続できません。 このエラーは、サーバーがリモート接続を許可するように構成されていないことが原因で発生することがあります。  
  
## <a name="user-action"></a>ユーザーの操作  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャー ツールを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリモート接続を許可できるようにします。  
  
## <a name="see-also"></a>参照  
 [ネットワーク プロトコルとネットワーク ライブラリ](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [クライアント ネットワーク構成](../../database-engine/configure-windows/client-network-configuration.md)   
 [クライアント プロトコルを構成します。](../../database-engine/configure-windows/configure-client-protocols.md)   
 [サーバー ネットワーク プロトコルの有効化または無効化](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
