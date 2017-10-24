---
title: "名前付きパイプ プロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a5e2f9b67c74a5eea97209bb812ee2e385c9c41a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="named-pipes-properties"></a>[名前付きパイプのプロパティ] ダイアログ ボックス
  **[名前付きパイプのプロパティ]**ダイアログ ボックスの **[プロトコル]** ページでは、名前付きパイプ プロトコルを使用している場合に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリッスンする名前付きパイプの表示や変更を行います。  
  
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
  
  

