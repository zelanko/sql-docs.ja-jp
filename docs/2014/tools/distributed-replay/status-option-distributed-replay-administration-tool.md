---
title: status オプション (分散再生管理ツール) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ea89386e-1598-4412-8b37-680d14b2a5b6
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5e2b1e7310b00fdb53a70f401f776ae7b26a299c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238152"
---
# <a name="status-option-distributed-replay-administration-tool"></a>status オプション (Distributed Replay 管理ツール)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 管理ツール、 `DReplay.exe`、分散再生コント ローラーとの通信に使用できるコマンド ライン ツールです。 このトピックでは、 **status** コマンド ライン オプションとそれに対応する構文について説明します。  
  
 **status** オプションは、コントローラーに照会し、現在の状態を表示します。  
  
 ![トピック リンク アイコン](../../database-engine/media/topic-link.gif "トピック リンク アイコン") 管理ツールの構文で使用される構文表記規則の詳細については、「[Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
dreplay status [-mcontroller] [-fstatus_interval]  
```  
  
#### <a name="parameters"></a>パラメーター  
 **-m** *controller*  
 コントローラーのコンピューターの名前を指定します。 "`localhost`" または "`.`" を使用してローカル コンピューターを参照できます。  
  
 **-m** パラメーターが指定されていない場合、ローカル コンピューターが使用されます。  
  
 **-f** *status_interval*  
 状態を表示する頻度 (秒単位) を指定します。  
  
 **-f** パラメーターを指定しない場合は、既定の間隔は 30 秒です。  
  
## <a name="examples"></a>使用例  
 次の例では、現在の状態は 60 秒ごとに表示されます。 値 `localhost` は、コントローラー サービスが管理ツールと同じコンピューターで実行されていることを示します。  
  
```  
dreplay status –m localhost -f 60  
```  
  
## <a name="permissions"></a>アクセス許可  
 対話ユーザー (ローカル ユーザーまたはドメイン ユーザー アカウント) として、管理ツールを実行する必要があります。 ローカル ユーザー アカウントを使用するには、管理ツールとコントローラーが同じコンピューター上で実行されている必要があります。  
  
 詳細については、「 [Distributed Replay Security](distributed-replay-security.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server 分散再生](sql-server-distributed-replay.md)   
 [Transact-SQL デバッガー](../../relational-databases/scripting/transact-sql-debugger.md)  
  
  
