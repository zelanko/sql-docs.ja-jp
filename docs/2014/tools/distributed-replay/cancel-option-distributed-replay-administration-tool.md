---
title: cancel オプション (分散再生管理ツール) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: fea376de-307a-4b45-b7e2-37df88f3681a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f6d9aa28d4a6879f3077b137880aae54b9a0c434
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63149880"
---
# <a name="cancel-option-distributed-replay-administration-tool"></a>cancel オプション (Distributed Replay 管理ツール)
  分散再生管理ツール`DReplay.exe`は、分散再生コントローラーとの通信に使用できるコマンドラインツールです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] このトピックでは、 **cancel** コマンド ライン オプションとそれに対応する構文について説明します。  
  
 
  **cancel** オプションは、コントローラーで実行されている現在の操作をキャンセルします。  
  
 ![トピックリンクアイコン](../../database-engine/media/topic-link.gif "トピック リンク アイコン")管理ツールの構文で使用される構文表記規則の詳細については、「transact-sql[構文表記規則 &#40;transact-sql&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
dreplay cancel [-mcontroller] [-q]   
```  
  
#### <a name="parameters"></a>パラメーター  
 **-m** *コントローラー*  
 コントローラーのコンピューター名です。 "`localhost`" または "`.`" を使用してローカル コンピューターを参照できます。  
  
 
  **-m** パラメーターが指定されていない場合、ローカル コンピューターが使用されます。  
  
 **-q**  
 非表示モードです。 確認のプロンプトは表示されません。  
  
 
  **-q** パラメーターは省略可能です。  
  
## <a name="examples"></a>例  
 次の例では、非表示モードでキャンセル要求が送信されます。 値 `localhost` は、コントローラー サービスが管理ツールと同じコンピューターで実行されていることを示します。  
  
```  
dreplay cancel -m localhost -q  
```  
  
## <a name="permissions"></a>アクセス許可  
 対話ユーザー (ローカル ユーザーまたはドメイン ユーザー アカウント) として、管理ツールを実行する必要があります。 ローカル ユーザー アカウントを使用するには、管理ツールとコントローラーが同じコンピューター上で実行されている必要があります。  
  
 詳細については、「 [Distributed Replay Security](distributed-replay-security.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server Distributed Replay](sql-server-distributed-replay.md)  
  
  
