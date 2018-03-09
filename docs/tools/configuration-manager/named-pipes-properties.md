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
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7a8a88c3d7f54d4bf31cb5256e52d8257297ae91
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="named-pipes-properties"></a>[名前付きパイプのプロパティ] ダイアログ ボックス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
**[名前付きパイプのプロパティ]** ダイアログ ボックスの **[プロトコル]**ページでは、名前付きパイプ プロトコルを使用している場合に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリッスンする名前付きパイプの表示や変更を行います。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動する必要があるのは、プロトコルを有効または無効にする場合、または名前付きパイプを変更する場合です。  
  
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
  
  
