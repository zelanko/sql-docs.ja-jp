---
title: "名前付きパイプ プロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
caps.latest.revision: "32"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 72fecdede46024eae399d9a762b0f8cdf7bb3a6b
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="named-pipes-properties"></a>[名前付きパイプのプロパティ] ダイアログ ボックス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]使用して、**プロトコル**ページで、**名前付きパイプのプロパティ** ダイアログ ボックスを表示または変更、名前付きパイプです[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がリッスンする、名前付きパイプ プロトコルを使用する場合。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]有効にするにまたは、プロトコルを無効にしたり、名前付きパイプの変更を再起動する必要があります。  
  
## <a name="options"></a>オプション  
 **有効**  
 可能な値は **Yes** と **No**です。  
  
 **[パイプ名]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリッスンする名前付きパイプを指定します。 既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が既定のインスタンスの場合は `\\.\pipe\sql\query` と、名前付きインスタンスの場合は `\\.\pipe\MSSQL$<instancename>\sql\query` でリッスンします。 このフィールドには最大 2,047 文字まで入力できます。  
  
## <a name="creating-an-alternate-named-pipe"></a>代替名前付きパイプの作成  
 名前付きパイプを変更するには、新しいパイプ名を **[パイプ名]** ボックスに入力し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。 **sql\query** は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が使用する名前付きパイプとしてよく知られているため、パイプを変更することによって、悪意のあるプログラムによる攻撃の危険性を減らすことができます。  
  
### <a name="example"></a>例  
 **\\\\unit\app** パイプでリッスンするには、 **.\pipe\unit\app** と入力します。  
  
 **\\\\acct** パイプでリッスンするには、 **.\pipe\acct** と入力します。  
  
## <a name="see-also"></a>参照  
 [有効にするにまたは、サーバー ネットワーク プロトコルを無効にします。](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [ネットワーク プロトコルを選択します。](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [名前付きパイプを使用して有効な接続文字列を作成します。](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)  
  
  
